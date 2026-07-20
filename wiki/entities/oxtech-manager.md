---
type: entity
created: 2026-07-20
updated: 2026-07-20
sources: [codebase:oxtech_manager@2ecb1d5, codebase:oxtech_portal@359f142, raw/2026-07-20_oxtech-multiagent-platform.pdf]
tags: [product, infrastructure]
---
# Oxtech Manager

Сервис управления жизненным циклом агентов [[oxtech-platform]]. Go 1.26, HTTP API на порту 8091,
аутентификация по заголовку `X-API-Key` с constant-time сравнением.

## Ответственности (по коду)

| Компонент | Периодичность | Что делает |
|---|---|---|
| Builder + Build Queue | по требованию | SSH на build-сервер, компиляция с build tags; 2 воркера (`BUILD_QUEUE_WORKERS`) |
| Deployer | по требованию | rsync бинарника, генерация `.env`, расчёт портов |
| DockerManager / SystemdManager | по требованию | запуск агентов; Docker — основной путь, systemd — fallback |
| Metrics Aggregator | 60 с | скрейп Prometheus-эндпоинтов агентов → Redis → Portal |
| Status Sync | 30 с | batch-статусы всех агентов в Portal |
| Monitor | 30 с | проверка живости агентов |
| Cleaner + GC | 30 мин | зомби-процессы, осиротевшие порты и юниты, артефакты сборки |
| MCP Service Manager | 30 с | markitdown и др. MCP-сервисы, автоперезапуск (до 5 попыток) |

API: ~35 endpoints — управление агентами (start/stop/restart/rebuild/logs/metrics), контейнерами,
MCP-сервисами, A2A discovery, приём OTLP-трейсов.

## Цепочка деплоя

```
git push → GitHub webhook → Portal /webhooks/github/agent_push
  → AgentSystemOperationJob(rebuild) → POST /api/v1/agents/:id/rebuild (Manager)
  → deploy-лок в Redis → сборка на build-сервере (git clone --depth 1 → go build -tags)
  → rsync на agents-хост → docker cp бинарника и .env → перезапуск процесса
  → iptables DNAT для A2A- и metrics-портов → верификация (статус + порт слушает)
  → только теперь остановка старой версии
```

Пересборка идёт по tier'ам (инфраструктура → базовые → коммуникации → специализированные →
координация), внутри tier'а — параллельно в тредах.

## Расхождения с презентацией

⚠️ Три утверждения слайда «Архитектура» требуют уточнённых формулировок (ниже — что честно
можно говорить).

| Заявлено | Что в коде |
|---|---|
| «деплой 15–25 с» | Цифра есть только в `docs/6_deployment/deployment.md:330`, в коде нет ни SLA, ни бенчмарка. Реальные бюджеты: до 10 мин на сборку, 30 с на верификацию запуска, Portal ждёт rebuild до 600 с. Замер длительности в коде есть, но его отчёт в Portal не доходит (см. ниже) |
| «blue-green» | Фактически «deploy → verify → cleanup»: новая версия занимает **тот же порт** (детерминированный, `agent_config_id % 45`), поэтому параллельного существования двух версий нет. `.backup` создаётся, но **кода отката из него не существует**. `CleanupOldAgentBinaries` — заглушка, только логирует |
| «автоперезапуск» | `MONITOR_AUTO_RESTART` = `false` и по умолчанию, и явно в `deploy.sh`. Monitor фиксирует падение и ставит статус `failed`, но **не перезапускает**. Восстановление де-факто держится на `--restart unless-stopped` уровня контейнера |

Что честно можно говорить: автоматизированный деплой одной кнопкой, безопасный редеплой с
отложенной очисткой старой версии, health-check каждые 30 с с фиксацией отказа.

## Известные дефекты

- **Отчёты о деплое не доходят в Portal**: `SetWebSocketClient` не вызывается в production-коде,
  поэтому `sendDeploymentReport` всегда выходит по `wsClient == nil`. Фактические тайминги
  деплоя в Portal не попадают.
- **Фоновая проверка build-сервера не запускается**: `StartBackgroundHealthChecks` не вызывается
  нигде; кэш обновляется лениво из `/health`.
- **Обратный webhook Manager → Portal мёртв**: пакет `internal/webhook` не импортируется,
  роуты в Portal остаются без вызывающей стороны.
- **GitHub webhook при пустом `GITHUB_WEBHOOK_SECRET` не проверяет подпись** (`return true if
  secret.blank?`) — endpoint становится открытым триггером пересборки.

## Изоляция агентов

Модель — **один контейнер на систему агентов**, не на агента. Агенты внутри — обычные процессы
(`docker exec -d`), делящие PID-namespace, файловую систему и сеть контейнера. Изоляция есть
между системами (`oxtech-agents-prod`, `oxtech-agents-test`, `keylink-agents-prod`), но не между
агентами внутри системы.

Порты **детерминированные**, не динамические: A2A = `basePort + (agent_config_id % 45) * 2`,
metrics = `9090 + agent_config_id`. Публикации портов через Docker нет — проброс делается
правилами iptables DNAT, чтобы не порождать `docker-proxy` на большие диапазоны.

⚠️ Ресурсных лимитов (CPU/память) у агентов нет — ни в `docker run`, ни в systemd-юните. Лимиты
заданы только для MCP-сервисов (512 МБ, 50% CPU). С учётом того, что хост agents.oxteam.me
располагает 1 CPU / 1 ГБ без swap, это реальный эксплуатационный риск.

Периметр закрыт UFW, управляющий трафик — по приватной сети; наружу nginx отдаёт только
`/gomodel/*`.

См. также [[observability]], [[oxtech-portal]].

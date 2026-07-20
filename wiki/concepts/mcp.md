---
type: concept
created: 2026-07-20
updated: 2026-07-20
sources: [raw/2026-07-20_oxtech-multiagent-platform.pdf, codebase:oxtech_portal@359f142, codebase:oxtech_agent@10ba1be]
tags: [protocol]
---
# MCP (Model Context Protocol)

Открытый протокол доступа агентов к инструментам и данным. Протокол Anthropic (ноябрь 2024).
«Вертикальный»: агент → инструменты/данные, клиент-сервер, вызовы функций по схеме.

В [[oxtech-platform]] — слой над реальными корпоративными системами. Ключевое отличие от
no-code конструкторов, где данные — файлы, загруженные в чат.

## Два MCP-интерфейса

| Интерфейс | URL | Инструментов | Кто использует |
|---|---|---|---|
| Portal MCP Server | `oxteam.me/mcp` | **67** | Go-агенты как MCP-клиенты |
| Keylink MCP | `oxteam.me/mcp/keylink` | **75** | контур [[keylink]] (отдельный сервер, свой Bearer) |
| MCP-A2A Converter | `oxteam.me/mcp_converter` | **5** | внешние ассистенты (Claude, Cursor, Perplexity) |

Суммарно по платформе — 147 инструментов. Заявленные в презентации «60+» относятся к Portal
MCP и подтверждаются кодом с запасом.

## Portal MCP: 67 инструментов по доменам

Собираются из 14 concern-модулей в `app/controllers/mcp_controller.rb:159` (Portal).

| Домен | Инструментов | Примеры |
|---|---|---|
| Пользователи и агенты | 9 | `get_users`, `auth_agent`, `find_users_by_skills` |
| Контент: проекты и услуги | 9 | `get_solutions`, `get_project_team`, `create_service` |
| Календарь | 8 | `create_calendar_event`, `find_free_slots`, `get_pending_invitations` |
| Электронная почта | 7 | `get_emails`, `send_email`, `reply_to_email`, `get_email_thread` |
| Хранилище S3 | 6 | `upload_document`, `get_document_url` (presigned), `list_documents` |
| Диалоги агентов | 5 | `get_agent_conversations`, `update_conversation_context` |
| Document Pipeline | 5 | `get_pipeline_state`, `save_pipeline_artifact`, `submit_review_result` |
| Факты и знания | 4 | `create_fact`, `get_facts_for_project` |
| Масштабирование агентов | 4 | `scale_agent_up`, `get_agent_instances` |
| Финансы (T-Bank) | 3 | `get_bank_accounts`, `get_transactions`, `get_financial_summary` |
| Задачи | 3 | `create_task`, `get_tasks`, `update_task` |
| Веб-чат (HITL) | 2 | `deliver_chat_message`, `deliver_orchestration_event` |
| Семантический поиск | 1 | `search_company_data` (векторный поиск, pgvector) |
| Документы (OxDocs) | 1 | `create_oxdocs_document` |

Схемы — JSON Schema draft-07. Ответ унифицирован: `{ content: [{ type: "text", text }] }`,
то есть всё возвращается текстом; `outputSchema` не используется.

## Аутентификация и разграничение прав

Bearer-токен, три источника (`app/controllers/concerns/bearer_authentication.rb:8`):
персональный `auth_token` пользователя, `auth_token` конфигурации агента, системный
`PORTAL_AUTH_TOKEN`. Неактивный пользователь — 401, формат ошибок JSON-RPC (`-32001`).

**Белый список инструментов на агента** — модель `AgentToolPermission`: таблица
`(agent_id, tool_name, enabled)`, проверка в двух местах — фильтрация `tools/list` и
enforcement при `tools/call`. Это подтверждает тезис презентации «агент не может вызвать
инструмент вне своего списка разрешений».

⚠️ Существенная оговорка: allowlist применяется **только к агентам**. Проверка начинается с
`return tools unless @current_user.agent?` — пользовательский и системный токены получают все
67 инструментов без ограничений. Keylink MCP механизмом `AgentToolPermission` не покрыт вовсе.

## Транспорт

- Portal `/mcp`: JSON-RPC 2.0 поверх POST. Реализованы три метода — `initialize`, `tools/list`,
  `tools/call`. `resources/*` и `prompts/*` не реализованы. Версия протокола `2024-11-05`
  захардкожена, согласования с клиентом нет.
- `GET /mcp/sse` — **не настоящий SSE**: отдаёт один кадр со списком инструментов и закрывает
  соединение.
- Converter: настоящие Streamable HTTP и SSE, но наружу через Portal-прокси SSE закрыт
  ответом 405 («POST-only mode»).

## Эксплуатация

- Rate limiting (Rack::Attack, Redis): 120 запросов/мин на `/mcp`, 60 на `/mcp_converter`,
  10/час на OAuth-регистрацию клиента. Лимиты **per-IP, не per-token**.
- Метрики вызовов: длительность и размер ответа, агрегация в `McpUsageStat`.
- Фильтры запросов логируются **только по ключам**, значения отбрасываются осознанно.

⚠️ Аудита вызовов в смысле security нет: `McpUsageStat` не хранит `user_id`/`agent_id`, поэтому
по логам нельзя ответить «кто вызвал `send_email`». Подробнее — [[observability]] и
[[claims-vs-code]].

См. также [[a2a]]; сравнение подходов — [[a2a-vs-mcp]]; аудит заявлений — [[claims-vs-code]].

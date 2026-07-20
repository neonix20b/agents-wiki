---
type: entity
created: 2026-07-20
updated: 2026-07-20
sources: [codebase:oxtech_portal@359f142, codebase:oxtech_agent@10ba1be]
tags: [agents, reference]
---
# Состав агентов

Фактический реестр агентов [[oxtech-platform]] по коду на 2026-07-20. Источник истины —
сиды Portal (`db/seeds/agent_templates.rb`, `db/seeds/agent_systems.rb`); централизованного
списка типов агентов в Go нет.

## Три разных числа

| Число | Что означает |
|---|---|
| **17** | шаблонов агентов в каталоге `AgentTemplate` |
| **13** | сконфигурировано в системе «Oxtech Production» |
| **11** | реально отвечают по A2A (проверено `agent_list` 2026-07-20) |
| 12 | цифра из презентации — в коде не встречается |

«12» сходится, если считать 11 работающих агентов плюс MCP-A2A Converter (инфраструктурный
компонент, сам себя в реестре агентов не показывает). Формулировка «12 агентов в production»
защитима, но при вопросе «покажите список» ответ будет из 11 позиций.

## Каталог: 17 шаблонов

| Агент | Роль | Capability | В Production |
|---|---|---|---|
| Orchestrator | координация многошаговых задач | `orchestration` | да (tier 4) |
| Memorizer | память и корпоративные знания | — | да (tier 1) |
| Communicator | каналы: Telegram, Email, Mattermost, Push | — | да (tier 2) |
| MCP-A2A Converter | конвертер протоколов, шлюз для внешних ассистентов | `converter` | да (tier 0) |
| ProjectManager | мониторинг задач, digest, дедлайны | `project_management` | да (tier 2) |
| Mailer | суммаризация писем, ответы, оценка спама | `email` | да (tier 2) |
| Writer | документы, diff-редактирование, PDF по ГОСТ, S3 | `document` | да (tier 3) |
| Reader | анализ документов, извлечение, суммаризация | `vision` | да (tier 3) |
| Financer | финансовые данные, транзакции, отчёты | `finance` | да (tier 3) |
| Analyst | анализ данных, графики, тренды | — | да (tier 3) |
| Scheduler | календарь, события, напоминания | `task_scheduling` | да (tier 3) |
| Reviewer | ревью документов: полнота, логика, факты | — | да (tier 3) |
| Internetor | поиск цен: DigiKey, Mouser, XMLStock, конвертация валют | `internet_search` | в конфиге есть, **не отвечает** |
| Procurement | анализ RFQ, поиск аналогов, расчёт КП | `procurement` | только Keylink |
| Speecher | голосовой ассистент STT → LLM → TTS | `speech` | **нет** |
| Lawyer | юридический анализ документов | — | **нет** |
| Engineer | разработка кода, инфраструктура, DevOps | — | **нет** |

Speecher, Lawyer и Engineer имеют шаблоны, но не входят ни в одну систему агентов. В презентации
и на графе они не показываются — и правильно.

⚠️ Дефект сборки: Lawyer и Engineer в Go компилируются под тегами `legal` и `technical`, а Portal
передаёт теги `lawyer` и `engineer`. При текущем деплой-пути эти агенты соберутся со **стабами**
вместо своих capability. Так как в production они не развёрнуты, эффекта пока нет.

## Инструменты по capability

| Capability | Инструменты агента |
|---|---|
| `memory_management` | 10 инструментов памяти: добавление сообщений, саммари, факты, поиск экспертов |
| `document` | `compile_latex`, `edit_latex`, `apply_diff`, `find_document_template`, `generate_document`, работа с pipeline |
| `vision` | Vision-анализатор (OpenAI/Anthropic/Gemini, автовыбор), `read_document` |
| messaging | `call_agent`, `hitl_request`, поиск контекста и фактов, `send_message` |
| `email` | `send_email`, `send_email_with_attachment`, `fetch_emails`, `reply_to_email` |
| `task_scheduling` | события, напоминания, расписание, поиск свободного времени |
| `procurement` | `analyze_rfq`, `find_analogs`, `calculate_margin`, `supervisor_check`, `send_quotation` |
| `internet_search` | поиск цен по дистрибьюторам, конвертация валют |
| `orchestration` | `orchestrate_task` |
| `project_management` | инструментов не добавляет — работает через A2A |

## Про «навыки» в Agent Card

⚠️ Существенная деталь для технической демонстрации: **skills в A2A-карточке декоративны.**
Они генерируются синтетически из конфига — одна базовая `agent_query` плюс по одной на каждый
элемент `own_tools` и `capabilities`. Поскольку `own_tools` пуст у всех 17 шаблонов, типичный
агент публикует **один-два skill'а**, а Memorizer и Communicator — ровно один (`agent_query`).

Ни оркестратор, ни менеджер удалённых агентов не используют `card.Skills` для выбора
исполнителя — выбор делает LLM по текстовому описанию агента. Единственный потребитель
skills — MCP-инструмент `agent_capabilities`.

## Что общее у всех агентов

Единый Go-бинарник, различие только в build tags и конфигурации из Portal. Независимо от
тегов каждый агент получает: A2A-сервер, `/health` и `/metrics`, аутентификацию, rate limit
120 req/min, HMAC-подпись, OpenTelemetry, инструменты `fetch_url`, `search_arxiv` и Wolfram.

Communicator ведёт каналы Telegram/Mattermost и реализует [[proactive-messenger-mode]]
(наблюдение за каналом + суточный дайджест). Writer собирает документы через
[[document-pipeline]].

См. [[oxtech-platform]], [[a2a]], [[orchestration]].

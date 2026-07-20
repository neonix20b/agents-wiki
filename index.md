# Индекс wiki

Каталог всех страниц. Обновляется при каждом инжесте. Правила — в [CLAUDE.md](CLAUDE.md).

## Источники (wiki/sources/)
- [oxtech-multiagent-platform-presentation](wiki/sources/oxtech-multiagent-platform-presentation.md) — конспект презентации платформы Oxtech, 12 слайдов (ингест 2026-07-20).
- [ox-ai-workers-readme](wiki/sources/ox-ai-workers-readme.md) — конспект README библиотеки ox-ai-workers + таблица преемственности идей (ингест 2026-07-20).
- [oxtech-agents-registration-certificate](wiki/sources/oxtech-agents-registration-certificate.md) — свидетельство о гос. регистрации ПО «Oxtech Agents», RU 2026613582, правообладатель ООО «ОКСТЕХ» (ингест 2026-07-20).
- [gigacowork-web-research](wiki/sources/gigacowork-web-research.md) — сводка публикаций о запуске GigaCowork: Habr, vc.ru, CNews и др. (ингест 2026-07-20).
- [a2a-vs-mcp-web-research](wiki/sources/a2a-vs-mcp-web-research.md) — сводка публикаций о протоколах A2A и MCP: Auth0, Merge.dev и др. (ингест 2026-07-20).
- [russian-llm-platforms-web-research](wiki/sources/russian-llm-platforms-web-research.md) — сводка материалов о LLM-ландшафте РФ: MWS, обзоры рынка, ДИТ Москвы (ингест 2026-07-20).

## Сущности (wiki/entities/)
- [oxtech-platform](wiki/entities/oxtech-platform.md) — мультиагентная платформа Oxtech: архитектура, единая кодовая база агентов, системы агентов, принципы, go-to-market.
- [agents-roster](wiki/entities/agents-roster.md) — фактический состав агентов: 17 шаблонов, 13 в Production, 11 отвечают.
- [oxtech-manager](wiki/entities/oxtech-manager.md) — жизненный цикл агентов: сборка, деплой, метрики, health-check, изоляция.
- [keylink](wiki/entities/keylink.md) — второй прикладной продукт на платформе: закупки электронных компонентов.
- [oxdocs](wiki/entities/oxdocs.md) — AI-редактор документов на платформе (LaTeX по ГОСТ → PDF).
- [oxmodel](wiki/entities/oxmodel.md) — LLM-шлюз: любой провайдер, on-premise, учёт токенов.
- [ox-ai-workers](wiki/entities/ox-ai-workers.md) — открытая Ruby-библиотека агентного фреймворка, предшественница платформы.
- [oxtech-company](wiki/entities/oxtech-company.md) — ООО «ОКСТЕХ»: реквизиты, статусы, активы ИС.
- [moscow-innovation-cluster](wiki/entities/moscow-innovation-cluster.md) — МИК (i.moscow): участие Oxtech и релевантные меры поддержки.
- [gigacowork](wiki/entities/gigacowork.md) — конкурент: платформа ИИ-агентов Сбера («Салют для бизнеса»), тестовый доступ с 19.05.2026.

## Концепции (wiki/concepts/)
- [a2a](wiki/concepts/a2a.md) — протокол взаимодействия агент–агент.
- [mcp](wiki/concepts/mcp.md) — протокол доступа агентов к инструментам и данным.
- [orchestration](wiki/concepts/orchestration.md) — оркестрация агентов: от Assistant::Orchestrator в gem до Orchestrator+A2A в платформе.
- [inner-monologue-fsm](wiki/concepts/inner-monologue-fsm.md) — внутренний монолог + конечный автомат: паттерн управления агентом из ox-ai-workers.
- [intellectual-property](wiki/concepts/intellectual-property.md) — реестр активов ИС Oxtech: что оформлено, что нет, меры поддержки.

## Синтез (wiki/synthesis/)
- [gigacowork-vs-oxtech](wiki/synthesis/gigacowork-vs-oxtech.md) — сравнение с GigaCowork: сходства, различия по 10 осям, выводы для позиционирования.
- [a2a-vs-mcp](wiki/synthesis/a2a-vs-mcp.md) — разница протоколов, 6 ограничений MCP-only межагентных архитектур, аргументация A2A+MCP для Oxtech.
- [russian-llm-landscape](wiki/synthesis/russian-llm-landscape.md) — LLM-платформы в РФ 2026: провайдеры для Oxmodel, конкуренты, образ заказчика (ДИТ).
- [dit-agent-factory-concept](wiki/synthesis/dit-agent-factory-concept.md) — концепция для ДИТ Москвы: городская фабрика агентов, комнаты-рынки навыков, зрелость, open core на Mos.Hub.

## Deliverables
_(пока пусто — договоры, планы, отчёты, презентации будут в deliverables/)_

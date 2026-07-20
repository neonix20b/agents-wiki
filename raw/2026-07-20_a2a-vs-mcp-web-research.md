# Веб-исследование: A2A vs MCP

Собрано 2026-07-20. Источники:
- Auth0: https://auth0.com/blog/mcp-vs-a2a/ (гайд по обоим протоколам, Agent Cards, client/remote agents)
- Merge.dev: https://www.merge.dev/blog/mcp-vs-a2a
- TrueFoundry: https://www.truefoundry.com/blog/mcp-vs-a2a
- Atlan: https://atlan.com/know/mcp/mcp-vs-a2a-protocol/
- Auth0+Google Cloud (безопасность A2A): https://auth0.com/blog/auth0-google-a2a/

## Факты
- MCP (Anthropic, ноябрь 2024): «вертикальный» протокол — агент → инструменты/данные. Клиент-сервер, схемы функций, structured tool calls, авторизация OAuth 2.1/API keys.
- A2A (Google, апрель 2025; далее — Linux Foundation): «горизонтальный» протокол — агент ↔ агент. JSON поверх HTTP; Agent Cards — публикуемые самоописания возможностей агента для discovery без раскрытия внутренней реализации; роли client agent / remote agent; задачи с жизненным циклом, параллельная работа, промежуточный прогресс, встречные вопросы (follow-ups).
- Консенсус источников: протоколы комплементарны, не конкурируют. MCP расширяет «что может один агент», A2A — «как агенты сотрудничают». Production multi-agent системы используют оба: MCP для доступа к данным на агента, A2A для координации задач между агентами.
- Паттерн «агент как MCP-инструмент» существует (agent wrapped as tool), но сводит взаимодействие к синхронному вызову функции.

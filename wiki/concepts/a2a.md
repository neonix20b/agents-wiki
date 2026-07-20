---
type: concept
created: 2026-07-20
updated: 2026-07-20
sources: [raw/2026-07-20_oxtech-multiagent-platform.pdf]
tags: [protocol]
---
# A2A (Agent-to-Agent)

Открытый протокол взаимодействия между агентами (Google, апрель 2025). «Горизонтальный»: агент ↔ агент, роли client/remote agent, Agent Cards для discovery возможностей, задачи с жизненным циклом (working / input-required / completed), длительные задачи и промежуточный прогресс.

В [[oxtech-platform]] используется для вызовов между Orchestrator и специализированными агентами; фактические A2A-вызовы видны в метриках и траекториях (например, `a2a_call: financer, writer, mailer`).

См. также [[mcp]]; сравнение подходов и ограничения MCP-only архитектур — [[a2a-vs-mcp]].

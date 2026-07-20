---
type: concept
created: 2026-07-20
updated: 2026-07-20
sources: [raw/2026-07-20_oxtech-multiagent-platform.pdf, raw/2026-07-20_ox-ai-workers-readme.md]
tags: [architecture, agents]
---
# Оркестрация агентов

Паттерн: центральный оркестратор распределяет работу между специализированными агентами и контролирует результат. Ключевой тезис Oxtech: модель отвечает → агент выполняет задачу → **система агентов ведёт процесс**.

Эволюция в продуктах Oxtech:
- [[ox-ai-workers]]: `Assistant::Orchestrator` с заданным workflow + инструмент Pipeline для связи ассистентов и общего контекста.
- [[oxtech-platform]]: Orchestrator как отдельный агент; связь по открытому протоколу [[a2a]], инструменты через [[mcp]]; живой граф вызовов, трассировка каждого шага.

См. также [[inner-monologue-fsm]].

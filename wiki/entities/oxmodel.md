---
type: entity
created: 2026-07-20
updated: 2026-07-20
sources: [raw/2026-07-20_oxtech-multiagent-platform.pdf]
tags: [product, llm]
---
# Oxmodel

LLM-шлюз [[oxtech-platform]]: агенты не привязаны к конкретной модели или вендору.

- Провайдеры: GigaChat, YandexGPT (контуры с локализацией), OpenAI, Anthropic, Gemini (где допустимо), локальные open-source модели.
- Разворачивается on-premise в контуре заказчика.
- Учёт и контроль: лимиты, расход токенов по агентам, единая точка аудита обращений к LLM.

Предшественник идеи — провайдеро-независимость в [[ox-ai-workers]] (смена LLM через `uri_base`: OpenAI, DeepSeek и любые API-совместимые).

Ландшафт доступных в РФ моделей и платформ, кандидаты на подключение (MWS GPT, Cotype, T-Pro) и ближайший функциональный аналог (MWS GPT) — [[russian-llm-landscape]].

Источник: [[oxtech-multiagent-platform-presentation]].

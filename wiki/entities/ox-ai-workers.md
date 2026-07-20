---
type: entity
created: 2026-07-20
updated: 2026-07-20
sources: [raw/2026-07-20_ox-ai-workers-readme.md]
tags: [library, ruby, open-source]
---
# OxAiWorkers (ox-ai-workers)

Открытая Ruby-библиотека (gem, MIT) команды Oxtech — ранняя разработка, идеи которой легли в основу [[oxtech-platform]]. Репозиторий: https://github.com/neonix20b/ox-ai-workers.

Агентный фреймворк: задачи решаются связкой конечного автомата, внутреннего монолога и внешних инструментов ([[inner-monologue-fsm]]).

## Архитектура
- **Assistant** (высокий уровень): Sysop (администрирование), Coder, Localizer, Painter, Expert (Wolfram Alpha), Orchestrator — координация команды ассистентов ([[orchestration]]).
- **Iterator** (низкий уровень): роль, инструменты, шаги, callbacks (on_inner_monologue, on_outer_voice, on_finish).
- **Worker**: Request (немедленно) / DelayedRequest (batch API, −50% стоимости, до 24 ч).
- **Tools**: Eval, FileSystem, Pixels, Wolfram, Pipeline, Database, Converter; свои — через ToolDefinition, общее состояние через `context`.

## Заметные механизмы
- `call_stack` — принудительный порядок вызова функций.
- `stop_double_calls` — защита от повторных вызовов и зацикливания рассуждений.
- Провайдеро-независимость через `uri_base` (OpenAI, DeepSeek и др.) — предшественник [[oxmodel]].
- Мультимодальность (PDF, изображения), I18n en/ru, CLI.

Источник: [[ox-ai-workers-readme]].

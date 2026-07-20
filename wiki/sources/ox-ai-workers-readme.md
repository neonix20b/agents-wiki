---
type: source
created: 2026-07-20
updated: 2026-07-20
sources: [raw/2026-07-20_ox-ai-workers-readme.md]
tags: [github, ruby, library, agents]
---
# README библиотеки ox-ai-workers

Конспект README репозитория https://github.com/neonix20b/ox-ai-workers (снапшот 2026-07-20). Библиотека [[ox-ai-workers]] — ранняя разработка команды, предшествующая [[oxtech-platform]].

## Ключевые тезисы

- Ruby gem: решение задач генеративным ИИ через **конечный автомат** (гем `state_machine`) + **внутренний монолог** + **внешние инструменты** — см. [[inner-monologue-fsm]].
- Двухуровневый API: высокоуровневые **Assistants** (Sysop, Coder, Localizer, Painter, Expert/Wolfram, Orchestrator) и низкоуровневая связка **Iterator + Worker + Tools**.
- **Workers**: `Request` — немедленное выполнение; `DelayedRequest` — batch API с экономией до 50% (выполнение до 24 ч), хранение `batch_id` в БД для Rails.
- **Tools**: Eval (ruby/sh), FileSystem, Pixels (генерация изображений: DALL-E 3, GPT-Image-1, Stability), Wolfram, Pipeline (координация ассистентов), Database, Converter. Кастомные — через `ToolDefinition` (`define_function`/`property`); метод `context` даёт общее состояние нескольким ассистентам.
- **Управление вызовами функций**: `call_stack` — принудительный порядок вызовов; `stop_double_calls` — запрет повторного вызова подряд (по умолчанию для inner_monologue/outer_voice — защита от зацикливания рассуждений).
- **Orchestrator** — ассистент, координирующий команду ассистентов по заданному workflow — прообраз оркестратора платформы, см. [[orchestration]].
- Callbacks состояний: on_inner_monologue, on_outer_voice, on_finish; стриминг ответов.
- Мультимодальность: add_file (PDF), add_image (URL/binary, detail low/high/auto).
- Модели: OpenAI, DeepSeek, любой API-совместимый провайдер через `uri_base` — идея, развитая в [[oxmodel]].
- I18n en/ru; CLI (`oxaiworkers init|run`); лицензия MIT.

## Преемственность идей → платформа Oxtech

| ox-ai-workers (gem) | [[oxtech-platform]] |
|---|---|
| Assistant::Orchestrator + Pipeline | Orchestrator + A2A между агентами |
| Специализированные ассистенты (Sysop, Coder…) | 12 специализированных агентов |
| Tools + ToolDefinition | MCP-слой, 60+ инструментов |
| Смена провайдера через uri_base | Oxmodel — LLM-шлюз |
| call_stack, stop_double_calls | Контроль действий, ограничение инструментов |
| inner_monologue / outer_voice | Трассировка траекторий |

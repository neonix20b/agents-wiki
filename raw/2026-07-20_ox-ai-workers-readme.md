# Снапшот README ox-ai-workers

Источник: https://github.com/neonix20b/ox-ai-workers (README.md, main, получен 2026-07-20).
Полный текст — в репозитории; ниже зафиксированы структура и ключевые факты на дату снапшота.

- Ruby gem `ox-ai-workers`: конечный автомат (state_machine) + генеративный ИИ (ruby-openai) для решения задач через внутренний монолог и внешние инструменты.
- Уровни API: Assistant (высокий) / Iterator + Worker + Tools (низкий).
- Workers: Request (немедленно), DelayedRequest (batch API, экономия до 50%, выполнение до 24 ч; хранение batch_id в БД для Rails).
- Assistants: Sysop, Coder, Localizer, Painter, Expert (Wolfram), Orchestrator (координирует несколько ассистентов).
- Tools: Eval (ruby/sh), FileSystem, Pixels (изображения), Wolfram, Pipeline (связь ассистентов), Database, Converter.
- Кастомные инструменты: module ToolDefinition, define_function/property; метод context — общее состояние между ассистентами.
- Управление функциями: call_stack (принудительный порядок вызовов), stop_double_calls (запрет повторных вызовов; по умолчанию для inner_monologue и outer_voice).
- Callbacks: on_inner_monologue, on_outer_voice, on_finish.
- Файлы и изображения: add_file (PDF), add_image (url/binary, detail: low/high/auto).
- Модели: OpenAI, DeepSeek и любые API-совместимые (uri_base), image-модели OpenaiDalle3, OpenaiGptImage, StabilityImages.
- I18n: локали en/ru, ассистенты с разными локалями.
- CLI: oxaiworkers init / init full / run sysop; каталог .oxaiworkers-local.
- Лицензия MIT.

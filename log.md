# Журнал

Append-only. Формат: `## [YYYY-MM-DD] ingest|query|deliverable|lint | Название`.

## [2026-07-20] ingest | Инициализация базы знаний
Создана структура agents-wiki по паттерну LLM Wiki (Karpathy): raw / wiki / deliverables / templates, схема в CLAUDE.md.

## [2026-07-20] ingest | Презентация «Мультиагентная платформа» (Oxtech)
Исходник: raw/2026-07-20_oxtech-multiagent-platform.pdf. Создано: sources/oxtech-multiagent-platform-presentation, entities/oxtech-platform, entities/oxdocs, entities/oxmodel, concepts/a2a, concepts/mcp. Обновлён index.md.

## [2026-07-20] ingest | README ox-ai-workers (GitHub)
Исходник: raw/2026-07-20_ox-ai-workers-readme.md (снапшот README github.com/neonix20b/ox-ai-workers). Создано: sources/ox-ai-workers-readme, entities/ox-ai-workers, concepts/orchestration, concepts/inner-monologue-fsm. Обновлено: entities/oxtech-platform (раздел «История»), entities/oxmodel (предшественник идеи), index.md.

## [2026-07-20] ingest | Свидетельство oxEngine + профиль ООО «ОКСТЕХ» в МИК
Исходники: raw/2026-07-20_oxengine-software-registration-certificate.pdf (RU 2014613157), raw/2026-07-20_imoscow-oxteh-company-page.md (i.moscow/company/54892725). Создано: sources/oxengine-registration-certificate, entities/oxtech-company, entities/moscow-innovation-cluster, concepts/intellectual-property. Обновлено: entities/oxtech-platform (ссылка на компанию), index.md.

## [2026-07-20] ingest | Конкурент GigaCowork (веб-исследование)
Исходник: raw/2026-07-20_gigacowork-web-research.md (Habr, vc.ru, CNews, Kommersant, TAdviser). Создано: sources/gigacowork-web-research, entities/gigacowork, synthesis/gigacowork-vs-oxtech (сравнение + выводы для позиционирования). Обновлён index.md.

## [2026-07-20] query | Тезис позиционирования: self-service vs профессиональное внедрение
В synthesis/gigacowork-vs-oxtech добавлен ключевой тезис (Д. Смолев): GigaCowork — ставка на простых пользователей, Oxtech — на команду внедрения и гибкую адаптацию под заказчика; с оговоркой про сегментацию.

## [2026-07-20] ingest | Исследование A2A vs MCP
Исходник: raw/2026-07-20_a2a-vs-mcp-web-research.md (Auth0, Merge.dev, TrueFoundry, Atlan). Создано: sources/a2a-vs-mcp-web-research, synthesis/a2a-vs-mcp (ограничения MCP-only, аргументы A2A+MCP). Обновлено: concepts/a2a, concepts/mcp, synthesis/gigacowork-vs-oxtech (строка «Протоколы»), index.md.

## [2026-07-20] ingest | LLM-платформы в России (веб-исследование)
Исходник: raw/2026-07-20_russian-llm-platforms-web-research.md (MWS, vc.ru, azoneai, just-ai, ict.moscow и др.). Создано: sources/russian-llm-platforms-web-research, synthesis/russian-llm-landscape (таблица игроков, роли: провайдер/конкурент/заказчик, выводы). Обновлено: entities/oxmodel (ссылка на ландшафт), index.md.
## [2026-07-20] ingest | Свидетельство о госрегистрации ПО «Oxtech Agents» (RU 2026613582)
Исходник: raw/2026-07-20_oxtech-agents-registration-certificate.pdf. Ключевое: правообладатель — ООО «ОКСТЕХ» (юрлицо, не физлицо), предмет регистрации — сама платформа, дата регистрации 06.02.2026, авторы Повалихин А. И. и Смолев Д. С. Создано: sources/oxtech-agents-registration-certificate. Обновлено: concepts/intellectual-property (разделение реестров Роспатент / Минцифры), entities/oxtech-company, index.md. Закрывает пробел «правообладатель ИС — физлицо», отмеченный при проверке полноты.

## [2026-07-20] ingest | Сверка вики с кодовой базой
Источник: код репозиториев portal@359f142, agent@10ba1be, manager@2ecb1d5, documents@6fe60a7 + живой agent_list. Создано: entities/agents-roster, entities/oxtech-manager, entities/keylink. Обновлено: entities/oxtech-platform, entities/oxmodel, concepts/mcp, concepts/a2a, concepts/orchestration, index.md. Уточнены цифры: 67 MCP-инструментов Portal (не 49/50), 17 шаблонов агентов / 13 в Production / 11 отвечают, a2a-go v2.3.1 + ADK v1.4.0.

## [2026-07-20] lint | Удаление oxEngine (RU 2014613157) из вики
Свидетельство oxEngine 2014 г. добавлено по ошибке — относится к другой программе и не имеет отношения к платформе. Удалены: raw/2026-07-20_oxengine-software-registration-certificate.pdf, wiki/sources/oxengine-registration-certificate. Очищены ссылки в concepts/intellectual-property, entities/oxtech-company, sources/oxtech-agents-registration-certificate, index.md. Актуальный документ по правам на платформу — RU 2026613582 «Oxtech Agents».

## [2026-07-20] lint | Синхронизация после pull: разрешение противоречия по провайдерам
После pull (4 коммита: свидетельство Oxtech Agents, удаление oxEngine, сверка с кодовой базой, AGENTS.md) в synthesis/russian-llm-landscape исправлены роли GigaChat/YandexGPT: «поддержан» → «кандидат, по коду не подключён» (по данным аудита в entities/oxmodel). Выявлены битые wikilinks на несозданные страницы: claims-vs-code, observability, hitl, oxtech-portal, oxtech-codebase-audit.

## [2026-07-20] query | Концепция фабрики агентов для ДИТ Москвы
По итогам двух раундов вопросов к Д. Смолеву создана synthesis/dit-agent-factory-concept: конструктор+фабрика агентов, комнаты как рынки навыков, показатель зрелости с агентом-аттестатором, open core на Mos.Hub, Oxtech — техпартнёр ядра, пилот — контрольные соотношения документов, прямое сравнение с GigaCowork. Контекст: встреча с ДИТ назначена, мотив — избежать вендор-лока Сбера. Обновлён index.md.

## [2026-07-20] deliverable | Презентация для ДИТ Москвы «Городская фабрика ИИ-агентов»
Создано: deliverables/presentations/2026-07-20_dit-moscow-agent-factory_v1.pptx — 14 слайдов по synthesis/dit-agent-factory-concept: развилка «аренда vs владение», ядро+правила, комнаты-площади, конвейер фабрики со шкалой зрелости, LLM-стратегия, прямое сравнение с GigaCowork, экосистема университетов, пилот «контрольные соотношения», дорожная карта, «почему Oxtech». Только защитимые формулировки (без «деплой 15–25 с», без «поддерживаем GigaChat»); заметки докладчика на каждом слайде. Обновлён index.md.

## [2026-07-20] deliverable | Презентация для ДИТ v2 — самодостаточный раздаточный формат
По замечаниям Д. Смолева (v1 — «оторванные слова», случайный стиль) создана deliverables/presentations/2026-07-20_dit-moscow-agent-factory_v2.pptx: 15 слайдов по образцу качественной презентации (ROOMY): кикер-рубрика, заголовок-утверждение, подзаголовок и все блоки полными предложениями, вывод-плашка на каждом слайде — читается без докладчика. Дизайн собственный: глубокий зелёный + красная нумерация. v1 сохранена по конвенции версий. Обновлён index.md. Урок в шаблоны: раздаточный материал ≠ слайды для доклада.
## [2026-07-20] ingest | Официальные материалы протокола A2A
Исходник: raw/2026-07-20_a2a-protocol-official-docs.md (github.com/a2aproject/A2A + a2a-protocol.org, проверено WebFetch). Создано: sources/a2a-protocol-official-docs. Обновлено: concepts/a2a — добавлены разделы «Статус протокола» и «Преимущества протокола» (Linux Foundation, спецификация v1.0.1 от 28.05.2026, непрозрачность как модель безопасности, task lifecycle, три режима взаимодействия, 6 SDK, три стратегии обнаружения). Зафиксировано: API реестра агентов спецификацией не стандартизован — собственные «комнаты» легитимны как расширение. Обновлён index.md.

## [2026-07-20] ingest | Проактивный режим агента в мессенджере (Mattermost)
Источник: код oxtech_agent@10ba1be, oxtech_portal@359f142, Tasks/233_mattermost_autonomy_toggle. Создано: concepts/proactive-messenger-mode — три сценария (наблюдение с буферизацией, дайджест 08:00 MSK, понедельничные напоминания), логика вмешательства, устройство буфера, содержание разбора, тумблер автономии с двумя путями доставки, границы применимости. Уточнено: флаг mattermost_autonomy_enabled по умолчанию ВКЛЮЧЁН (записи в БД нет, геттер отдаёт true); на проде выключен нажатием тумблера 16.07.2026. Обновлён index.md.

## [2026-07-20] deliverable | Word-концепция «Городская фабрика ИИ-агентов» для ДИТ
Создано: deliverables/plans/2026-07-20_dit-moscow-agent-factory-concept_v1.docx — концепт-записка 6 стр. для передачи в ДИТ после встречи: титульный лист с реквизитами ООО «Окстех», основные положения, предпосылки, суть концепции (конструктор/комнаты/конвейер), функциональные возможности, 3 сценария использования, выгоды, прямое сравнение с GigaCowork (таблица, по открытым данным), о разработчике и следующие шаги. Стиль профессиональный, функционально-выгодный, без технических деталей. Обновлён index.md.

## [2026-07-20] deliverable | Переговорная презентация для ДИТ Москвы v3
Создано: deliverables/presentations/2026-07-20_dit-moscow-agent-factory_v3.pptx — новая концепция и дизайн с логотипом Oxtech, 15 основных слайдов и 3 технических приложения для личной встречи руководителя с техническими специалистами. Акцент: технологическое партнёрство с ДИТ, подтверждённые возможности production-платформы, A2A+MCP, единая кодовая база агентов, городская фабрика и открытое сравнение с GigaCowork. Явно разделены работающие компоненты и совместная разработка; добавлены заметки докладчика. Обновлён index.md.
## [2026-07-20] schema | Правило черновиков для deliverables
В CLAUDE.md добавлено: перед финальным документом создаётся черновик в deliverables/drafts/ (не в git, добавлено в .gitignore); финальная версия в целевой папке — только после одобрения пользователем. Цель — не плодить версии финальных файлов.

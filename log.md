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

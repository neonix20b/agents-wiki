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

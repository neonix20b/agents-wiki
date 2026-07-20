# Веб-исследование: LLM-платформы, доступные в России

Собрано 2026-07-20. Источники:
- MWS: https://mws.ru/services/mws-gpt/ ; Habr (как устроена платформа): https://habr.com/ru/companies/ru_mts/articles/967478/ ; новости MWS про Open Source LLM и мультиагентность
- Обзоры рынка: https://vc.ru/ai/2733649 (список моделей и сервисов 2026), https://azoneai.ru/blog/10-sravnenie-llm/ , https://ai-journal.ru/rossijskie-nejroseti/
- Агентные платформы: https://just-ai.com/blog/sravnenie-rossijskih-platform-dlya-sozdaniya-ai-agentov , https://blog.albato.ru/rossijskie-platformy-dlya-ii-agentov-v-2026-top-10-s-czenami-i-sravneniem/
- Москва/ДИТ: https://ict.moscow/news/ai-models-in-russia-2025/ , Ведомости.Город (ИИ в Москве), CNews (Mos.Hub, open source)
- Госуслуги: TAdviser / 3dnews об ИИ-консультанте Минцифры

## Факты
- **MWS GPT (МТС Web Services)**: LLM-платформа-агрегатор — 70+ моделей (включая ведущие open-source), OpenAI-совместимый API, три варианта развёртывания: SaaS / Hybrid / On-premise; мультиагентные и low-code возможности; инфраструктура MWS Cloud (GPU в РФ). Развивается ~2,5 года.
- **GigaChat (Сбер)**: мультимодальность (текст, голос, изображения через Kandinsky); GigaChat 2 Lite — лучшее цена/качество на русском (оценка обзоров); в 02.2026 цена снижена почти втрое. GigaChat Business (03.2026) — корпоративная no-code платформа ИИ-агентов.
- **YandexGPT (Яндекс)**: линейка Lite / Pro / 5 Pro (reasoning, контекст 128k); 5.1 Pro — снижены галлюцинации. Yandex AI Studio — платформа ИИ-агентов (no-code с 09.2025, reasoning-агенты на DeepSeek-V3.2 с 03.2026).
- **Cotype (MTS AI)**: корпоративная модель для закрытых контуров, on-premise.
- **T-Pro (Т-Банк)**: open-source модель, можно разворачивать на своих серверах.
- **Cloud.ru**: облачный доступ к open-source LLM (в т.ч. бесплатный тир).
- **ДИТ Москвы**: собственной публичной LLM-платформы не продаёт; строит платформу полного цикла «Искусственный интеллект» (с 2024; ~300 обученных моделей за 2024, 90+ ИИ-сервисов города), дообучает open-source модели (LoRA) под городские задачи (подтверждено публично — А. Подопросветов, ДИТ); open-source инфраструктура Mos.Hub, платформа MosTech.
- **Минцифры/Госуслуги**: ИИ-консультант на отечественной нейросети (бета).
- Рынок агентных платформ РФ 2026 (10+): GigaChat Business, Yandex AI Studio, Just AI, Tomoru, TWIN, Albato, Nodul, Битрикс24, MWS, Cloud.ru; отдельно GigaCowork.
- TAdviser: рынок платформ легального корпоративного доступа к зарубежным ИИ-моделям вырос до 3 млрд ₽/год.

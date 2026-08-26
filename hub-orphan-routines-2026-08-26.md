[все дашборды](index.html) · категория: Флот и узлы · [← _sync-conflicts-ALERT](_sync-conflicts-ALERT.html) · [improvements-2026-07-07-fleet-arch →](improvements-2026-07-07-fleet-arch.html)

# Сироты планировщика на хабе A-2022BAYAREA

Замер 26.08.2026 прибором `scheduled_tasks_doctor.py`: **269 папок задач на диске, 23 в реестре, 246 сирот**.
Сирота = промпт `SKILL.md` цел, но ни один реестр приложения на него не ссылается.

| корзина | сколько | что делаем |
|---|---|---|
| A. был enabled + cron в бэкапе 19.08 | 9 | **воскрешены 26.08** |
| B. был enabled, но одноразовый | 9 | не воскрешать — отработали |
| C. в бэкапе был выключен | 117 | не воскрешать — гасили намеренно |
| D. нет в бэкапе 19.08 | 99 | разбор глазами (создано после 19.08) |
| E. в описании стоит «переехал / влит / заглушена» | 12 | не воскрешать — решение отменено |


## A. Воскрешены (были живые, крон взят из бэкапа 19.08) (9)

- `claudeai-sync-daily` · 2026-08-11 · [ACTIVE -- DO NOT DELETE. The 2026-07-20 "[DISABLED -- migrated to Windows Task]" label was WRONG and is retracted 2026-
- `content-drain-live` · 2026-08-11 · Живая (in-app) рельса дренажа контент-воронки: 2 самых старых сида -> реальные тексты + гейт + часы + обратная запись. Д
- `facebook-diary-daily` · 2026-07-25 · Daily ~21:15 — turn the day's openclaw conversations (ALL machines via vault corpus + local fill) into one honest Facebo
- `hanging-tasks-digest` · 2026-08-11 · Ежедневно (05:52 Лиссабон) — сводка ВИСЯЧИХ задач Антону в TG-папку. Источник истины = реестр 10-Tasks; голосовая очеред
- `preference-sweep-daily` · 2026-08-11 · Daily sweep свежих чатов на повторяющиеся предпочтения + новые артефакты → предлагает на ревью (file + Telegram). Review
- `skill-gap-daily` · 2026-08-11 · [WEEKLY Mon 00:50 — 2026-07-04 Anton, token-save]. Еженедельный аудит «какой скилл строить дальше» (внутренние повторы +
- `tg-relationships-weekly` · 2026-08-11 · Будильник №5 (еженедельный): дни рождения на неделю + важные лиды, с кем давно не общались. Осторожен с качеством данных
- `tg-weekly-digest` · 2026-08-11 · Будильник №6 (вс вечером): недельный свод — что сделано/что зависло — из brain_digest.py, в Telegram. [HUB-owned 2026-06
- `voice-triage` · 2026-08-19 · 1x/день (10:00 Лиссабон) триаж НОВЫХ голос/текст заметок Антона из TG-хаба; корзины 🔧задача/💎альфа + КАЖДОЕ сообщение → 

## B. Одноразовые — отработали, не воскрешаем (9)

- `auto-a2022bayarea-260819-vcround-empty-strings` · 2026-08-19 · Починить пустые строки вместо NULL в vc_round (leads.db) — аналитика считает по 9% данных
- `auto-hub-260819-3posts-kits-killer-features` · 2026-08-19 · КОНТЕНТ: 3 поста «как это работает у нас» — память волт+RAG+SQLite · флот-раскатка с доказательством · независимые сторо
- `auto-hub-260819-cron-to-event-audit` · 2026-08-19 · АУДИТ: все кроны/поллеры флота — что переводить на событийную n8n-рельсу, что оставить рутиной. Ранжированный список ДО→
- `auto-hub-260819-dr-runner-monosnap` · 2026-08-19 · DR-раннер: DR26-08-19-HUB-02-1756 Monosnap упаковка под Долину — веер 6 рельс, забор отчётов, синтез, отдача Кириллу (сы
- `auto-hub-260819-vault-secret-scrub-mongo` · 2026-08-19 · Вычистить открытый пароль Mongo из волта, оригиналов и поискового индекса + эскалация ротации Антону
- `auto-hub-260820-mirror-mass-delete-gate` · 2026-08-19 · Зеркало волта E-to-F молча повторяет массовые удаления и рапортует «всё ок» — поставить гейт
- `auto-hub-260820-skill-collisions-local-shared` · 2026-08-19 · Развести коллизии local-brain-onboard/brain-onboard и local-github-growth/github-growth, открыть красный гейт skill_guar
- `auto-hub-260820-telegram-mcp-sse-runbook` · 2026-08-19 · Красная ячейка telegram-mcp-sse без карты и runbook: разобрать, починить или честно списать
- `auto-hub-260820-watchdogs-tell-truth` · 2026-08-19 · Три сторожа врут: нет дедупа алярмов, ложный RED от моргания arXiv, disabled трактуется как deprecated

## E. Отменённые решения — воскрешать нельзя (12)

- `auto-hub-260819-kamil-peer-watch` · 2026-08-19 · ВЫКЛЮЧЕНА 19.08 (правило Антона: лид-чаты проверяем сессией max 2×/сутки — исполнитель lead-thread-reply 45 9,18). Держи
- `auto-hub-260819-kirill-peer-watch` · 2026-08-19 · ВЫКЛЮЧЕНА 19.08 (правило Антона: лид-чаты проверяем сессией max 2×/сутки — исполнитель lead-thread-reply 45 9,18). Держи
- `connector-health-daily` · 2026-08-11 · [RUNS AS WINDOWS TASK "Claude Connector Health Daily" since 2026-07-20 (in-app MCP cron retired; survives Desktop-app de
- `faaa-weekly-sync` · 2026-08-11 · [RUNS AS WINDOWS TASK "Claude FAAA Weekly Sync" since 2026-07-20 (in-app MCP cron retired; survives Desktop-app death; m
- `fb-teaser-lag-watch` · 2026-08-06 · ⏸️ ВЫКЛЮЧЕН 06.08.2026 18:20 вместе с конвейером: сторож кричал бы «тизеры не уходят», хотя они остановлены НАМЕРЕННО (п
- `gmail-digest-morning` · 2026-08-23 · [RUNS AS WINDOWS TASK "Claude Gmail Digest Morning" since 2026-07-20 (in-app MCP cron retired; survives Desktop-app deat
- `health-weekly-sync` · 2026-08-11 · [RUNS AS WINDOWS TASK "Claude Health Weekly Sync" since 2026-07-20 (in-app MCP cron retired; survives Desktop-app death;
- `obsidian-backup-healthcheck` · 2026-08-11 · [RUNS AS WINDOWS TASK "Claude Obsidian Backup Healthcheck" since 2026-07-20 (in-app MCP cron retired; survives Desktop-a
- `session-unsticker-hourly` · 2026-08-05 · ⏸️ ВЫКЛЮЧЕНА 05.08.2026 22:30 — работу забрала дешёвая рельса «Claude Session Unsticker Tick» (Windows Task, каждые 15 м
- `token-spend-watchdog` · 2026-08-11 · [RUNS AS WINDOWS TASK "Claude Token Spend Watchdog" since 2026-07-20 (in-app MCP cron retired; survives Desktop-app deat
- `vault-janitor-nightly` · 2026-08-05 · ⏸️ MIGRATED TO MAYAK 2026-07-05: janitor теперь ночной cron на fleet-anchor (03:00 UTC, /home/anton/mayak_tasks/vault-ja
- `voice-sessions-runner` · 2026-08-06 · ⏸️ ЗАГЛУШЕНА 06.08 16:52 под приказ Антона «останови ВСЕХ РОБОТОВ» (15:15). Создана в 15:31 в неведении об этом приказе.

## D. Нет в бэкапе 19.08 — нужен разбор глазами (99)

- `_DELETED-cross-machine-robot-dryrun-20260624-153156` · 2026-06-20 · Phase-2 cross-machine bus TASK runner — DRY-RUN: classify pending bus items + AUTHORIZATION blocks, report to log only, 
- `auto-hub-260818-dr-discount-runner` · 2026-08-18 · AUTO-hub-260818: разогнать ДР DR26-08-18-HUB-02-2037 про скидку у дилера Mercedes Frankfurt
- `auto-hub-260818-dr-runner` · 2026-08-18 · AUTO-hub-260818: разогнать очередь ДР, в первую очередь DR26-08-18-HUB-01-1742 по конфигурации Mercedes V-Class
- `auto-hub-260819-kirill-reverse-eng-lab` · 2026-08-19 · УЧЁНЫЙ: реверс-инженерия системы Кирилла (Antigravity-оркестрация, фрактальная декомпозиция, спекроутинг, алгебра агенто
- `auto-hub-260821-bus-poison-messages` · 2026-08-21 · Шина не режет сообщения по лимиту 4096: три яд-строки вечно бьются в спуле при каждой отправке
- `auto-hub-260821-daily-longread-pair` · 2026-08-21 · Ежедневная пара лонгрид+девлог на GitHub: заглушка на завтра + сборка и публикация за сегодня
- `auto-hub-260821-dashboards-google-sheets` · 2026-08-21 · AUTO-ресёрч+пилот: дашборды в Google Sheets вместо HTML (хостинг, доступы, конкурентная запись пиров по колонкам), из го
- `auto-hub-260821-dead-owner-watchdogs` · 2026-08-21 · Сторожа кричат по выключенным владельцам, а телефонная сессия Антона лежит в реестре мёртвого аккаунта и не бегает с 18.
- `auto-hub-260821-dellm-canary-connector-health` · 2026-08-21 · Де-LLM канарейка: connector_health_daily из claude -p в чистый python (LLM-слой 28 дней красил RED в GREEN)
- `auto-hub-260821-dig-browser-rail-down` · 2026-08-21 · Сессия-копатель: browser-rail-down (счёт ≥3 → чинит корень по сумме кейсов)
- `auto-hub-260821-dig-fb-footer-contract` · 2026-08-21 · Сессия-копатель: контракт «футер FB → первый коммент» без исполнителя + 6 черновиков 15.08 (счёт 1 → статистировать)
- `auto-hub-260821-dig-notebooklm-stale-rail` · 2026-08-21 · Сессия-копатель: weekly-brain-audio-digest без аудио (счёт 2 → статистировать, не чинить корень)
- `auto-hub-260821-dr-fanout-vibe-teach` · 2026-08-21 · Разнести веером два свежих ДР из очереди (курсы для не-кодеров + экономика синтетических сотрудников)
- `auto-hub-260821-dr-teasers-daily` · 2026-08-21 · ДР-полоса: 10 тизеров в день из корпуса дипресёрчей в каналы @PaloAltoAi и @PaloAltoAiRu
- `auto-hub-260821-fleet-git-rail` · 2026-08-21 · Разгрести git-рельсу флота: старые авто-снимки режут .py, пуш отбит хуком
- `auto-hub-260821-fleet-routine-registry` · 2026-08-21 · AUTO-стройка: единый реестр рутин всего флота (рутины=сотрудники, офисы=машина+аккаунт), из голосовой hub:5678
- `auto-hub-260821-habr-promise-guardrails-agentevals` · 2026-08-21 · Хабр-обещание: прогнать трейсы через Invariant Guardrails и AgentEvals
- `auto-hub-260821-longread-devlog-rule` · 2026-08-21 · AUTO — довести правило про лонгрид/девлог до всех домов канона, из голосовой hub:5671
- `auto-hub-260821-longread-naming` · 2026-08-21 · Закрыть дельту по переименованию лонгрида (голосовая 5653): проверить движок daily_longread.py, оформить поручение Наташ
- `auto-hub-260821-npc-morning-prompt` · 2026-08-21 · Голосовая 5662: пост про «начальный промпт дня» (память+ситуация+статус+гормоны+тело), публикация в живой FB-тред серии 
- `auto-hub-260821-npc-post-daily-cycle` · 2026-08-21 · AUTO — оформить пост про сон/пробуждение как закрытие-открытие сессии, из голосовой hub:5659
- `auto-hub-260821-npc-post-initial-prompt` · 2026-08-21 · AUTO — оформить пост про «начальный промпт дня» человека, из голосовой hub:5662
- `auto-hub-260821-npc-post-logs-legacy` · 2026-08-21 · AUTO — оформить развёрнутый пост про логи/наследие NPC после «смерти», из hub:5668
- `auto-hub-260821-npc-post-session-length` · 2026-08-21 · AUTO — оформить пост про длину «сессии» человека (24ч/сон/vault), из голосовой hub:5656
- `auto-hub-260821-npc-post-soul-player` · 2026-08-21 · AUTO — оформить развёрнутый пост про душу-игрока/NPC (RPG-аналогия, Ghost in the Shell), из hub:5665
- `auto-hub-260821-npc-session-length` · 2026-08-21 · Голосовая 5656 (серия «AI, NPC или я?») — пост про длину сессии и параллельные сессии, публикация через /fb-post
- `auto-hub-260821-npc-sleep-index` · 2026-08-21 · Голосовая 5659 (серия «AI, NPC или я?») — пост про сон как индексацию памяти, публикация через /fb-post
- `auto-hub-260821-npc-who-is-player` · 2026-08-21 · Голосовая 5665: лонгрид «кто игрок» (душа/NPC-управление, WarCraft-аналогия, Ghost in the Shell + Blade Runner), серия «
- `auto-hub-260821-patent-post` · 2026-08-21 · Собрать FB-пост из голосовой Антона про PhD/патенты/академпрофиль, закрыть 2 фактических пробела (темы заявок, ссылка пр
- `auto-hub-260821-publedger-proof-gate` · 2026-08-21 · Системная починка: pub_ledger принимает «опубликовано» только с доказательством + верификация дня-1 vibe-teach
- `auto-hub-260821-red-canon-blocks-fleet` · 2026-08-21 · Красный CLAUDE.md блокирует раскатку канона на флот; проверить, жив ли ночной оптимизатор Маяка (фикс 14.08 не применён)
- `auto-hub-260821-review-after-rail-proven-and-tail` · 2026-08-21 · Хвост 81 просроченного review_after против капа 6 сессий/сутки
- `auto-hub-260821-routine-value-audit` · 2026-08-21 · Голосовая 5675: польза и цена КАЖДОЙ рутины — «одна рутина = один сотрудник», аудит пользы поверх переписи 21.08 + разбо
- `auto-hub-260821-school-stress-dr` · 2026-08-21 · Alpha Protocol DR: здоровьесберегающие технологии в образовании + длительность школьного дня (голосовая 5648) + пост в F
- `auto-hub-260821-seo-geo-kontakty-i-dr-kak-kontent` · 2026-08-21 · SEO/GEO для второго мозга (№15) + DR как контент (№22): контакты везде, синтез DR
- `auto-hub-260821-series-posts-ai-self-ordered-dr` · 2026-08-21 · Серия постов: ИИ сама заказывает себе Deep Research
- `auto-hub-260821-session-brief-shadow-verdict` · 2026-08-21 · Вердикт по брифу на старте сессии (session_brief, shadow до 13.08)
- `auto-hub-260821-shadow-harvest-daily` · 2026-08-21 · Жнец теней: harvest_watch.py + вердикты по созревшим теням/пилотам (закрывает разрыв CLAUDE.md §5.7 «две даты»)
- `auto-hub-260821-skill-conflicts-merge` · 2026-08-21 · Разобрать 13 sync-conflict копий скиллов: слить уникальные строки в живые SKILL.md, открыть гейт skill_guard
- `auto-hub-260821-task-inbound-collect-scores-last-messa` · 2026-08-21 · Сортировка входящего судит по ПОСЛЕДНЕМУ сообщению и роняет advisors в мусор
- `auto-hub-260821-tg-lock-no-timeout` · 2026-08-21 · Лок телеграм-сессии без таймаута: зависший процесс слепит 19 сторожей, 124 коллизии за сутки
- `auto-hub-260821-tg-rail-silent-undelivery-root-fix` · 2026-08-21 · Корни рельсы @***ySsd: молчащая недоставка (exit 0) + замок без TTL + непринятые посылки на хабе
- `auto-hub-260821-thought-journal-v2` · 2026-08-21 · Журнал мысли v2: по-файлово на рутину + читатель-дашборд; потребитель = менеджер-рутина, не Антон
- `auto-hub-260821-vibe-teach-day1` · 2026-08-21 · День 1 серии vibe-teach: написать и опубликовать первые посты (запуск серии)
- `auto-hub-260821-vibe-teach-day1-fb-retry` · 2026-08-21 · Дожать день 1 серии vibe-teach: FB-пост + остальные тизеры (TG-тизер RU уже вышел)
- `auto-hub-260821-vibe-teach-day1-publish` · 2026-08-21 · Опубликовать одобренный пост дня 1 серии vibe-teach (FB + тизеры TG/X/Threads)
- `auto-hub-260821-voice-session-tg-notify` · 2026-08-21 · AUTO-стройка: TG-нотификация «голосовая обработана → сессия поднята» в конвейере voice_sessions, из голосовой hub:5685
- `auto-hub-260821-vykatit-pochinennye-ssylki-na-palo-alto` · 2026-08-21 · Выкатить на живой palo-alto.ai уже починенные мёртвые ссылки и задокументировать рельсу деплоя
- `auto-hub-260822-class-counter-blind` · 2026-08-22 · Починка корня-энейблера: счётчик классов журнала поломок не считает (97% классов — одиночки), из-за чего правило третьей
- `auto-hub-260822-clobber-onair-root` · 2026-08-22 · Сессия-починка системного класса «перезапись чужого живого артефакта» (≥14 строк журнала): 5-почему по серии → заставить
- `auto-hub-260822-fix-inflight-dedup-class` · 2026-08-22 · AUTO — починка СИСТЕМНОГО класса (3-й рецидив, §5.10): дедуп смотрит диск/реестр, а параллельная сессия ещё пишет. Заявк
- `auto-hub-260822-fix-node-hardcode-github-registry` · 2026-08-22 · Убрать зашитое имя узла MacBook-Anton из github_routines_registry.py
- `auto-hub-260822-fleet-db-recovery` · 2026-08-22 · AUTO — оценить идею Антона (p2p-восстановление БД/state флота по аналогии с блокчейном) против уже существующей Syncthin
- `auto-hub-260822-github-25-routines-program` · 2026-08-22 · GitHub-25: программа прокачки личного профиля Антона (25 рутин, 90 дней)
- `auto-hub-260822-harvest-gran6` · 2026-08-21 · Урожай 🌾 грани 6: судить трёх копателей + токен-цена + перепрогон Gemini-рельсы
- `auto-hub-260822-help-flag-lint` · 2026-08-22 · Починка класса unparsed-flag-silently-runs-work: линт --help на все CLI-скрипты, тест в регресс-сетке
- `auto-hub-260822-lost-retro-decentralized-scale` · 2026-08-22 · AUTO — недописанные ЦЕННЫЕ артефакты (книга, главы, длинные тексты) → саммари + точка с запятой + в библиотеку волта. По
- `auto-hub-260822-peer-lost-session-light-retro` · 2026-08-22 · AUTO — рутина на КАЖДОМ пире: ночью берёт заснувшие сессии и делает по ним облегчённое ретро с полным RECALL. Из голосов
- `auto-hub-260822-q1r-fallback-hardening` · 2026-08-21 · 4 рутины Q1R: доказать переживание пустого бака существующей рельсой claude_run --extfallback, добавить где нет
- `auto-hub-260822-queue-recovery-14-dead` · 2026-08-21 · Ре-арм 14 одноразовых задач 21.08, убитых потолком сессий (голосовые Антона: DR, посты, лонгриды)
- `auto-hub-260822-reactivation-batch-followups` · 2026-08-22 · Ответить троим из реактивационного батча (Safak срочно) + онбординг Кевина-тестера
- `auto-hub-260822-rebrand-clawrush-to-charm` · 2026-08-22 · Ребренд: вычистить ClawRush → всё под CHARM (написание уточняется)
- `auto-hub-260822-red-tests-43` · 2026-08-22 · Погасить 43 красных теста регресс-сетки хаба по триажу 22.08 (real-fail → drift → infra)
- `auto-hub-260822-repair-browser-rail-down` · 2026-08-22 · Класс browser-rail-down стал системным (18-я поломка) — отдельная сессия починки
- `auto-hub-260822-repair-bus-send-flags-as-text` · 2026-08-22 · Класс bus_send.py принимает флаги как текст — сессия починки класса (3-я поломка, §5.10)
- `auto-hub-260822-repair-gate-substring-not-action` · 2026-08-22 · Класс «детектор судит подстроку, а не действие» — сессия починки класса (4-я поломка, §5.10)
- `auto-hub-260822-repair-git-snapshot` · 2026-08-21 · Оживить корневой git-снапшот ~/.claude (мёртв с 19.08, 3 доказанных корня) + честный exit-код в ps1
- `auto-hub-260822-repair-keep-core` · 2026-08-21 · Починки по аудиту KEEP-ядра: слепой sync_check, застрявшая шина, сторож бэкапа на облако, 13 sync-conflict в скиллах, ло
- `auto-hub-260822-retro-lost-na-pirah` · 2026-08-22 · AUTO — облегчённое ретро потеряшек на КАЖДОМ пире (не централизованно на хабе), из голосовых hub:5697 + hub:5699
- `auto-hub-260822-routine-org-model` · 2026-08-21 · Штатное расписание рутин: мама·приёмник·рельса·цена у каждой + мандат менеджера robot-audit-weekly на найм/увольнение
- `auto-hub-260822-routine-refactor-larva` · 2026-08-22 · AUTO — рутина-рефакторщик рутин + «личинка» самопочинки внутри рутины, из голосовой hub:5694
- `auto-hub-260822-routine-self-refactor-larva` · 2026-08-22 · AUTO — «личинка» самопочинки внутри рутины: 3 спотыкания подряд → рутина сама поднимает сессию рефакторинга себя. Из гол
- `auto-hub-260822-vibe-teach-cta-post` · 2026-08-22 · AUTO — короткий CTA-пост «начните пользоваться Claude Code/Codex + поддержите в комментариях», из голосовой hub:5690, вс
- `auto-hub-260823-dr-audit-hub-01-1606` · 2026-08-23 · Аудит применения DR26-08-21-HUB-01-1606 (рынок курсов по Claude Code для не-кодеров)
- `auto-hub-260823-dr-audit-hub-02-1609` · 2026-08-23 · Аудит применения DR26-08-21-HUB-02-1609 (экономика синтетических сотрудников)
- `auto-hub-260823-dr-audit-hub-04-1747` · 2026-08-23 · Аудит применения DR26-08-21-HUB-04-1747 (венгерский язык, проверка мема)
- `auto-hub-260823-dr-runner` · 2026-08-23 · AUTO-hub-260823-dr-runner — разнести заказ DR26-08-23-HUB-01-2221 (аяуаска) по веером внешних LLM и забрать отчёты
- `auto-hub-260823-dr-runner-touchbase` · 2026-08-23 · AUTO-hub-260823-dr-runner: разгрести очередь ДР (в т.ч. DR26-08-23-HUB-02-2226 touch base)
- `auto-hub-260823-dr-teaser-threads-x-rail` · 2026-08-23 · Достроить рельсы Threads + X для ДР-тизеров (заказ Антона 23.08: тизер каждого DR в Threads/FB/X)
- `auto-hub-260823-test-conveyor-top22` · 2026-08-22 · Конвейер «тесты пишет чужая подписка»: покрыть топ нагруженных деталей без теста, панель ломателей по канону рельс
- `auto-hub-260824-episode-spor-pro-tablicy` · 2026-08-23 · Эпизод «босс позвал спорить про таблицы»: лонгрид+девлог+тизеры из сессии стол-и-витрина (приказ Антона «делай B сам»)
- `auto-hub-260824-failing-routines-triage` · 2026-08-23 · Триаж 26 падающих рутин хаба (Canon Publish 96×/сут код 1) — сессия-детёныш ретро 23.08
- `auto-hub-260825-fleet-debt-drain` · 2026-08-25 · Дренаж долгов хаба перед флотом: 237 непринятых deploy-посылок, 13 старых UNPAID TASK, мерж fleet/main по владельцам, де
- `auto-hub-260829-harvest-sheets-tech` · 2026-08-23 · 🌾 Технический урожай тени №16 (Google-книга флота): 6 узлов пишут? ноль 429? ноль чужих строк?
- `auto-hub-260921-harvest-sheets-main` · 2026-08-23 · 🌾 ГЛАВНЫЙ урожай тени №16: заполняют ли ЛЮДИ человеческие колонки книги флота без напоминания
- `auto-hub-weekly-repo-release` · 2026-08-25 · AUTO-HUB-weekly-repo-release: субботняя рутина обновления топ-10 GitHub-репо лаборатории (портировать наработки, резать 
- `claudeai-courier-health` · 2026-06-28 · Daily auto-import of claude.ai web chats into the vault via Claude-in-Chrome (Anton's real logged-in browser) — pull → s
- `content-drain-daily` · 2026-08-22 · "DRAIN the content funnel: turn captured seeds into finished posts, gate them, arm the 24h clock. Counterpart of content
- `daily-troika-posts` · 2026-08-23 · Ежедневная тройка постов за предыдущий день: итог дня, факап дня, боль дня (приказ Антона 23.08.2026)
- `dr-daily-digest` · 2026-08-23 · Суточный DR-свод: отчёт Антону за 24ч + подъём аудит-сессий применения (заказ Антона голосом 23.08.2026)
- `five-hard-monthly` · 2026-07-22 · Пять трудных вопросов месяца: pressure-test убеждений Антона (belief-* + concept-bible-*) → TG чат 03
- `hub-deploy-unpack-daily` · 2026-08-21 · Хаб: ежедневно распаковывать непринятые посылки deploy-манифеста
- `intention-daily` · 2026-07-22 · Ночью 23:20 Лиссабон: намайнить намерения Антона из всех сессий дня → 2-3 поста-намерения с явной просьбой (голос Антона
- `spawn-visibility-probe` · 2026-07-29 · Разовая проба: видна ли в списке сессий сессия, запущенная через scheduled-task рельсу
- `takeout-arrival-watch` · 2026-06-28 · Daily watch (to ~June 26) for Anton's CLEAN Takeout exports (Chrome + My Activity) delivered as download LINKS to email 
- `vibe-teach-daily` · 2026-08-21 · Ежедневный пост обучающей серии «Claude Code для не-кодеров» (тизер TG + средний FB)
- `weekly-brain-audio-digest` · 2026-07-22 · Weekly NotebookLM audio digest of Anton's Second Brain (Sun 05:30 Lisbon)
- `wisdom-distill-weekly` · 2026-07-22 · Мудрость недели: 3-5 durable-уроков из собственных слов Антона за 7 дней → 03-Insights + анонс в TG чат 03
- `zz-hub-store-load-canary` · 2026-08-22 · Канарейка переноса git-s7-fast на хаб: доказать, что запись в scheduled-tasks.json подхвачена приложением после рестарта

## C. Были выключены намеренно (117)

- `alpha-to-tg` · 2026-07-04 · [WEEKLY Mon 04:20 — 2026-07-04 Anton, не читал ежедневно]. Еженедельно — НОВАЯ намайненная альфа (волт + голос) в TG-пап
- `auto-hub-260805-dr-runner-1858` · 2026-08-05 · AUTO-hub-260805: разогнать DR26-08-05-HUB-01-1858 веером из 6 рельс и собрать отчёты
- `auto-hub-260805-dr-runner-2158` · 2026-08-05 · AUTO-hub-260805: разогнать DR26-08-05-HUB-02-2156 (FB Graph API для личного профиля) веером из 6 рельс и собрать отчёты
- `auto-hub-260805-stale-task-digest` · 2026-08-05 · AUTO-hub-260805: экран задач врёт про состояние — done-карточка показана как P0 blocked, найти корень и посчитать класс
- `auto-hub-260806-alpha-credit-close-delta` · 2026-08-06 · AUTO — кредиты авторам советов: разобрать 16 без вердикта, отдать 2 долга «спасибо», доказать что фидеры пишут в реестр.
- `auto-hub-260806-apply-verify-status-split` · 2026-08-06 · AUTO-hub-260806-apply-verify-status-split — починка корня класса «доставка ≠ применение»: у применения появляется собств
- `auto-hub-260806-codex-mirror-v410` · 2026-08-06 · Пересобрать зеркало канона Codex с v2.14.1 до v4.10.0 (кап уже поднят до 48 КиБ)
- `auto-hub-260806-crm-engine-hub-deploy` · 2026-08-06 · CRM-сенсоры: ночные рутины на хабе (закрыть Connect-провал 27.06)
- `auto-hub-260806-deepak-robomyne-vc-intros` · 2026-08-06 · Deepak/Robomyne: blurb+фото+one-pager под VC/angel-интро
- `auto-hub-260806-dr-fanout-triz-5why` · 2026-08-06 · Веер ДР по двум заказам: ТРИЗ (DR26-08-06-HUB-01-1055) и 5 Why по серии (DR26-08-06-HUB-02-1055)
- `auto-hub-260806-dr-registry-v3-apply-fold` · 2026-08-06 · dr_registry v3: принять пакет с HP17, применить, fold, раскатать
- `auto-hub-260806-dr-runner` · 2026-08-06 · AUTO-hub-260806-dr-runner: разнести DR26-08-06-HUB-03-1725 по 6 рельсам и забрать отчёты
- `auto-hub-260806-funnel-feeder` · 2026-08-06 · Корень «0 публикаций при 290 активных»: назначить исполнителя-рутину на стадию new→seeded→публикация
- `auto-hub-260806-github-threads-silence` · 2026-08-06 · Закрыть молчание в шести живых GitHub-тредах с внешними инженерами (замер 06.08)
- `auto-hub-260806-hub-pending-deploy-unpack` · 2026-08-06 · Хаб: распаковать непринятые посылки deploy-манифеста
- `auto-hub-260806-interactive-tasks-away-mode` · 2026-08-06 · 35 задач планировщика Interactive-only: сторожа молчат при выключенном хабе
- `auto-hub-260806-mistral-community-question` · 2026-08-06 · AUTO — вопрос комьюнити «кто пользовался Mistral?» (ДР / кодинг / OpenRouter vs подписка) + сбор ответов в решение по на
- `auto-hub-260806-model-frontmatter-canary` · 2026-08-06 · Канарейка: слушается ли поле model во frontmatter рутины (замер, не задача)
- `auto-hub-260806-model-frontmatter-canary2` · 2026-08-06 · Канарейка-2: во frontmatter ВПИСАНО model sonnet -- слушается ли рантайм
- `auto-hub-260806-orphan-engine-detector` · 2026-08-06 · КОРЕНЬ КЛАССА «стадия без хозяина»: наш гейт работает по самодекларации и не видит незаписанную стадию. Построить детект
- `auto-hub-260806-record-application-video` · 2026-08-06 · Видео-визитка Anthropic (ElevenLabs + HeyGen), сценарий готов
- `auto-hub-260806-routine-session-rights` · 2026-08-06 · Боль дня: права рутинной сессии, самолечение рутин без аппрувов, запуск полноценной сессии с телефона
- `auto-hub-260806-shared-brain-post-contrib` · 2026-08-06 · AUTO — «общий мозг для команды»: ресёрч похожих проектов, контриб нашего ноу-хау, качественный пост-README. Из голосовой
- `auto-hub-260806-voice-runner` · 2026-08-06 · P0: рельса «голосовая → сессия» ни разу не отработала. Разобрать первую партию неразложенных голосовых.
- `auto-hub-260809-github-outbound-catchup` · 2026-08-09 · Догон субботней полосы мемо 80/20: GitHub-треды + consumer-hunt + X-тизеры + ACK-долг шины top-20
- `auto-hub-260809-root1-reward-loop` · 2026-08-09 · Корень №1: наружный выхлоп без владельца и счётчика долга — вылечить reward-петлю
- `auto-hub-260809-root2-death-ritual` · 2026-08-09 · Корень №2: детали рождаются, но не умирают — построить ритуал смерти по счётчикам
- `auto-hub-260809-root3-fleet-multiplier` · 2026-08-09 · Корень №3: конвейер доставки флота сам в долгах (179 посылок + 239 долгов) и плодит ремонт
- `auto-hub-260809-root4-memory-diet` · 2026-08-09 · Корень №4: MEMORY.md 29КБ > обреза 25КБ — амнезия каждую сессию, диета немедленно
- `auto-hub-260809-secondop-context-inline` · 2026-08-09 · Починка корня panel-bridge: secondop.py передаёт --context как путь, рельсы ревьюируют строку пути вместо работы
- `auto-hub-260809-sendmessage-rail-blindspot` · 2026-08-09 · Разбор бага: живая рабочая сессия невидима для рельса send_message и list_sessions
- `auto-hub-260810-approval-pusher` · 2026-08-10 · AUTO — сторож-проталкиватель зависших аппрувов: каждые 15 мин проверять сессии и проталкивать их, из голосовой hub:5170
- `auto-hub-260810-arxiv-ping` · 2026-08-10 · Построить ежедневный пинг arXiv по тикету AH-201695 (приказ Антона, дом = хаб)
- `auto-hub-260810-call-booking-skill` · 2026-08-10 · AUTO — скилл букинга звонков: Calendly-пинг «забукал?», детект даты, напоминания за сутки и час, из голосовой hub:5225
- `auto-hub-260810-connect-audit` · 2026-08-10 · AUTO — аудит правила Connect: найти сессии/рутины, чьим выходом никто не пользуется, из голосовой hub:5161
- `auto-hub-260810-connector-kit-announce` · 2026-08-10 · Разнести анонс telegram-mcp-kit: посты с описанием + ссылка + инструкции (приказ Антона 09.08)
- `auto-hub-260810-console-hider-spare-user-terminal` · 2026-08-10 · Починить console_hider.ps1: не прятать консоль, открытую Антоном руками (проверка родителя процесса)
- `auto-hub-260810-dr-nonprofit-fanout` · 2026-08-10 · Веер DR26-08-10-HUB-01-1449 (платформы регистрации 501c3) по внешним LLM + сбор отчётов
- `auto-hub-260810-dr-runner-accel` · 2026-08-10 · AUTO-hub-260810-dr-runner-accel: разнести два ДР (акселераторы + фандрейз-упаковка) по веером внешних LLM и забрать отчё
- `auto-hub-260810-kids-money-apps` · 2026-08-10 · AUTO — ресёрч: приложения для обучения детей деньгам (iPad/iPhone), из голосовой hub:5221 (Музей денег, Будапешт)
- `auto-hub-260810-kit-approval-gate` · 2026-08-10 · Кит №5: agent-approval-gate — human-in-the-loop апрув агента через Telegram (Антон «+» 10.08)
- `auto-hub-260810-kit-fleet-deploy` · 2026-08-10 · Кит №6: fleet-deploy — раскатка фиксов на N машин с verify-читающим-факт и канарейкой (Антон «+» 10.08)
- `auto-hub-260810-kit-llm-spend-audit` · 2026-08-10 · Кит №8: llm-spend-audit — кто жрёт контекст и утилизация оплаченных подписок (Антон «+» 10.08)
- `auto-hub-260810-kit-mcp-daemon-diet` · 2026-08-10 · Кит №3: mcp-daemon-diet — один MCP-демон на машину вместо копии на сессию (приказ Антона 10.08 «+»)
- `auto-hub-260810-kit-oss-publish` · 2026-08-10 · Кит №4: oss-publish — санитайзер «данные понарошку» + final_gate, конвейер открытия внутрянки (Антон «+» 10.08)
- `auto-hub-260810-kit-secondop-panel` · 2026-08-10 · Кит №7: secondop-panel — панель внешних ломателей (мульти-вендор ревью) на каждый билд (Антон «+» 10.08)
- `auto-hub-260810-measure-review-registry` · 2026-08-11 · AUTO — реестр «замерить через месяц»: отложенные замеры/ревью не забываются, из голосовой hub:5175
- `auto-hub-260810-natasha-parcel` · 2026-08-10 · Применить посылку tg-permalink-not-crm-20260810 от узла Наташи (apply+verify+ACK)
- `auto-hub-260810-routine-selfheal` · 2026-08-10 · AUTO — механизм «рутина нашла ошибку → сама поднимает сессию-починку корня без аппрувов», из голосовой hub:5164
- `auto-hub-260810-tests-external-llms` · 2026-08-11 · AUTO — покрытие тестами силами простаивающих подписок (Codex/Grok/Gemini) + документация → скилл, из голосовой hub:5217
- `auto-hub-260810-whatsapp-mcp-kit` · 2026-08-10 · Собрать и опубликовать whatsapp-mcp-kit на GitHub (второй коннектор серии, приказ Антона 09.08)
- `auto-hub-260811-abc-experiment-prep` · 2026-08-11 · A/B/C-эксперимент харнес-фреймворков: подготовка — выбор 3 CRM-задач, characterization-тесты, изоляция рукавов
- `auto-hub-260811-audit-rutin-perenos-na-hab` · 2026-08-11 · AUTO — аудит всех рутин флота, перенос с ноутов/Mac на хаб, разбор Маяка с approve, маршрутизация моделей; из голосовой 
- `auto-hub-260811-bible-chrome-passwords-rule` · 2026-08-11 · Приём правила в Библию: пароли всегда сохранены в Chrome — ВСЕГДА использовать их, логиниться самому
- `auto-hub-260811-c68bb7-stop-confirm` · 2026-08-11 · Подтвердить на хабе, что посылка контента c68bb7 НЕ уйдёт в публикацию по истечении окна апрува (стоп Наташи, silence=ST
- `auto-hub-260811-repair-dead-scheduled-task` · 2026-08-11 · Класс dead-scheduled-task стал системным (3-я поломка) — сессия починки
- `auto-hub-260811-task-asks-to-02-undelivered-2026-08-06` · 2026-08-11 · 559 недоставленных сообщений в чат 02 с 21.07 — Антон не видит аски с узла Наташи
- `auto-hub-260811-task-scripts-31-deleted-files-2026-08` · 2026-08-11 · 31 файл вынут из ~/.claude/scripts 31.07 — 6 задач и 2 хука зовут пустоту
- `auto-hub-260811-watchdog-v2-hung` · 2026-08-11 · Watchdog v2: ветка HUNG (зависший Claude Desktop) + ревизия headless-рестарта; обновить OSS и посылку флоту
- `auto-hub-260812-cap5-asks` · 2026-08-12 · Внедрить кап-5 открытых асков к Антону в существующий approval.py (+auto-expiry 14д)
- `auto-hub-260812-doc-alpha-reenable` · 2026-08-12 · Вернуть doc-alpha-weekly в строй: сам чинит — молчит; руки Антона — одна weekly-карточка
- `auto-hub-260812-freeze-cf-coach` · 2026-08-12 · Заморозить очередь content-factory (1688) на дашбордах + coach-morning в pull-режим /coach
- `auto-hub-260812-mayak-cron-key` · 2026-08-12 · КОРЕНЬ: вшить claude_headless.env в cron Маяка, чтобы ночные роботы получали OAuth-токен
- `auto-hub-260812-mission-pulse-dossier` · 2026-08-12 · Досье последних 3 отчётов mission-pulse для решения Антона о переделке на дешёвый вариант
- `auto-hub-260812-repair-dead-scheduled-task` · 2026-08-19 · Класс dead-scheduled-task стал системным (9-я поломка) — сессия починки
- `auto-hub-260812-watchdog-issue-after-pass` · 2026-08-11 · После ночного PASS живого kill-теста сторожа завести upstream issue с уликами (мандат Антона 11.08 вечером)
- `auto-hub-260817-instrument-lies-5why` · 2026-08-17 · 5 почему по серии «прибор врёт» (3-й датированный случай, §5.10) — корень класса и починка
- `auto-hub-260817-nat-daily-lanes` · 2026-08-17 · Поднять полосы-потребители карточки дня по заказу узла Натальи (TASK #1847400/01)
- `auto-hub-260817-rails-dashboard` · 2026-08-17 · Построить и опубликовать дашборд карты LLM-рельс флота + вшить rail_glm по приходу ключа
- `auto-hub-260817-rc-canary` · 2026-08-17 · Канарейка Remote Control: живая одноразовая сессия для Антона, тест видимости и работы с телефона
- `auto-hub-260818-anton-phone-live` · 2026-08-18 · Свежая сессия хаба для Антона: работа с телефона через Remote Control
- `auto-hub-260818-rc-anton-live` · 2026-08-18 · RC-сессия для управления Антоном с телефона (страховка к ресюмнутой Anton-2)
- `auto-hub-260818-rc-cockpit-anton` · 2026-08-18 · RC-кокпит Антона 18.08: живая сессия, видимая с телефона, продолжение очереди сессии Anton-2
- `auto-hub-260819-chip-debt-triage-autolaunch` · 2026-08-19 · Разбор 110 ненажатых чипов + автозапуск живых
- `auto-hub-260819-daniel-ospina-vhodyashchiy-kontakt` · 2026-08-19 · Daniel Ospina (@_Daniel_Ospina) — живой входящий, строит Tortoise (graph-memory для агентов)
- `auto-hub-260819-github-2fa-lab-account` · 2026-08-19 · Включить 2FA на GitHub-аккаунте Palo-Alto-AI-Research-Lab (дедлайн GitHub: 13.08.2026)
- `auto-hub-260819-hackernoon-hacker-news-content-strateg` · 2026-08-19 · HackerNoon / Hacker News — контент-стратегия (голосовая задача №54 от 28.07)
- `auto-hub-260819-kirill-gruppa-robot-s-haba` · 2026-08-19 · AUTO — лид Кирилл: найти/поднять группу, перевести общение робота с Маяка на хаб, вести проактивно. Из голосовой hub:549
- `auto-hub-260819-monosnap-upakovka-veernyy-dr` · 2026-08-19 · AUTO — наша сторона договорённостей со звонка 19.08 с Кириллом Симаковым: упаковка Monosnap под Долину + веерный DR (наш
- `auto-hub-260819-n8n-event-rail-build` · 2026-08-19 · СТРОЙКА: событийная рельса лид-тредов — n8n MTProto детектор (Маяк/облако) → пинг хаба → подъём/пробуждение сессии-ответ
- `auto-hub-260819-onboard-dima-petya-starter-kit` · 2026-08-19 · Довести Диму и Петю до РАБОТАЮЩЕГО сетапа (не до «отдали ссылку»)
- `auto-hub-260819-post-velosiped-chehiya-nelzya` · 2026-08-19 · AUTO — контент из голосовой про чешский веломастер: «почему в одних странах делают, а в других „невозможно“». Голос Анто
- `auto-hub-260819-sessii-vneshnih-pirov-strogo-na-habe` · 2026-08-19 · AUTO — принять правило «сессии с внешними лидами/пирами запускаются строго на хабе» во все дома + разрулить конфликт с §
- `auto-hub-260819-sessiya-umiraet-s-noutbukom-pribor` · 2026-08-19 · AUTO — «нет сессии = нет волшебства»: зафиксировать механику смерти сессии, прибор видимости живых сессий внешних пиров,
- `auto-hub-260819-skills-nevidimy-dlya-karty-pokrytiya` · 2026-08-19 · Скиллы невидимы для карты покрытия — 127 деталей вне гейта §5.8
- `auto-hub-260819-sync-conflict-audit` · 2026-08-19 · Разбор класса «sync-conflict молча съедает содержимое»: аудит всех конфликтных копий волта, возврат потерянного, опознан
- `coach-morning` · 2026-08-12 · "[PAUSED by Anton 2026-08-12 — pull-режим /coach по запросу] [WEEKLY Mon 07-34 — cron applied 2026-07-03 Anton, token-sa
- `content-factory-daily` · 2026-08-12 · "[PAUSED by Anton 2026-08-12 — НЕ ВКЛЮЧАТЬ, канал @ClawRus остановлен, очередь заморожена] Ночью (23:40 Lisbon, ночное о
- `cu-grant-cold-session-probe` · 2026-07-29 · Одноразовый холодный замер: подхватывает ли новая сессия доступ к экрану по инструкции хука
- `devlog-collect-nightly` · 2026-07-14 · ⏸️ SUPERSEDED 14.07 by Windows Task Scheduler "Devlog Collect Nightly" (00:50, pythonw, 0 tokens, no Claude session, no 
- `doc-alpha-weekly` · 2026-08-12 · Weekly: mine alpha (new features applicable to us) from all key tool docs/changelogs; self-fix silently, P0-safety insta
- `fb-watch-daily` · 2026-08-06 · ⛔ ОСТАНОВЛЕНА 06.08.2026 18:20 приказом Антона: «Полностью останови задачи по постингу тизеров в этот чат без ок или апп
- `mission-pulse-weekly` · 2026-07-27 · Еженедельный Mission-Pulse: статус миссии №2 + табло-дельта + 1-3 аска каждому (Антон/Наташа/Руслана), draft-first, отпр
- `ph-launch-day-consensus` · 2026-07-29 · SLOT-TEST: проверка переиспользования отработавшего слота вместо create (0 диалогов)
- `pilot-post-season-launch` · 2026-07-29 · AUTO-hub-260729-nightly-routines-visible: перевести ночные Windows-рутины на видимую рельсу
- `rc-cockpit-anton-daily` · 2026-08-21 · Ежедневная свежая кокпит-сессия для управления с телефона Антона (лечение класса «рестарт аппки + до-ключевые сессии»)
- `reddit-warmup-lead` · 2026-07-27 · [STOPPED 2026-07-27 Anton] Reddit-лейн закрыт (баны 20.07). Рутина выключена в scheduled-tasks MCP — это и есть та рельс
- `sess-alpha-pipeline-calls` · 2026-07-29 · п.38+48 Альфа-конвейер: звонки и инженерные каналы с доказательством
- `sess-bible-help-useful` · 2026-07-29 · Библия: помогаем только полезным (циничный капер)
- `sess-bikes-usa-portugal` · 2026-07-29 · п.47 Велосипеды: США → перегрузочный склад → Португалия, сквозной расчёт
- `sess-chrome-passwords-store` · 2026-08-11 · DR fanout DR26-08-11-HUB-01-1154: Superpowers vs OpenSpec vs Spec Kit (веер по внешним LLM)
- `sess-content-plan-v1` · 2026-07-29 · п.28+26 Контент-план v1 + робот дистрибуции + дневник FB/X в GitHub
- `sess-dogfooding-temperature` · 2026-07-29 · Гейты из hooks/ не доезжают до пиров — закрыть класс (chip_guard под ударом)
- `sess-fleet-health-red-bus` · 2026-07-29 · AUTO-hub-260729-fleet-rollout-session-gates: раскатать новые гейты сессий на весь флот
- `sess-github-visibility-dr` · 2026-07-29 · п.53+41 Заметность GitHub: собрать DR, замер, позиционирование
- `sess-lost-knowledge-screen-alpha` · 2026-07-29 · п.8+20 Потерянное знание: скрин-альфа hub:3807 + забрать ноу-хау
- `sess-output-freshness-peers` · 2026-07-29 · Хвосты ночи: output_freshness на пиры + ночная регрессия
- `sess-outreach-similar-builders` · 2026-07-29 · п.52 Аутрич к строящим похожее (доделать после обрыва на лимите)
- `sess-peer-personal-vault` · 2026-07-29 · AUTO-hub-260729-chip-debt-triage: триаж 107 ненажатых чипов
- `sess-phone-remote-control` · 2026-07-29 · п.11 Пульт с телефона: видеть / запускать / оценить ответ живой сессии
- `sess-public-repo-hygiene-dr` · 2026-07-29 · AUTO-hub-260729-deploy-parcels-apply: распаковать 4 висящие посылки deploy
- `sess-reply-antonkatkov` · 2026-07-29 · Долг: ответить Антону Каткову @*****katkov (ждёт 21 день)
- `sess-swarm-coordination` · 2026-07-29 · п.33+6 Координация роя: одна живая сессия, watchdog зависших
- `sess-writing-styles-voice` · 2026-07-29 · п.29+39 Стили письма до конца + голосовой слой (подкасты)
- `sessions-results-digest` · 2026-07-29 · Собрать результаты фоновых сессий 29.07 в один дашборд, который видно в приложении
- `show-hn-gate-verdict-0808` · 2026-08-06 · Разовый вердикт по гейту Show HN 11.08 (08.08 утро): замерить внешние ссылки + воспроизведения, дать честное «стреляем /
- `tg-calendar-agenda` · 2026-08-05 · ⏸️ STOPPED 2026-07-27 по слову Антона («пока не надо предупреждать про будущие эвенты из календаря»). Не включать без ег
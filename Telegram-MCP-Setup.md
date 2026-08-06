[все дашборды](index.html) · категория: Инфраструктура и рутины · [← Tasks-Audit-2026-07-04-to-07](Tasks-Audit-2026-07-04-to-07.html) · [Waiting-Sessions-MACANTON →](Waiting-Sessions-MACANTON.html)

---
title: "Telegram MCP — подключение к Claude (Windows)"
type: setup-guide
source: claude-code-research
authored_by: ai
origin: external
date: 2026-05-31
tags: [telegram, mcp, connector, claude-code, voice-gap, setup]
related: ["[[_Pokupki-MOC]]"]
---

# Telegram MCP под Windows — как подключить к Claude

**Зачем тебе именно это:** твои экспорты Telegram Desktop (HTML/JSON) **не содержат голосовых `.ogg`** — в чате «Покупки» так потеряно **9 418 голосовых** (это подтвердил дашборд). Bot API тут бесполезен: бот не читает старую историю личных чатов и не качает старую медиу. Нужен **MTProto / user-account** сервер, который умеет `download_media(chat_id, message_id, file_path)` — тогда Claude пройдёт по чату, найдёт каждое голосовое и скачает `.ogg` по `msg_id`, а дальше Whisper → обогащаем ледджеры по id (идемпотентно, через скилл `telegram-reimport`).

## TL;DR

Бери **#1 `chigwell/telegram-mcp`**: единственный, у кого есть и точный `download_media`, и встроенный **read-only режим**, и самый живой репозиторий (v3.1.13 от 27.05.2026, ~1.1k★). Чистый Python через `uv` — **никакого TDLib и нативной сборки** на Windows.

## Сравнение (3 варианта, все — user-account MTProto)

| | #1 chigwell/telegram-mcp ⭐ | #2 dryeab/mcp-telegram | #3 overpod/mcp-telegram |
|---|---|---|---|
| Движок | Telethon (Python) | Telethon (Python) | GramJS (Node) |
| Скачать медиа по msg_id | ✅ `download_media` + `get_media_info` | ✅ `media_download` | ✅ `telegram-download-media` |
| Runtime / Windows | `uv`, без нативных деп. | PyPI `uv tool install`, `.exe` в PATH | `npx` / готовый `.exe` |
| Read-only режим | ✅ `TELEGRAM_EXPOSED_TOOLS=read-only` | ❌ нет | ❌ нет |
| Авторизация | session **string** (QR/телефон) | session **файл** (`login`) | QR «Link Desktop Device» |
| Поддержка | **v3.1.13 · 27.05.2026 · ~1.1k★** | v0.1.11 · 15.04.2025 · ~247★ | v1.36.4 · 28.05.2026 · ~11★ |

> TDLib-серверов зрелых нет, и это к лучшему: TDLib на Windows = компиляция C++ / поиск `tdjson.dll`. Все три варианта этого избегают.

---

## Установка #1 chigwell/telegram-mcp (рекомендую), пошагово

### 1. Получить `api_id` / `api_hash`
1. Зайди на **https://my.telegram.org**, войди по номеру (код придёт **в приложение Telegram**).
2. **API development tools** → создать приложение (platform: Desktop).
3. Получишь числовой `api_id` и hex `api_hash`. **`api_hash` храни как пароль** — он идентифицирует приложение, не твой вход.

### 2. Поставить uv и сервер (PowerShell)
```powershell
# uv (Astral), если ещё нет:
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"

git clone https://github.com/chigwell/telegram-mcp.git C:\mcp\telegram-mcp
cd C:\mcp\telegram-mcp
uv sync

# одноразово сгенерировать session STRING (QR или телефон+код):
uv run session_string_generator.py        # интерактивно
# -> скопировать выведенную строку в конфиг ниже

# папка, КУДА можно качать медиа (см. gotcha про allowed-roots):
New-Item -ItemType Directory -Force C:\TG-Media | Out-Null
```

### 3. ⚠️ Главный gotcha — allowed-roots
Файловые инструменты (`download_media`, `send_file`, …) **по умолчанию выключены** ради безопасности. Чтобы `download_media` мог писать, нужно передать разрешённую папку **позиционным аргументом** `main.py` (НЕ через env). Это и есть тот шаг, без которого скачивание голосовых не заработает — папка `C:\TG-Media` в конце `args`.

### 4. Конфиг Claude Desktop
Файл `%APPDATA%\Claude\claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "telegram": {
      "command": "uv",
      "args": ["--directory", "C:\\mcp\\telegram-mcp", "run", "main.py", "C:\\TG-Media"],
      "env": {
        "TELEGRAM_API_ID": "YOUR_API_ID",
        "TELEGRAM_API_HASH": "YOUR_API_HASH",
        "TELEGRAM_SESSION_STRING": "YOUR_SESSION_STRING",
        "TELEGRAM_EXPOSED_TOOLS": "read-only"
      }
    }
  }
}
```

### Для Claude Code (CLI)
```powershell
claude mcp add telegram --scope user `
  --env TELEGRAM_API_ID=YOUR_API_ID `
  --env TELEGRAM_API_HASH=YOUR_API_HASH `
  --env TELEGRAM_SESSION_STRING=YOUR_SESSION_STRING `
  -- uv --directory C:\mcp\telegram-mcp run main.py C:\TG-Media
```
(всё после `--` — команда запуска; хвост `C:\TG-Media` = allowed root.)

> Нюанс read-only: `download_media` технически *пишет* файл. Если под `read-only` его не видно — сделай разовый bulk-проход скачивания с `read-only` **выключенным** (и заданным allowed root), потом верни `read-only` обратно для повседневной работы.

---

## Безопасность (важно)
- **User-account MCP = полный доступ к твоему Telegram**: читать все чаты и (если не ограничить) писать/править/удалять и менять настройки. Это и даёт нужную силу (старая медиа), и несёт риск.
- **Session string/файл = твой аккаунт без телефона и 2FA.** Не коммить в git, не вставляй в чаты; диск под BitLocker; ограничь права на `claude_desktop_config.json` (там строка лежит открытым текстом).
- **Отзыв:** Telegram → Settings → Devices/Active Sessions → terminate.
- **Держи read-only** для повседневного (только #1 умеет встроенно). Узкий allowed root (`C:\TG-Media`) — тоже защита: файловые инструменты не лезут по всему диску.
- **ToS:** userbot формально против правил; для личного чтения/скачивания баны редки, но не нулевые — **троттли** массовое скачивание 9.4k файлов (паузы), чтобы не словить flood-wait.

## Как это закрывает твой voice-gap
1. Подключаешь #1, `read-only` off на разовый проход, allowed root = `C:\TG-Media`.
2. Просишь Claude: пройти по чату «Покупки», через `get_media_info` найти все `voice`/`audio` сообщения, `download_media` по `msg_id` → `.ogg` в `C:\TG-Media`.
3. Whisper-транскрипция `.ogg` → обновляем ледджеры/посты **по `msg_id`** через скилл `telegram-reimport` (идемпотентно).
4. Возвращаешь `read-only` on.

## Запасной вариант
**#2 `dryeab/mcp-telegram`** — `uv tool install mcp-telegram`, ставит `.exe` в PATH, без клонирования; авторизация `mcp-telegram login`. Нет read-only — бери, если не нужен этот режим.

---
*Источники (проверены): github.com/chigwell/telegram-mcp · github.com/dryeab/mcp-telegram · github.com/overpod/mcp-telegram · github.com/sparfenyuk/mcp-telegram · my.telegram.org. Ресёрч: Claude Code, 2026-05-31.*

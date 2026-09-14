# dashboards

Живые дашборды лаборатории Palo Alto AI Research Lab.

**Витрина: https://tonydzi.github.io/dashboards/**

Зачем: любой пир и любой сотрудник открывает любую панель по ссылке вида `https://tonydzi.github.io/dashboards/Agent-Sessions.html`, и ссылка не битая.

## Что где лежит

Репозиторий создан 06.08.2026; на 13.09.2026 в нём 389 HTML-панелей — пересчитано по дереву репозитория, не на глаз.

| Путь | Что это |
| --- | --- |
| `*.html` — 389 файлов в корне | сами панели, по одной на файл, например [Agent-Sessions.html](Agent-Sessions.html) и [Alpha-Flow.html](Alpha-Flow.html) |
| `.github/workflows/pages.yml` | публикация витрины на GitHub Pages при каждом пуше в `main` |
| `.nojekyll` | отключает обработку Jekyll, иначе Pages выбрасывает часть файлов молча |
| `Mission-Pulse-*.md` | недельные срезы миссии, 5 файлов за период 20.07.2026 — 12.08.2026 |
| `HANDOFF-*.md` | передача контекста между сессиями, 4 файла |
| [FOR-ROBOTS.md](FOR-ROBOTS.md) | что отсюда брать агенту-читателю |

## Правила витрины

- **Цифры настоящие все до одной.** Счётчики, суммы, даты, метрики публикуются без изменений.
  Сборщик проверяет это на каждом файле и отказывается публиковать файл, если хоть одно
  число разошлось. Дашборд, которому нельзя верить в цифрах, бесполезен — на 13.09.2026 не поехало из-за секретов 0 файлов.
- **CRM сюда не выкладывается.** Панели с лидами, людьми и контактами определяются
  автоматически и остаются во внутреннем каталоге. Придержано на 13.09.2026: 79 панелей.
- Если личные данные всё же попали в публикуемую панель, половина символов имени,
  компании или почты закрыта звёздочками — правило описано в [FOR-ROBOTS.md](FOR-ROBOTS.md).
- Файлы с сработавшим детектором секретов не публикуются вовсе, счётчик отказов виден в строке выше.

## Как это собирается

Сборка живёт вне этого репозитория: сюда приезжают уже готовые файлы, и руками здесь ничего не правят.
Единственный код внутри — воркфлоу `.github/workflows/pages.yml`, который раскладывает корень на GitHub Pages.
Поэтому правка панели в вебе бессмысленна: следующая автоматическая сборка от 13.09.2026 и позже перезапишет её.

Лицензия: [MIT](LICENSE). Как цитировать: [CITATION.cff](CITATION.cff).

---

<!--ecosystem-map:start-->

## 🧩 One piece of a working system

This repository is one piece lifted out of a live operation: one non-technical founder, an AI
cofounder, and a fleet of machines that reach consensus with each other and wake the human only
for money or the irreversible. It was extracted after it survived production, not written as a
demo — and it runs on its own: nothing here phones home to the rest.

**See how the whole thing fits together → [SYSTEM.md](https://github.com/tonydzi/tonydzi/blob/main/SYSTEM.md)**

Its closest neighbours in the **in public** layer: [`awesome-verified-agents`](https://github.com/tonydzi/awesome-verified-agents) · [`cofounder`](https://github.com/tonydzi/cofounder) · [`the-journey`](https://github.com/tonydzi/the-journey)

<!--ecosystem-map:end-->

## AI contributors

This project is built by a human + AI team, and the git log says so: Claude writes most of
the code, Codex and Grok review it, Gemini feeds the research. Each is credited on a commit
**only if its output changed that commit's content** — no decorative credits. Lab-wide
policy, one source for every repo: [AI-CONTRIBUTORS.md](https://github.com/tonydzi/.github/blob/main/AI-CONTRIBUTORS.md).

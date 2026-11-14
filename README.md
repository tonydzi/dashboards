# dashboards

A public gallery of live status pages (dashboards) from Palo Alto AI Research Lab: plain web pages that show real numbers from our AI operation.

**Who it's for:** anyone who wants to see how a multi-agent AI operation looks in numbers, and our own team members who open a panel by link.
**What you get:** about 400 self-contained web pages with real figures. Customer and contact data is never published.

## Quick start
1. Open the gallery: https://tonydzi.github.io/dashboards/
2. Click any panel. Each one is a single web page that needs no login.
3. To keep a copy, clone the repo and open any `.html` file in a browser.

**Done when:** the gallery loads and a panel you click opens with charts or tables.

> Want an AI agent to do it for you? Paste this to Claude Code / Codex / Cursor:
> "Read the 'For AI agents' section of https://github.com/tonydzi/dashboards and set it up for me."

## For AI agents

### Preconditions
- Nothing to install and no code to run. This repo is a published output of an automated build, not a source of truth.
- Any browser, or `git` to clone. No accounts or keys.
- Ask the human: which panel or topic they want, since there are hundreds. File names describe the topic (for example `Brain-Health.html`).

### Use
```bash
git clone https://github.com/tonydzi/dashboards
cd dashboards
```
Open a file such as `index.html` or any `<Name>.html` in a browser, or read the live version at https://tonydzi.github.io/dashboards/. To search by topic, list the `.html` file names (`ls *.html`, PowerShell: `Get-ChildItem *.html`) and read the matching page.

### Configure
Nothing to configure. Pages are generated elsewhere and published here as they are; do not hand-edit them.

### Verify
Same on Windows, macOS and Linux (run the second line inside the cloned folder):
```bash
python -c "import urllib.request as u; print(u.urlopen('https://tonydzi.github.io/dashboards/').status)"
python -c "import glob; print(len(glob.glob('*.html')))"
```
Expected: `200`, then a number of HTML files (396 when checked on 2026-11-14, including `index.html`; the Russian text below says 403 panels because that number is stamped at build time, so a difference of a few is normal). A count of 0 means you are not inside the clone. Run here: the 200 matched; the file count matched 396.

### Uninstall / rollback
Delete the cloned folder. Nothing else was changed.

### Rules for the agent
- Treat the numbers as a snapshot dated by each page, not as live truth; the underlying systems are not in this repo.
- This repo is a published surface and is not meant to be edited by hand; do not push changes here.
- Do not try to recover hidden or masked data (CRM, contacts, names with asterisks). It is withheld on purpose.
- Do not copy real figures into your own reports without naming the page and its date.

## Details

Живые дашборды лаборатории Palo Alto AI Research Lab.

**Витрина: https://tonydzi.github.io/dashboards/**

Зачем: любой пир и любой сотрудник открывает любую панель по ссылке, и ссылка не битая.

## Правила витрины

- **Цифры настоящие все до одной.** Счётчики, суммы, даты, метрики публикуются без изменений.
  Сборщик проверяет это на каждом файле и отказывается публиковать файл, если хоть одно
  число разошлось. Дашборд, которому нельзя верить в цифрах, бесполезен.
- **CRM сюда не выкладывается.** Панели с лидами, людьми и контактами определяются
  автоматически и остаются во внутреннем каталоге. Придержано сейчас: 68.
- Если личные данные всё же попали в публикуемую панель, половина символов имени,
  компании или почты закрыта звёздочками.
- Файлы с сработавшим детектором секретов не публикуются вовсе.

Собирается автоматически, руками здесь ничего не правят.
Опубликовано панелей: 403. Не поехало из-за секретов: 0.

---

<!--ecosystem-map:start-->

## 🧩 One piece of a working system

This repository is one piece lifted out of a live operation: one engineer running a fleet of
machines, built with Claude as implementation collaborator; the machines reach consensus with
each other and wake the human only for money or the irreversible. It was extracted after it
survived production, not written as a demo — and it runs on its own: nothing here phones home
to the rest.

**See how the whole thing fits together → [SYSTEM.md](https://github.com/tonydzi/tonydzi/blob/main/SYSTEM.md)**

Its closest neighbours in the **in public** layer: [`awesome-verified-agents`](https://github.com/tonydzi/awesome-verified-agents) · [`cofounder`](https://github.com/tonydzi/cofounder) · [`agent-control-plane-casebook`](https://github.com/tonydzi/agent-control-plane-casebook)

<!--ecosystem-map:end-->

## AI contributors

This project is built by a human + AI team, and the git log says so: Claude writes most of
the code, Codex and Grok review it, Gemini feeds the research. Each is credited on a commit
**only if its output changed that commit's content** — no decorative credits. Lab-wide
policy, one source for every repo: [AI-CONTRIBUTORS.md](https://github.com/tonydzi/.github/blob/main/AI-CONTRIBUTORS.md).

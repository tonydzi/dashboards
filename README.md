# dashboards

Живые дашборды лаборатории Palo Alto AI Research Lab.

**Витрина: https://palo-alto-ai-research-lab.github.io/dashboards/**

Зачем: любой пир и любой сотрудник открывает любую панель по ссылке, и ссылка не битая.

## Правила витрины

- **Цифры настоящие все до одной.** Счётчики, суммы, даты, метрики публикуются без изменений.
  Сборщик проверяет это на каждом файле и отказывается публиковать файл, если хоть одно
  число разошлось. Дашборд, которому нельзя верить в цифрах, бесполезен.
- **CRM сюда не выкладывается.** Панели с лидами, людьми и контактами определяются
  автоматически и остаются во внутреннем каталоге. Придержано сейчас: 52.
- Если личные данные всё же попали в публикуемую панель, половина символов имени,
  компании или почты закрыта звёздочками.
- Файлы с сработавшим детектором секретов не публикуются вовсе.

Собирается автоматически, руками здесь ничего не правят.
Опубликовано панелей: 218. Не поехало из-за секретов: 0.

---

<!--ecosystem-map:start-->

## 🧩 One piece of a working system

This repository is one piece lifted out of a live operation: one non-technical founder, an AI
cofounder, and a fleet of machines that reach consensus with each other and wake the human only
for money or the irreversible. It was extracted after it survived production, not written as a
demo — and it runs on its own: nothing here phones home to the rest.

**See how the whole thing fits together → [SYSTEM.md](https://github.com/Palo-Alto-AI-Research-Lab/Palo-Alto-AI-Research-Lab/blob/main/SYSTEM.md)**

Its closest neighbours in the **in public** layer: [`the-journey`](https://github.com/Palo-Alto-AI-Research-Lab/the-journey) · [`clawrush`](https://github.com/Palo-Alto-AI-Research-Lab/clawrush) · [`awesome-verified-agents`](https://github.com/Palo-Alto-AI-Research-Lab/awesome-verified-agents)

<!--ecosystem-map:end-->

## AI contributors

This project is built by a human + AI team, and the git log says so: Claude writes most of
the code, Codex and Grok review it, Gemini feeds the research. Each is credited on a commit
**only if its output changed that commit's content** — no decorative credits. Lab-wide
policy, one source for every repo: [AI-CONTRIBUTORS.md](https://github.com/Palo-Alto-AI-Research-Lab/.github/blob/main/AI-CONTRIBUTORS.md).

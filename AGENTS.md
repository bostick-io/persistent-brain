# AGENTS.md

Entry point for any AI assistant working on ClockPoint. Read this first.

## Read order

1. `brain/architecture.md` for what the app is and how the pieces fit.
2. `brain/conventions.md` for naming, status values, and scope rules.
3. The newest file in `brain/timeline/` for recent changes. Read newest first and stop
   once you have enough recent context. You do not need the whole history every time.
4. `brain/cheatsheet.md` only when you need a reused query or snippet.

## Rules

- Pull only what the current task needs. Do not load the entire repo into context by
  default. That is the whole point of keeping this small and structured.
- Ground answers in what is written here. If a detail is not in the brain, say so
  rather than guessing at architecture.
- When something changes during a session (a new field, a fixed bug, a decision),
  append a dated entry to `brain/timeline/`. Keep the stable files stable.

## What not to touch

- Secrets never live here. API keys sit in ServiceNow system properties, never in
  source control.
- Real employee data and sys_ids stay out of this repo.

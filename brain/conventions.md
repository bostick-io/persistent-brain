# Conventions

Rules the assistant should follow so it does not reintroduce old mistakes.

## Status values

- Completion state is read from `u_status === 'completed'`.
- `u_completed` is a legacy boolean that is not reliably maintained. Do not read it.

## Naming and scope

- Core tables currently live in Global scope with a `u_` prefix
  (`u_time_entry`, `u_wellness_log`, `u_break_log`, `u_shift_config`).
- The intended convention is scoped naming, `x_ptb_*`. Migrating the core tables off
  Global is planned but not done. Until then, expect the `u_` prefix on the four tables.
- The "Global" scope label on the update set does not mean cross-team contamination.
  Diagnostic checks confirmed the work is isolated despite the label.

## Secrets

- The Anthropic API key lives in a ServiceNow system property, never in code and never
  in this repo.

## Data the AI search box sees

- A curated slice only: names, recent ratings, shift report text, last 14 days. Roughly
  5 to 15 KB per query, not the full database. The system prompt forbids inventing data
  and requires grounding answers in the slice provided.

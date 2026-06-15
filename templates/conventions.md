# Conventions

Rules the assistant should follow so it does not reintroduce old mistakes.

## Status values

The canonical status field and its allowed values, plus any legacy field to avoid.

- Task state is read from `status`, one of `open`, `in_progress`, `done`.
- `is_complete` is a legacy boolean that is not reliably maintained. Do not read it.

## Naming and scope

How tables, fields, and files are named, and any rename or migration still in progress.

- Tables use snake_case singular nouns (`task`, `app_user`).
- Older tables used a `tbl_` prefix and are being renamed. Until that is done, expect both.

## Secrets

Where credentials live, so they never end up in code or in this repo.

- API keys live in environment variables, never in code and never in this repo.

## What leaves the system

What gets sent out on any external call, and the limits on it.

- The email digest sends only task titles and due dates, never full task descriptions.

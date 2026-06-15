# Cheatsheet

Patterns and gotchas reused often, so the assistant is not rederiving them each session.

## Aggregating across users

The standard way to sum or count across a table.

Example: count open tasks per user with one grouped query, rather than pulling every row
into the app and counting there.

## A reused query

The one or two queries you write constantly.

Example: open tasks for a user, ordered by due date, capped to a sensible limit.

## Common gotchas

The traps that have bitten before.

- Read state as `status === 'done'`, never the legacy `is_complete`.
- Data must load before the view renders, or the page shows undefined on first paint.

## Recovery

How to undo damage when something breaks.

- The database has nightly backups. Check the latest snapshot before rebuilding by hand.

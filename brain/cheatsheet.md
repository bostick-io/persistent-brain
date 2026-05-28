# Cheatsheet

Patterns and gotchas reused often, so the assistant is not rederiving them each session.

## Aggregating across the team

Use `GlideAggregate` for sums over a table, for example total break minutes per
employee in a window. Filter by employee, by date range, and by type, then `SUM` the
duration field. Avoid pulling every row into the client and summing there.

## Blocker theme detection

Collect blocker text from recent shift reports, normalize it (trim and lowercase, key
on the first chunk of the string), count occurrences, sort by count, and keep the top
several. That is what powers the aggregate blockers panel.

## Recent shift reports

Query `u_time_entry` for rows with a clock-out in the window and a submitted report,
order by clock-out time descending, and cap the result. Only keep rows that actually
have blockers or handoff text.

## Common gotchas

- Read completion as `u_status === 'completed'`, never the legacy `u_completed`.
- Server-side data must be assembled before the client binds to it. A missing
  client-side binding shows up as undefined data on load, which usually means the
  server block ran in the wrong place.
- The wellness popup refreshes on a 30-second poll, so a new pending row appears
  without a page reload.

## Recovery

- ServiceNow keeps widget version history. It has saved a bad template overwrite before.
  Check version history before rebuilding anything by hand.

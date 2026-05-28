# Architecture

The stable picture of what ClockPoint is. This changes rarely.

## One-line summary

ClockPoint is a ServiceNow application: four database tables, six widgets across two
portal pages, one scheduled job, and one external AI call. Employees clock in, get
nudged to take a movement break with a teammate every couple of hours, log a short
shift report when they clock out, and managers see all of it on a dashboard with a
plain-English AI search box on top.

## The four tables

Everything is a query against one or more of these.

- `u_time_entry` — the shift table. One row per shift, created on clock-in and updated
  on clock-out with hours, blockers, and handoff notes. Most things hang off this.
- `u_wellness_log` — the prompts table. One row each time the system asks an employee
  to take a movement break. Tracks status, a 1 to 5 feeling rating, and the assigned
  buddy.
- `u_break_log` — the breaks table. One row per break or lunch with start, end, total
  minutes, and break type.
- `u_shift_config` — the schedule table. Which group works which shift, expected start
  and end times, and how often wellness prompts fire. One row per shift type.

## The moving parts

- **Clock-in flow** writes a `u_time_entry` row and a pending `u_wellness_log` row. A
  popup widget polls every 30 seconds, sees the pending row, and shows itself.
- **Wellness prompt** is a scheduled job that runs every couple of hours. It checks a
  set of skip guards (on a break, shift nearly over, recently prompted, no buddy free)
  before pairing the employee with a buddy and creating a pending wellness log.
- **Manager dashboard** reads the tables directly on page load. No queue, no bus.
- **AI search box** sends a curated slice of recent data to Claude and returns a
  grounded plain-English answer. See `decisions.md` for why it works this way.

## Roles

- `x_ptb_manager` gates the manager dashboard. Clock-in is open to all employees.

# Decisions

Choices made on purpose, with the reasoning, so they do not get relitigated every week.

## Claude for the AI search box, not Now Assist (for now)

Now Assist is the right production answer. Claude was chosen to prove the capability
today on a developer instance. The architecture moves to Now Assist with a server-side
endpoint swap, so this is not a dead end.

## Curated 14-day slice, not the whole database

The AI search box sends only a small, relevant slice to the model. This keeps the cost
near half a cent per query, keeps the data exposure small, and keeps answers grounded.
Sending more would cost more and ground less.

## Dashboard reads tables directly

No event queue or message bus. The dashboard queries the four tables on page load. For
this scale it is simpler, cheaper, and easier to reason about than an event pipeline.

## Blocker text repetition in seed data is intentional

Demo seed data repeats certain blocker phrases on purpose, so the dashboard's aggregate
panel has a real pattern to detect and surface. It is a feature of the demo, not messy
data.

## Panel order reflects operational priority

On the manager dashboard, the blockers panel sits above the fold because "what is
blocking the team" is the first thing a manager needs. Layout follows priority.

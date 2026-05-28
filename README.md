# ClockPoint Context Brain

A small, versioned context layer for working on **ClockPoint**, a ServiceNow-native
workforce time-tracking and wellness app, with an AI coding assistant.

It exists to solve one boring, expensive problem: stateless AI.

Every new session, the assistant starts from zero. So every session I'd re-explain
the app before any real work could happen, which burned thousands of tokens on setup
alone and still produced generic answers when I forgot a detail.

This repo is the fix. Instead of retyping context, the stable knowledge lives here in
plain markdown, version-controlled, and the assistant reads it before it answers and
appends to it when something changes.

## The result

Curated context instead of a copy-pasted project dump dropped my setup tokens from
roughly **10,000 per session to about 2,500**, a ~75% cut, every session. The morning
ritual of catching the assistant up basically went away.

## How an agent uses this

1. Read `AGENTS.md` first. It says what to load and in what order.
2. Pull the stable facts from `brain/architecture.md` and `brain/conventions.md`.
3. Check the most recent file in `brain/timeline/` for what changed lately.
4. Use `brain/cheatsheet.md` for the patterns and snippets reused constantly.
5. After the session, append a new dated entry to `brain/timeline/`.

## Structure

```
brain/
  architecture.md     stable facts: what the app is, the tables, the moving parts
  conventions.md      naming rules, status values, scope notes
  decisions.md        choices made and why, so they don't get relitigated
  cheatsheet.md       reused queries, snippets, gotchas
  timeline/           dated log of what changed, newest read first
```

## Where this is headed

This is the hand-rolled version of an idea now showing up in production tooling like
GBrain, where a git repo of markdown is the source of truth, a database handles search,
and a background job keeps the brain fresh. Same principle, just scaled up. The roadmap
is to move this onto an automated memory layer so the read, write, and cleanup happen
without me babysitting it.

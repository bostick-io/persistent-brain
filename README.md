# persistent-brain

Persistent context for stateless AI coding agents. Plain markdown in git that the agent reads before each session and updates after.

Every new session, an AI coding assistant starts from zero. I kept re-explaining my project before any real work could happen, which burned thousands of tokens on setup alone and still produced generic answers whenever I left out a detail.

persistent-brain is the fix. The stable knowledge lives here in plain markdown, version-controlled. The agent reads it before it answers and appends to it when something changes. No database, no infrastructure. Just files in a repo.

## The result

Curated context instead of a copy-pasted project dump dropped my setup tokens from roughly 11,000 per session to about 3,000, a 73% cut, every session. The morning ritual of catching the assistant up basically went away, and I got back about 20 minutes a morning.

I built this while working on ClockPoint, a ServiceNow app, but nothing here is ServiceNow-specific. Point it at any project and the pattern holds.

## How an agent uses this

1. Read `AGENTS.md` first. It says what to load and in what order.
2. Pull the stable facts from `brain/architecture.md` and `brain/conventions.md`.
3. Check the most recent file in `brain/timeline/` for what changed lately.
4. Use `brain/cheatsheet.md` for the patterns and snippets reused constantly.
5. After the session, append a new dated entry to `brain/timeline/`.

## Structure

```
brain/
  architecture.md     stable facts: what the project is, its parts, how they connect
  conventions.md      naming rules, status values, scope notes
  decisions.md        choices made and why, so they don't get relitigated
  cheatsheet.md       reused queries, snippets, gotchas
  timeline/           dated log of what changed, newest read first
```

## Why markdown over a tool

A wave of heavier tools solves this with vector databases and MCP servers. Those scale further than this does. The tradeoff is setup and another moving part to maintain. persistent-brain is the opposite bet. It does less and runs anywhere git runs. You can read the whole thing yourself in a text editor, and for one developer on one project that's usually enough.

## Where this is headed

The same idea is showing up across a wave of agent-memory tools now, where a git repo of markdown is the source of truth, a database handles search, and a background job keeps the context fresh. Same principle, scaled up. My roadmap is to move this onto an automated memory layer so the read, write, and cleanup happen without me babysitting it.

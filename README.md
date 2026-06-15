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

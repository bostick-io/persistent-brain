# Architecture

The stable picture of what this project is. This changes rarely.

## One-line summary

One or two sentences a newcomer could read to understand the whole system at once.

Example: A small task-tracking web app. Two database tables, a REST API, and a single-page frontend. Users create tasks, assign them to each other, and mark them done.

## The tables

Everything is a query against one or more of these. One line each on what a row represents.

- `task` — one row per task. Created when a user adds it, updated as status and assignee change.
- `app_user` — one row per user. Holds name, email, and role.

## The moving parts

The flows that tie the tables together. Name each one and say what it reads and writes.

- **Create-task flow** writes a `task` row and notifies the assignee.
- **Daily digest** is a scheduled job that reads each user's open tasks and emails them the list.

## Roles

Who can see or do what.

- `admin` gates user management. Task creation is open to any signed-in user.

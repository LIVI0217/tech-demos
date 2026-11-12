# Agent rules

This is a sticky monorepo of self-contained tech demos. Work happens in pull requests on this repository. Never create a new repository.

## Where a demo lives

Each demo is `apps/<kebab-slug>/` and is fully self-contained. It has its own `package.json` and `bunfig.toml`. From that directory, `bun install && bun run dev` starts the app. There is no root `package.json` and no workspace.

Change only your own `apps/<slug>/` directory. Leave every other demo alone. Update `tracking/seen-bookmarks.json` only when the task tells you to.

## Plan first

Before scaffolding or installing, read `skills/project-planning/SKILL.md` and write the plan to `apps/<slug>/PLAN.md`. The plan is part of the demo. Do not start `bunx create-*` until that file exists.

## Build

- Use Bun.
- Start from an official scaffold: `bunx create-*`. Do not hand-write a project skeleton.
- Before any install, add `bunfig.toml` in the demo directory:

```toml
[install]
minimumReleaseAge = 259200
```

- UI uses the shadcn/ui minimalist preset. Initialize with `bunx shadcn@latest init` and add components only when a slice needs them.
- Use one opinionated framework, Next.js or TanStack Start, only when the demo needs it. A one-screen utility gets no application framework.

## Pull requests

A demo pull request contains that demo's `apps/<slug>/` directory and, only when the task says so, `tracking/seen-bookmarks.json`.

Every demo pull request must attach at least one screenshot and at least one video of the running app.

## Bookmark ledger

`tracking/seen-bookmarks.json` has four arrays: `proposed`, `approved`, `skipped`, and `built`. Each entry is:

```json
{ "id": "string", "title": "string", "url": "string", "date": "YYYY-MM-DD" }
```

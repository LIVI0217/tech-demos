# tech-demos

本仓库是一组各自独立的技术演示。每个演示位于 `apps/<slug>/`，进入该目录后执行 `bun install && bun run dev` 即可在本地运行。

Small, sticky monorepo of tech demos. Each demo is its own Bun project. There is no shared install at the repo root.

## Layout

| Path | What it is |
| --- | --- |
| `apps/<slug>/` | One demo. Own `package.json`, `bunfig.toml`, and `PLAN.md`. `<slug>` is kebab-case. |
| `skills/project-planning/` | Planning skill used before a demo is scaffolded. |
| `tracking/seen-bookmarks.json` | Bookmark ledger with `proposed`, `approved`, `skipped`, and `built`. An entry is `{ "id", "title", "url", "date" }`. |
| `AGENTS.md` | Rules for adding a demo. |

## Run a demo

```bash
cd apps/<slug>
bun install
bun run dev
```

Run those commands from the demo directory. Dependencies stay inside that demo.

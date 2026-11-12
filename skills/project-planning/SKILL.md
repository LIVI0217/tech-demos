---
name: project-planning
description: >-
  Plan a single-user Bun and shadcn/ui MVP before scaffolding. Use when
  starting a demo in apps/<slug>, writing apps/<slug>/PLAN.md, or choosing
  the stack, vertical slices, and what to defer.
---

# Plan a Bun MVP

Write `apps/<slug>/PLAN.md` before `bunx create-*` or `bun install`. The plan is the scope of the pull request. If the request already states the goal, record it and proceed. If it is ambiguous, pick the smallest single-user reading, write that assumption in the plan, and build that.

## Workflow

1. **Goal and boundary.** Write the goal as one sentence: who uses it, and what they can finish in one sitting. Draw the single-user MVP boundary around that sentence. One person, one local run, one happy path.

2. **Vertical slices.** Split the MVP into outcome-oriented slices. Each slice is something the user can see or do, in demo order, including the UI and behavior that make that outcome true. Do not split by layer.

3. **Prefer a library.** Before writing a utility, use a maintained library that already does it. Original code is for the behavior the demo exists to show.

4. **Official scaffold.** Start with `bunx create-*`. Do not copy a template by hand or invent a skeleton.

5. **Release-age gate, then install.** Create `bunfig.toml` in the demo directory before the first install:

   ```toml
   [install]
   minimumReleaseAge = 259200
   ```

   `259200` is three days in seconds. Then run `bun install`.

6. **Framework only when it helps.** Pick one, and say why in the stack section.
   - No application framework for a one-screen utility. A client scaffold such as `bunx create-vite` is enough.
   - Next.js when the demo needs file-based routing or server rendering.
   - TanStack Start when the demo needs a full-stack React app without Next.js.
   Do not add a second framework later to solve a local problem.

7. **shadcn/ui, on demand.** From the demo directory run `bunx shadcn@latest init` and select the minimalist preset. Add a component only when the current slice renders it (`bunx shadcn@latest add <component>`). Do not install the catalog up front.

8. **Organize by feature.** Colocate each slice's components, state, and helpers in one feature folder. Keep shared primitives few and boring.

9. **Tests for critical logic only.** Test pure rules the demo would be wrong without (parsing, scoring, a state transition). Skip component snapshots and framework tests.

10. **Hooks for formatting and fast checks only.** A format-on-commit hook is enough. Do not run the test suite or a full typecheck from the hook.

11. **Defer the rest.** Anything that does not change the one-sentence goal goes to deferred items. It does not ship as a TODO inside the MVP.

## Output shape

`apps/<slug>/PLAN.md` uses these sections:

### Goal

One sentence.

### MVP

What the single user can do when this demo is done, and an explicit **Out** list of what it will not do.

### Tasks

Ordered vertical slices. Each item names a user outcome, not a layer.

### Stack

One line per choice: the tool, then why it is the smallest thing that works.

### Deferred

Each leftover, with the reason it is outside this MVP.

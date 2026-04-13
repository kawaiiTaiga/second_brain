# Wiki Update Workflow

Use this workflow whenever a task changes project state, adds durable knowledge, or creates a new wiki page.

## Goal

Capture what future sessions would otherwise need explained again.

## File-Placement Rule

- `status.md` - Current state, next actions, and decisions.
- `map.md` - File layout, runtime locations, deployment shape, and operational structure.
- `skills/` - Repeatable ways an agent should work on the project.
- `knowledge/` - Durable facts, edge cases, and resolved quirks.
- `index.md` - Discovery layer for every page.
- `log.md` - Chronological milestone record.

## Workflow

1. Decide whether the outcome is state, structure, workflow, or durable knowledge.
2. Update the smallest page that should own that fact.
3. If no page cleanly owns it, create a new page in the right folder.
4. Add the new page to `wiki/index.md` with a one-line summary.
5. Append a short milestone to `wiki/log.md` if the work materially changed the project.

## Quality Bar

- Write pages so they make sense when read alone.
- Prefer exact file paths and artifact names when they are safe to publish.
- Do not leave important decisions only in commit messages.
- Keep root-level pattern docs separate from project-specific operating details.

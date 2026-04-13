# second-brain Repository Maintenance

Use this workflow when changing the structure or operating rules of the `second_brain` repository itself.

## Scope Rule

- `README.md` is the short public entry point.
- `LLM-Wiki.md` explains the pattern.
- `wiki/` is the live operating memory.

Do not move day-to-day project state back into root documents.

## Change Workflow

1. If the pattern changes, update `LLM-Wiki.md`.
2. If the live repository structure changes, update `wiki/projects/second-brain/map.md`.
3. If maintenance rules change, update `wiki/projects/second-brain/skills/` or `wiki/shared/skills/`.
4. Register every new page in `wiki/index.md`.
5. Add a milestone to `wiki/log.md` for changes that future sessions should notice quickly.

## Public Hygiene Rule

- Before pushing, review the diff for machine-specific paths, private URLs, and operational details that should not be public.
- If exact local paths are not essential, convert them to repository-relative references or neutral descriptions.

## Consistency Check

Before closing the task, confirm:
- the index includes the new pages,
- the log records the milestone,
- and the owning project page still reflects the current state.

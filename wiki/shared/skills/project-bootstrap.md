# Project Bootstrap

Use this workflow when adding a new project or nested project page to the wiki.

## New Project

Create:
- `wiki/projects/<project>/status.md`
- `wiki/projects/<project>/map.md`
- `wiki/projects/<project>/skills/README.md`
- `wiki/projects/<project>/knowledge/README.md`

Then:
1. Add the project entries to `wiki/index.md`.
2. Add a milestone to `wiki/log.md`.
3. Record repository or hosting facts in `knowledge/` if the project already exists elsewhere.

## New Child Project

Create the same four files under:
- `wiki/projects/<parent>/<child>/`

Then:
1. Update the parent project's `status.md` or `map.md` so the relationship is explicit.
2. Add the child project entries to `wiki/index.md`.
3. Log the addition in `wiki/log.md`.

## Naming Rule

- Use stable names that match the real project or repository.
- Prefer hyphenated or existing project names over temporary labels.
- Keep parent and child-project boundaries explicit when a brand, product, and codebase are different things.

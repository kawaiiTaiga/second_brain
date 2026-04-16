# LLM Wiki Templates

Use these templates as starting points. Adapt them to the repository instead of copying them mechanically.

If the user's projects are hierarchical, keep that hierarchy in both folders and index entries.

Keep `skills/` and `knowledge/` distinct:

- `skills/` is for instructions and working rules.
- `knowledge/` is for facts, locations, system behavior, and durable learnings.

Use the wiki as a layered navigation system:

- `wiki/index.md` is the first stop for a fresh LLM session.
- `status.md`, `skills/README.md`, and `knowledge/README.md` are local hubs.
- Leaf pages should be reached through those hubs, not discovered by luck.
- Keep the navigation depth shallow: root index -> project index -> local hub -> leaf.
- Do not over-engineer the structure if the current layout is already easy for an LLM to follow.

## `wiki/index.md`

```md
# Wiki Index

This index is the entry point for finding relevant context inside the wiki.

Read this file first, then jump to the smallest relevant project or subproject hub.

## Shared

- [shared/skills/README.md](./shared/skills/README.md) - Cross-project conventions and reusable workflows.
- [shared/knowledge/README.md](./shared/knowledge/README.md) - Cross-project knowledge and repeated lessons.

## Projects

### <project-name>

- [projects/<project-name>/status.md](./projects/<project-name>/status.md) - Current status and decision history.
- [projects/<project-name>/map.md](./projects/<project-name>/map.md) - Repository layout and key file roles.
- [projects/<project-name>/skills/README.md](./projects/<project-name>/skills/README.md) - Project-specific workflows.
- [projects/<project-name>/knowledge/README.md](./projects/<project-name>/knowledge/README.md) - Durable project knowledge.

### <project-name> / <subproject-name>

- [projects/<project-name>/subprojects/<subproject-name>/status.md](./projects/<project-name>/subprojects/<subproject-name>/status.md) - Subproject status and next actions.
- [projects/<project-name>/subprojects/<subproject-name>/map.md](./projects/<project-name>/subprojects/<subproject-name>/map.md) - Subproject structure and key files.
- [projects/<project-name>/subprojects/<subproject-name>/skills/README.md](./projects/<project-name>/subprojects/<subproject-name>/skills/README.md) - Subproject-specific workflows.
- [projects/<project-name>/subprojects/<subproject-name>/knowledge/README.md](./projects/<project-name>/subprojects/<subproject-name>/knowledge/README.md) - Durable subproject knowledge.
```

Keep the root index selective. Do not dump every deep note here once the wiki grows. Link to hubs and let the hubs fan out.

## `wiki/log.md`

```md
# Wiki Log

## [YYYY-MM-DD] <project-name> | <milestone>
- Short summary of what changed.
- Reference the relevant page if one was added or updated.
```

Use the log for sync milestones too, for example:

```md
## [YYYY-MM-DD] <project-name> | Synced wiki to GitHub
- Pushed latest wiki updates to `origin/main`.
- Confirmed repository metadata in `knowledge/repository-hosting.md`.
```

## `status.md`

```md
# <project-name> Status

## Summary

One paragraph describing what this project is and where it stands now.

## Current State

- What exists now
- What is working
- What is blocked or pending

## Next

- Next concrete action
- Next concrete action

## Decisions

- Important decision and why it was taken
- Important decision and why it was taken
```

## `map.md`

````md
# <project-name> Map

## Repository Layout

```text
/
  wiki/
  src/
  ...
```

## File Roles

- `path/to/file` - what it is for
- `path/to/file` - what it is for

## Notes

- Environment or deployment notes
- Search hints for future sessions
````

When a project has subprojects, add a `## Subprojects` section listing each child and its role.

## Nested Project Layout

````md
# <project-name> Map

## Repository Layout

```text
wiki/
  projects/
    <project-name>/
      status.md
      map.md
      subprojects/
        <subproject-name>/
          status.md
          map.md
          skills/
          knowledge/
```

## Subprojects

- `<subproject-name>` - one-line explanation of what it owns
````

## `skills/README.md`

```md
# <project-name> Skills

Use this folder for project-specific workflows that should guide future maintenance.

Initial rules:
- Keep durable process rules here.
- Add new pages to `wiki/index.md`.
- Append meaningful milestones to `wiki/log.md`.
- Keep Git and sync instructions here, not only in status notes.
- Point to the specific deeper workflow pages that a fresh session may need next.
```

## `knowledge/README.md`

```md
# <project-name> Knowledge

Use this folder for durable project-specific knowledge.

Planned topics:
- Vendor quirks
- Resolved edge cases
- Operational lessons
- Repository hosting and sync details
- Links to the important deep knowledge pages in this area
```

## `knowledge/repository-hosting.md`

```md
# Repository Hosting

## GitHub

- Owner: `kawaiiTaiga`
- Repository: `second_brain`
- Visibility: `public`
- Default branch: `main`
- Remote name: `origin`
- Repository URL: <https://github.com/kawaiiTaiga/second_brain>
- Clone URL: `https://github.com/kawaiiTaiga/second_brain.git`

## Sync Policy

- Pull or otherwise sync from `origin/main` before editing when safe.
- Commit meaningful wiki changes promptly.
- Push updates back to `origin/main` after meaningful maintenance.

## Notes

- Update this page whenever remote, branch, or visibility settings change.
```

Use exact values instead of vague text. Prefer:

- full GitHub URL,
- full clone URL,
- explicit remote name,
- explicit branch name,
- deployment target when relevant.

Do not use a local filesystem path as the primary repository location when a GitHub URL exists.

## Placement Heuristic

Use this quick rule when filing information:

- "What is happening now?" -> `status.md`
- "Where is it?" -> `map.md`
- "How should we work?" -> `skills/`
- "What did we learn?" -> `knowledge/`
- "Who else needs this across projects?" -> `shared/`
- "Is this about the parent project or one child subproject?" -> file it at the matching level
- "Is this a rule for how we operate?" -> `skills/`
- "Is this a fact about where something lives or how it behaves?" -> `knowledge/`
- "Will a fresh session need help finding this later?" -> add or update the nearest index or hub page

## Git Heuristic

When the user asked for git usage:

- create the repository if missing,
- commit initial scaffolding promptly,
- push after meaningful updates,
- record remote details in the wiki if they affect future operations.
- for the user's second-brain wiki, default to `https://github.com/kawaiiTaiga/second_brain.git`.
- do not stop at a local commit if the repository is meant to stay synced on GitHub.
- default standing instruction: "After meaningful wiki changes, sync to GitHub immediately: add, commit, and push to origin/main."

# second-brain Map

## Repository Layout

```text
/
  LLM-Wiki.md
  README.md
  wiki/
    index.md
    log.md
    shared/
      skills/
      knowledge/
    projects/
      second-brain/
        status.md
        map.md
        skills/
        knowledge/
      hampter/
        status.md
        map.md
        skills/
        knowledge/
        subprojects/
          tiaga_face_v0.1/
            status.md
            map.md
            skills/
            knowledge/
```

## File Roles

- `LLM-Wiki.md` - Concept and operating model for the wiki pattern.
- `README.md` - Short repository introduction and navigation.
- `.git/` - Local repository metadata and commit history.
- `wiki/index.md` - Catalog of wiki pages.
- `wiki/log.md` - Append-only activity log.
- `wiki/projects/second-brain/status.md` - Current project state and next actions.
- `wiki/projects/second-brain/map.md` - Structural reference for this repository.
- `wiki/projects/second-brain/knowledge/repository-hosting.md` - GitHub hosting and publication details.
- `wiki/projects/hampter/status.md` - Parent-level HAMPTER context.
- `wiki/projects/hampter/subprojects/tiaga_face_v0.1/status.md` - Subproject state for the face renderer.
- `wiki/projects/hampter/subprojects/tiaga_face_v0.1/map.md` - Exact source layout and local runtime locations for the face renderer.

## Notes

- Keep new durable decisions in `status.md`, `skills/`, or `knowledge/` rather than only in commit messages.
- Register new pages in `wiki/index.md` so future sessions can discover them quickly.
- Default branch is `main` and the configured remote is `origin`.

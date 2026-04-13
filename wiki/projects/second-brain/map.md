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

- `LLM-Wiki.md` - concept and operating model for the wiki pattern.
- `README.md` - short repository introduction and navigation.
- `.git/` - repository metadata and commit history.
- `wiki/index.md` - catalog of wiki pages.
- `wiki/log.md` - append-only activity log.
- `wiki/projects/second-brain/status.md` - current project state and next actions.
- `wiki/projects/second-brain/map.md` - structural reference for this repository.
- `wiki/projects/second-brain/knowledge/repository-hosting.md` - GitHub hosting and publication details.
- `wiki/projects/hampter/status.md` - parent-level HAMPTER context.
- `wiki/projects/hampter/subprojects/tiaga_face_v0.1/status.md` - subproject state for the face renderer.
- `wiki/projects/hampter/subprojects/tiaga_face_v0.1/map.md` - source layout, repository location, and development runtime notes for the face renderer.

## Notes

- Keep new durable decisions in `status.md`, `skills/`, or `knowledge/` rather than only in commit messages.
- Register new pages in `wiki/index.md` so future sessions can discover them quickly.
- Default branch is `main` and the configured remote is `origin`.

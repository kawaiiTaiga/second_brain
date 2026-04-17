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
        taiga/
          status.md
          map.md
          skills/
          knowledge/
          taiga-face/
            status.md
            map.md
            skills/
            knowledge/
          signage/
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
- `wiki/projects/hampter/taiga/status.md` - TAIGA parent-project state for the monorepo.
- `wiki/projects/hampter/taiga/taiga-face/status.md` - project state for the face renderer.
- `wiki/projects/hampter/taiga/signage/status.md` - project state for the signage runtime.

## Notes

- Keep new durable decisions in `status.md`, `skills/`, or `knowledge/` rather than only in commit messages.
- Register new pages in `wiki/index.md` so future sessions can discover them quickly.
- Default branch is `main` and the configured remote is `origin`.


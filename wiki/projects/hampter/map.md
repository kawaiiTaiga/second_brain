# hampter Map

## Wiki Hierarchy

```text
wiki/
  projects/
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

## Role Of This Parent Project

- Parent-level HAMPTER context belongs here.
- Project-specific implementation details belong under direct child folders such as `taiga/`.
- `taiga` is the current documented HAMPTER child project and contains the `taiga-face` and `signage` subprojects.

## Notes

- Keep HAMPTER-wide philosophy or conventions at this level.
- Keep TAIGA monorepo structure and shared repo facts at the `taiga/` level.
- Keep renderer, formula, prompt, and geometry details at the `taiga/taiga-face/` level.
- Keep reactive text-signage runtime details at the `taiga/signage/` level.


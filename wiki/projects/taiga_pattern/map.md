# taiga_pattern Map

Source repository:
- <https://github.com/kawaiiTaiga/taiga>

Tracked branch:
- `origin/main`

## Repository Layout

```text
/
  README.md
  taiga-face/
    analysis/
    artifacts/
    app.js
    dsl-runtime.js
    renderer.js
    index.html
    styles.css
    server.mjs
    package.json
  signage/
    app.js
    index.html
    styles.css
    README.md
    hampter-signage-design.md
    signage-simulator-summary.md
```

## Subproject Boundaries

- `taiga-face/` is the source of truth for the face renderer and formula DSL runtime.
- `signage/` is the source of truth for the reactive text signage simulator.
- Shared repo-level orientation belongs at the root, while implementation detail belongs inside the matching child folder.

## Related Wiki Pages

- `wiki/projects/taiga_pattern/taiga-face/` - face runtime notes.
- `wiki/projects/taiga_pattern/signage/` - signage runtime notes.

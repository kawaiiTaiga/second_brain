# hampter Status

## Summary

`hampter` is the parent project context for formula-driven, continuously evaluated behavior systems. In this wiki, `taiga` is the current HAMPTER child project and now groups both the TAIGA face runtime and the reactive signage runtime.

## Current State

- The parent project exists in the wiki as a container for HAMPTER-specific child projects.
- `taiga` is the currently documented child project.
- `taiga/taiga-face` stores renderer design, DSL philosophy, prompt assets, geometry findings, and workflow rules for the face runtime.
- `taiga/signage` stores the reactive signage simulator, prompt strategy, parser constraints, and runtime notes for text animation work.

## Child Projects

- `taiga` - a TAIGA monorepo that currently contains:
  - `taiga-face` - a WebGL2 + JavaScript face renderer that evaluates formulas every frame and blends transient behaviors over an always-running idle face.
  - `signage` - a browser-based reactive text-signage simulator that turns natural-language intent into low-level motion formulas.

## Next

- Add more HAMPTER child projects under this parent instead of flattening them as separate top-level wiki projects.
- Keep parent-level philosophy and cross-project conventions here if more related pages appear.

## Decisions

- `hampter` is the parent node in the wiki hierarchy.
- `taiga` is documented as a direct HAMPTER child project.
- `taiga-face` and `signage` are documented as TAIGA subprojects inside that parent project.


# taiga Status

Parent project:
- `hampter`

## Summary

`taiga` is a HAMPTER subproject organized as a monorepo. It currently contains the `taiga-face` face renderer and the `signage` reactive text-signage simulator.

## Current State

- The GitHub repository is `https://github.com/kawaiiTaiga/taiga`.
- The repository root now groups:
  - `taiga-face/` for the robot-eye face renderer.
  - `signage/` for the browser-based text signage simulator.
- The face runtime remains the more mature implementation and keeps its analysis and artifact workflow.
- The signage runtime is a newer browser app focused on natural-language-to-formula text motion authoring.

## Child Projects

- `taiga-face` - WebGL2 face runtime with a formula DSL, compact semantic axes, and transient overlay behavior.
- `signage` - Canvas-based text signage simulator with selector-based layers, a safe expression parser, and direct low-level motion channels.

## Next

- Keep the monorepo split clear: face work under `taiga-face/`, signage work under `signage/`.
- Record shared repo-level conventions here if cross-subproject workflow grows.
- Keep the wiki hierarchy synchronized with the monorepo hierarchy.

## Decisions

- The GitHub repository name is `taiga`.
- `taiga-face` is no longer treated as the whole repository; it is a subdirectory inside `taiga`.
- `signage` is a sibling TAIGA subproject rather than a separate top-level HAMPTER project.

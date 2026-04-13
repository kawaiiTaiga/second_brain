# tiaga_face_v0.1 Status

Parent project:

- `hampter`

## Summary

`tiaga_face_v0.1` is a formula-driven robot-eye face runtime. The important product claim is not merely that a face runs on the web. The important claim is that an LLM can describe expression behavior as formulas and the runtime can execute those formulas continuously.

## Current State

- Local workspace path: `C:\Users\dukes\Downloads\hampter_lab\TAIGA_FACE`
- Published repository: <https://github.com/kawaiiTaiga/taiga-face>
- The runtime is a standalone local HTML + WebGL2 application with:
  - preset buttons,
  - direct YAML/JSON DSL input,
  - reactive sliders,
  - live output inspection.
- The current browser surface is usable for direct editing, but it still frames itself too much as a local runtime demo.
- The current repo includes a transient prompt asset at `transient-dsl-prompt.md`.
- The current repo does not yet expose a canonical, user-facing "copy this prompt into an LLM" surface with a copy button.

## Current Priorities

- Emphasize that LLM-authored formulas are the core value, not the fact that the renderer is on the web.
- Provide one canonical executable prompt in the app surface.
- Add a clear copy button for that prompt so a user can move from "describe an expression" to "generate DSL" without reconstructing the prompt manually.
- Keep the formula runtime and renderer semantics aligned with the prompt so generated outputs stay executable.

## Next

- Add a dedicated prompt surface in the UI that explains the goal in LLM terms and includes copy-to-clipboard behavior.
- Treat the prompt as a first-class product surface, not just a hidden doc file.
- Update the app wording so the main flow is:
  1. ask an LLM for a formula,
  2. paste generated YAML,
  3. run the expression.
- Keep the wiki current whenever the canonical prompt, UX flow, or repository structure changes.

## Decisions

- The primary narrative is "LLM can express face behavior through formulas."
- The web runtime is a proving surface for that narrative, not the end in itself.
- Prompt usability is a product requirement, not optional documentation.
- The prompt must be easy to copy and easy to execute against the runtime.

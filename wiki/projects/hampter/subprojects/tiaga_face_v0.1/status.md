# tiaga_face_v0.1 Status

Parent project:
- `hampter`

## Summary

`tiaga_face_v0.1` is a HAMPTER subproject: a vanilla HTML + WebGL2 robot-eye face renderer driven by a formula DSL. The runtime continuously evaluates formulas over time, blends temporary behaviors over an always-running idle face, and renders a stylized black-and-white EVE-like eye face.

## Current State

- The app runs locally with `node server.mjs` or `npm start`.
- The renderer is WebGL2 with a shader-driven eye renderer and a compact semantic coordinate system.
- The runtime supports:
  - compact face mode,
  - direct low-level face mode,
  - transient overlays with automatic return to idle,
  - time-based formulas and helper functions.
- External models can generate YAML formulas directly. The current approach assumes the model can handle coordinate-like parameters as long as the prompt is precise.
- The ordinary presets are usable. `HAPPY` has been softened to avoid the "joker" look.
- Strong smile is no longer treated as a plain lid-clipped eye. It now blends toward a crescent-band shape family in the renderer.

## Current Priorities

- Keep the ordinary `HAPPY` expression in a soft, warm range.
- Reserve the high-smile crescent-band regime for explicit strong smile requests.
- Preserve the HAMPTER philosophy: runtime behavior lives continuously, formulas are artifacts, and the LLM does not drive the face frame-by-frame.
- Keep the wiki pages current when prompt rules, renderer shape families, or coordinate semantics change.

## Next

- If more smile work is needed, tune the renderer shape family first before adding new emotion-specific rules.
- If compact semantics change, re-run the compact-axis analysis and update the knowledge pages.
- If prompt strategy changes, update both `knowledge/prompts.md` and the root prompt files.

## Decisions

- The DSL is allowed to stay coordinate-like. Human-friendly naming is secondary to precise controllability.
- Future work should prefer fixing the coordinate system or the renderer shape family over adding emotion-specific hardcoded modes.
- Smile is special. Most expressions can be produced by lid-clip geometry, but strong smile needs a separate crescent-band renderer regime.
- The wiki is the durable reference layer for future agents; root notes are treated as implementation artifacts, not the only source of truth.

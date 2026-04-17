# signage Status

Parent project:
- `taiga_pattern`

## Summary

`signage` is a TAIGA subproject: a browser-based reactive text-signage simulator that maps natural-language motion intent into selector-driven, low-level formulas over per-character channels.

## Current State

- The runtime is a lightweight HTML/CSS/Canvas app.
- Presets are structured JSON objects with `base`, `baseline`, and selector-scoped `layers`.
- The expression engine no longer uses `new Function`; it parses and evaluates a restricted formula language directly.
- The current authoring model favors low-level channels such as `offset_x`, `offset_y`, `scale_x`, `scale_y`, `rotation`, `skew_x`, `opacity`, `tracking`, `glow`, `blur`, and `brightness`.
- The current implementation is a simulator and prompt-validation surface rather than a full typography engine.

## Current Priorities

- Keep the prompt focused on direct formula generation instead of canned animation categories.
- Preserve selector-based targeting so the model can avoid brittle manual index counting.
- Keep parser constraints and JSON-output rules explicit when external LLMs generate presets.

## Next

- Add clearer safe-range guidance for runtime channels.
- Improve parse-error feedback for malformed formulas.
- Decide whether the simulator should stay canvas-based or evolve toward a deeper typography renderer.

## Decisions

- The signage runtime lives under the `signage/` subdirectory of the `taiga` monorepo.
- The core value is natural-language-to-formula generation, not a preset library.
- Structured motion representation matters because it keeps LLM-generated results editable.

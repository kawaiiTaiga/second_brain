# signage Runtime And Prompting

## Authoring Model

- The signage runtime is designed around direct low-level formulas, not a menu of canned effects.
- The user can describe motion in natural language, but the durable representation is still structured and editable.
- The important split is:
  - natural-language request for the human-facing interface,
  - selector-based formulas for the runtime-facing representation.

## Motion Representation

- Text motion is expressed through low-level channels like `offset_x`, `offset_y`, `scale_x`, `scale_y`, `rotation`, `skew_x`, `opacity`, `tracking`, `glow`, `blur`, and `brightness`.
- Presets use `base`, `baseline`, and `layers`.
- Layers target subsets of the text via selectors rather than manual absolute character counting.

## Selector Rules

- Supported selector styles include:
  - literal substring matches,
  - `{ "word": n }`,
  - `{ "chars": "..." }`,
  - `{ "regex": "..." }`,
  - `"all"`,
  - `"last_word"`.
- Inside a matched span, `char_index` restarts from `0`.
- This is a deliberate design choice to let LLMs work in meaningful spans instead of brittle index arithmetic.

## Parser Rules

- The runtime no longer evaluates formulas with `new Function`.
- It now tokenizes, parses, and evaluates a restricted expression language directly.
- Supported expression pieces currently include:
  - numbers,
  - identifiers,
  - function calls,
  - parentheses,
  - unary `+` and `-`,
  - binary `+`, `-`, `*`, `/`, `%`.
- This keeps the evaluator safer and constrains formula generation to a known surface.

## Prompting Rules

- Prompts for external LLMs should:
  - require valid JSON output,
  - require escaped backslashes in regex strings,
  - describe `rotation` as a small radian value rather than a degree-like number,
  - keep `scale_x` and `scale_y` close to `1` unless strong deformation is explicitly intended,
  - preserve readability unless the request explicitly asks for distortion.

## Product Framing

- The key product strength is not a preset catalog.
- The key product strength is that a lightweight web UI can expose a complex motion system through natural language while still preserving an editable structured representation underneath.

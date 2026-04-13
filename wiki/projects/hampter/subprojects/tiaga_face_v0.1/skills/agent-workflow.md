# tiaga_face_v0.1 Agent Workflow

## Operating Model

- Treat the project as an LLM-to-formula runtime, not merely a face demo page.
- The LLM is expected to generate DSL formulas.
- The runtime executes those formulas continuously.
- When the product message becomes muddy, fix the surface language and prompt flow before adding more renderer complexity.

## Priority Order

When evaluating a request, check in this order:

1. Is the product message clear that LLM-generated formulas are the core value?
2. Is there a visible prompt users can copy and run?
3. Is the generated YAML likely to execute cleanly?
4. Only after that, ask whether the renderer shape family needs tuning.

## Layer Selection Rule

- Prompt discoverability problem -> update `index.html`, `app.js`, and prompt assets
- Runtime parsing problem -> update `dsl-runtime.js`
- Renderer silhouette problem -> update `renderer.js`
- Styling or framing problem -> update `styles.css`

## Mandatory Workflow For Prompt-Oriented Changes

1. Inspect the current prompt asset and current UI surface.
2. Decide whether the issue is:
   - missing prompt visibility,
   - bad copyability,
   - stale prompt content,
   - or runtime incompatibility with the prompt.
3. Keep the prompt and the runtime semantics aligned.
4. File durable changes into the wiki, especially when canonical prompt location or UX requirements change.

## UX Rule

- A copy button for the canonical prompt is not a minor convenience; it is part of the primary usage path.
- The app should help users go from natural-language request to executable DSL with as little reconstruction as possible.

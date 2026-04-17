# taiga-face Agent Workflow

## Operating Model

- Treat the project as a formula-driven runtime, not a keyframe animation editor.
- The LLM is expected to generate DSL formulas. Do not redesign the project around frame-by-frame control.
- The right layer to change depends on the failure mode:
  - coordinate meaning problem -> adjust `dsl-runtime.js`,
  - shape-family problem -> adjust `renderer.js`,
  - prompt control problem -> adjust prompt assets.

## Mandatory Workflow For Geometry Changes

1. Identify whether the issue is:
   - compact coordinate semantics,
   - renderer silhouette family,
   - preset/prompt guidance,
   - or invalid YAML / runtime parsing.
2. Change the smallest relevant layer.
3. Re-run the right validation:
   - coordinate changes -> `node analysis\\compact-axis-analysis.mjs`
   - renderer smile changes -> `node analysis\\capture-smile-sweep.mjs`
4. Inspect artifacts before closing the task.
5. File durable conclusions into the wiki.

## Smile-Specific Rule

- Do not immediately add new emotion-specific hardcoded modes when smile looks wrong.
- First decide whether the problem is:
  - entering the extreme smile regime too early,
  - ordinary happy values being too aggressive,
  - or the renderer shape family being wrong.
- Ordinary `HAPPY` should stay below the strong crescent regime.
- Strong closed-eye smiles should use the crescent-band regime intentionally.

## Prompting Rule

- When preparing prompts for external models, describe:
  - coordinate semantics,
  - safe ranges,
  - strong-smile versus ordinary-happy distinction,
  - and transient return-to-idle behavior.
- Do not assume human-readable emotion names alone are enough.

## YAML Rule

- Preserve valid indentation. Broken indentation can make the runtime interpret `behavior` and `face` incorrectly.


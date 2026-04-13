# tiaga_face_v0.1 Prompts

## Current Real Prompt Asset

- Present in repository: `transient-dsl-prompt.md`

The older wiki reference to `FACE_FORMULA_PROMPT_KO.md` is stale. That file is not present in the current `TAIGA_FACE` workspace and should no longer be treated as the canonical prompt source.

## Product Requirement

The project needs a canonical prompt surface that is visible from the app and easy to copy.

Required behavior:

- show one executable prompt that explains how the LLM should emit face DSL,
- expose a copy button next to that prompt,
- let the user move directly from copied prompt -> LLM -> returned YAML -> paste into runtime.

## Why This Matters

The project's main claim is that an LLM can express behavior through formulas.

Without a prominent prompt surface:

- users have to reconstruct instructions manually,
- outputs become less consistent,
- the product reads like "a local face renderer" instead of "a formula interface for LLM expression generation."

## Prompt Guidance

The canonical prompt should teach:

- output only YAML,
- formula-driven behavior rather than keyframes,
- compact face mode as the preferred control space,
- transient behavior when a temporary reaction is intended,
- safe expression semantics for `openness`, `squint`, `smile`, `roundness`, `slant`, `asymmetry`, `gaze`, `glow`, and `warmth`,
- use of `time`, `local_time`, `env(...)`, `decay(...)`, and related helpers.

## UX Rule

Treat the copyable prompt as part of the runtime UI and onboarding flow, not a hidden developer note.

# taiga-face Prompts

## Canonical Prompt Assets

- Root file: `FACE_FORMULA_PROMPT_KO.md`
- Older transient-oriented file: `transient-dsl-prompt.md`

Use `FACE_FORMULA_PROMPT_KO.md` as the current main prompt for external models.

## What The Current Prompt Encodes

The prompt explicitly teaches:
- compact coordinate semantics,
- safe value ranges,
- that the system is formula-driven, not keyframe-driven,
- that temporary reactions should use transient behavior,
- that strong smile is a rounded crescent-band regime,
- that ordinary `HAPPY` should stay softer and avoid the joker/sneer look.

## How To Use It

1. Paste the full prompt block from `FACE_FORMULA_PROMPT_KO.md`.
2. Replace only the final `User request`.
3. Ask for one YAML object only.
4. Reformat the returned YAML if indentation is broken before testing it.

## Good Request Language

For ordinary happy:
- `soft happy`
- `warm happy`
- `not joker-like`
- `not an extreme crescent smile`

For strong closed-eye smile:
- `strong crescent smile`
- `rounded parenthesis-like closed-eye smile`

For transient reactions:
- `temporary reaction`
- `returns to idle`

## Prompting Principle

The prompt should constrain the geometry enough that different models stay inside the same emotional family, while still allowing stylistic variation in formulas.


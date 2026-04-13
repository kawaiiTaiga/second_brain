# tiaga_face_v0.1 Usability And Surface

## Main Surface Principle

The interface should guide the user toward LLM-assisted formula generation.

Good framing:

- "Describe an expression, copy the prompt, ask an LLM, paste YAML, run it."

Weak framing:

- "This is just a local face runtime with some controls."

## Required Surface Elements

- one canonical prompt block,
- one copy button for that prompt,
- direct DSL paste area,
- immediate apply action,
- visible live output for debugging.

## Framing Requirement

The page should communicate:

- the system is formula-driven,
- the LLM can author those formulas,
- the runtime is where those formulas are executed and inspected.

## Anti-Pattern

Do not let the prompt live only in repository docs. If the prompt is central to usage, it must be available in the product surface itself.

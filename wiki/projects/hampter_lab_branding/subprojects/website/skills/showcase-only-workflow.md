# website Showcase-Only Workflow

Use this page when the task is about the public HAMPTER LAB website surface.

## Core Boundary

- `hampter-lab` is the showcase and brand site.
- Project repositories such as `taiga-face` are the source of truth for the actual project experiments.
- Do not confuse "change the website" with "change the project repo."

## Default Rule

If the user asks to update what appears on the public HAMPTER LAB site:

- edit `https://github.com/kawaiiTaiga/hampter-lab`
- do not edit or push project repos unless the user explicitly asks for that too

If the user asks to update the actual project runtime or experiment source:

- edit the matching project repo such as `https://github.com/kawaiiTaiga/taiga-face`
- do not assume the showcase site should mirror that change automatically

## Source Of Truth Rule

- Showcase copy, cards, links, public summaries, and integrated preview surfaces belong to `hampter-lab`
- Experiment code, prototype UI, and project-internal prompt flow belong to the project repo

## Decision Rule For Ambiguous Requests

When the request mentions:

- "website"
- "showcase"
- "portfolio"
- "what users see on hampterlab"

then treat `hampter-lab` as the only target unless the user explicitly says to modify a project repo too.

When the request mentions:

- the project folder itself
- the prototype runtime
- the experiment repo
- internal prompt UX for the project app

then treat the project repo as the target unless the user explicitly says to mirror it into the showcase site.

## Safe Response Pattern

Before editing, make the target explicit in your own working note:

- `Target: hampter-lab showcase only`
- or `Target: taiga-face project repo`

## Anti-Pattern

Do not push a project-repo change and then describe it as if the public website was updated.

That creates exactly the confusion this page is meant to prevent.

## Practical Example

- Adding a TAIGA card, changing `/taiga/` on the public site, adjusting homepage layout:
  - `hampter-lab`
- Changing the standalone TAIGA_FACE app's prompt block, internal buttons, or prototype controls:
  - `taiga-face`

## If Both Need Changes

If the user wants both:

1. update the project repo as the experimental source
2. separately update `hampter-lab` as the showcase surface
3. report clearly that two repositories were changed

# website Skills

Use this folder for repeatable workflows that govern how the HAMPTER LAB website should be maintained.

## Core Workflows

- Site maintenance skill source: `C:\Users\dukes\.codex\skills\hampter-site-maintainer\SKILL.md`
- Post publishing skill source: `C:\Users\dukes\.codex\skills\hampter-post-publisher\SKILL.md`

## Working Rules

- Use `https://github.com/kawaiiTaiga/hampter-lab` as the source-of-truth repository.
- Pull from `origin/main` before editing when the checkout is already published and clean.
- Validate meaningful site changes with `npm run build`.
- Push ready changes to `origin/main`; Vercel is connected and should redeploy from GitHub.
- Keep the visual tone cold, clean, and lab-like unless the user explicitly changes the direction.
- Do not reintroduce mock `MAKES` or mock `DEV LOG` content.

## Content Workflow

- New lab entries are expected in three versions: `origin`, `korean`, `english`.
- Use one shared `translationKey` across those variants.
- Publish new posts under `src/content/lab/` only when real content is supplied.

## Runtime Workflow

- Keep interactive runtime pages inside the main site shell when the user wants them to feel like part of HAMPTER LAB.
- Reuse the existing TAIGA face runtime pattern for future browser-based runtime pages when possible.

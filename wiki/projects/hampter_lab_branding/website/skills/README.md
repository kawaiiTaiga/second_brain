# website Skills

Use this folder for repeatable workflows that govern how the HAMPTER LAB website should be maintained.

## Core Workflows

- Site maintenance skill source: `C:\Users\dukes\.codex\skills\hampter-site-maintainer\SKILL.md`
- Post publishing skill source: `C:\Users\dukes\.codex\skills\hampter-post-publisher\SKILL.md`
- Wiki maintenance skill source: `C:\Users\dukes\.codex\skills\llm-wiki\SKILL.md`
- Showcase boundary rule: `showcase-only-workflow.md`

## Working Rules

- Use `https://github.com/kawaiiTaiga/hampter-lab` as the source-of-truth repository.
- Pull from `origin/main` before editing when the checkout is already published and clean.
- Validate meaningful site changes with `npm run build`.
- Push ready changes to `origin/main`; Vercel is connected and should redeploy from GitHub.
- Do not run a manual production deploy after every push.
- If GitHub and production disagree, check whether Vercel actually deployed the latest commit; use a manual production deploy only as an exception path.
- Keep the visual tone cold, clean, and lab-like unless the user explicitly changes the direction.
- Do not reintroduce mock `MAKES` or mock `DEV LOG` content.
- If the user says "website" or "showcase", default to changing `hampter-lab` only.
- Do not report a `taiga-face` project-repo change as if it updated the public HAMPTER LAB site.

## Content Workflow

- New lab entries are expected in three versions: `origin`, `korean`, `english`.
- Use one shared `translationKey` across those variants.
- Publish new posts under `src/content/lab/` only when real content is supplied.

## Runtime Workflow

- Keep interactive runtime pages inside the main site shell when the user wants them to feel like part of HAMPTER LAB.
- Reuse the existing TAIGA face runtime pattern for future browser-based runtime pages when possible.
- Current TAIGA runtime route is `/makes/taiga_face/`.

## Wiki Filing Rule

- Keep procedural instructions in this `skills/` folder
- Keep exact repository URLs, routes, deployment targets, and solved behaviors in `knowledge/`

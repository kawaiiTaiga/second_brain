# website Skills

Read this page after [../index.md](../index.md). This is the local workflow hub for the HAMPTER LAB website.

## Deep Pages

- [showcase-only-workflow.md](./showcase-only-workflow.md) - Boundary between website-only changes and changes that belong in another project repo.

## Referenced Skills

- `hampter-site-maintainer`
- `hampter-post-publisher`
- `llm-wiki`

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
- Do not report a `taiga` project-repo change as if it updated the public HAMPTER LAB site.

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

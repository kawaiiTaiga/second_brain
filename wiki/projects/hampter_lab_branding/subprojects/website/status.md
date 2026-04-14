# website Status

## Summary

The `website` subproject is the live Astro-based HAMPTER LAB site. It functions as the current public brand surface, a minimal archive shell, and the host for the integrated TAIGA face runtime.

## Current State

- Repository: `https://github.com/kawaiiTaiga/hampter-lab`
- Local path used in recent work: `C:\Users\dukes\Downloads\hampter_lab`
- Production URL: <https://hampterlab.vercel.app>
- Runtime page: <https://hampterlab.vercel.app/taiga/>
- Homepage currently shows only one real `MAKES` entry: `TAIGA Face Runtime`
- `DEV LOG` and `/lab/` are empty-state placeholders until real posts are published
- Mock detail routes for old `makes` and `lab` entries were removed
- Related Codex skills are now filed in the wiki as part of this subproject context
- The site should be operated as a showcase surface separate from project-experiment repos

## Next

- Publish real posts using the `origin / korean / english` content workflow.
- Add future `MAKES` items only when there is a real interactive page or project to link.
- Continue aligning new runtime pages to the same monochrome HAMPTER LAB tone.

## Decisions

- Keep TAIGA face integrated under the main site rather than as a separate standalone web deployment.
- Use the same HAMPTER LAB shell and styling system for runtime pages.
- Prefer simple empty states over fake project or blog content.
- Treat `hampter-lab` as the website target and project repos as separate experiment targets unless the user explicitly requests both.

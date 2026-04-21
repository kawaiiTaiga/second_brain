# Wiki Log

## [2026-04-13] second-brain | Initialized wiki repository
- Created the first `wiki/` structure based on the `LLM Wiki` pattern.
- Added initial `status.md`, `map.md`, shared placeholders, and repository documentation.

## [2026-04-13] second-brain | Published repository to GitHub
- Created the public GitHub repository `kawaiiTaiga/second_brain`.
- Recorded hosting metadata in `projects/second-brain/knowledge/repository-hosting.md`.

## [2026-04-13] second-brain | Tracked llm-wiki skill in repository
- Added a repository-managed copy of the `llm-wiki` Codex skill under `skills/llm-wiki/`.
- This keeps the GitHub repository in sync with the locally installed skill rules and templates.

## [2026-04-16] second-brain | Strengthened index-first wiki navigation rules
- Updated the `llm-wiki` skill to frame the wiki as durable knowledge for future LLM sessions.
- Added `Read Order` and `Index-First Rules` so fresh sessions start from `wiki/index.md` and navigate through hub pages.
- Clarified that the root index should stay selective while `status.md`, `skills/README.md`, and `knowledge/README.md` act as local hubs.

## [2026-04-16] second-brain | Converted wiki navigation to staged indexes
- Reduced `wiki/index.md` to top-level shared and project entry points.
- Added second-stage `index.md` pages for shared space, parent projects, and active child projects.
- Shifted the wiki toward `root index -> project index -> local hub` navigation instead of listing deep notes at the root.

## [2026-04-16] second-brain | Standardized local hub pages
- Aligned `skills/README.md` and `knowledge/README.md` pages across projects so each one states its role as a local hub.
- Kept the structure shallow: root index, project index, local hub, then leaf pages.
- Clarified that the structure only needs to be strict enough to prevent LLM confusion, not to satisfy a perfect taxonomy.

## [2026-04-16] second-brain | Added standing GitHub sync instruction
- Updated the `llm-wiki` skill to treat immediate `origin/main` sync as a standing command after meaningful wiki changes.
- Added the same wording to the repository-tracked skill templates so future copies inherit the behavior.

## [2026-04-21] second-brain | Tightened GitHub-first references
- Updated the `llm-wiki` skill to prefer canonical GitHub URLs whenever a canonical repo exists.
- Removed remaining local machine path references from the HAMPTER LAB website wiki where direct GitHub URLs were better.
## [2026-04-21] second-brain | Tightened GitHub-only location guidance
- Tightened the `llm-wiki` skill and wiki docs so location references use direct GitHub URLs.
- Left local filesystem paths as exceptions only when the filesystem location itself is operationally important.
- Added a GitHub-first lookup rule so future sessions check the canonical GitHub repo before local copies when both exist.
- Replaced a local `.codex` skill path reference with a skill-name-oriented description.

## [2026-04-13] second-brain | Added wiki maintenance skills
- Added shared skills for wiki updates, project bootstrap, and public-repo safety.
- Added a project-specific maintenance workflow for the `second_brain` repository.
- Registered the new skill pages in `wiki/index.md`.

## [2026-04-13] hampter | Added taiga-face project page
- Added `hampter` as a parent project in the wiki hierarchy.
- Filed `taiga-face` under `projects/hampter/taiga-face/`.
- Recorded the face renderer's design, prompts, map, workflow, smile-shape findings, and repository metadata.

## [2026-04-13] hampter | Switched taiga-face location references to git-first
- Rewrote hosting references to use GitHub repository URLs, clone URLs, remote names, and tracked branches as the canonical locations.
- Updated `taiga-face` documentation to point at `https://github.com/kawaiiTaiga/taiga` instead of local filesystem paths.

## [2026-04-13] hampter_lab_branding | Added website project hierarchy
- Added parent project pages for `hampter_lab_branding`.
- Added `website` as a child project page with status, map, skills, and hosting knowledge pages.
- Recorded the live website repository, Vercel deployment target, and the TAIGA face runtime integration approach.

## [2026-04-13] hampter_lab_branding | Expanded website operating knowledge
- Added brand-direction notes at the parent project level.
- Added website knowledge pages for content workflow, routes and surfaces, and TAIGA face runtime integration.
- Expanded the website skill page to include wiki usage and deployment troubleshooting rules.

## [2026-04-14] hampter_lab_branding | Clarified website deployment workflow
- Updated the website wiki to reflect the current TAIGA runtime route `/makes/taiga_face/`.
- Recorded that normal website deployment should be `git push` to `origin/main`, with manual Vercel production deploys used only as an exception path.

## [2026-04-14] hampter_lab_branding | Flattened website wiki path
- Moved the website pages into `projects/hampter_lab_branding/website/`.
- Removed the extra nested directory so this project uses a flatter `branding/website` structure.

## [2026-04-14] hampter_lab_branding | Added showcase-only workflow boundary
- Added a dedicated workflow page that separates `hampter-lab` website changes from project-repo changes.
- Recorded that the public site is the showcase surface while repos like `taiga-face` remain separate experiment sources.
- Updated website status, skills, index, and repository-hosting notes to reduce cross-repo confusion.

## [2026-04-13] rf | Added RF parent project and startopolgy10 project page
- Added `rf` as the parent wiki project for wireless topology and middleware work.
- Added `startopolgy10` under `projects/rf/` to capture the Fleet AirLink star-topology implementation.
- Recorded implementation history, test results, hwsim/kernel notes, networking/router guidance, GUI/video routing behavior, current known gaps, and RF power guidance.

## [2026-04-14] wiki | Flattened remaining nested project directories
- Moved `projects/hampter/taiga-face/` into the parent project's top level.
- Moved `projects/rf/startopolgy10/` into the parent project's top level.
- Updated wiki references to stop using an extra nested container path.

## [2026-04-13] rf | Added new-session quickstart pages for startopolgy10
- Added `skills/session-start.md` as the first-read handoff page for a fresh session.
- Added `knowledge/runtime-startup.md` with immediate runnable paths and sanity checks.
- Updated `status.md`, `skills/README.md`, `wiki/index.md`, and `wiki/log.md` so a new agent can start work without re-deriving state from chat history.

## [2026-04-13] rf | Added public repository reference for startopolgy10
- Added `knowledge/repository-access.md` with the canonical wiki repo name, HTTPS clone URL, and relevant subtree paths.
- Updated `skills/session-start.md` and `knowledge/README.md` so a new session can find the public wiki immediately.

## [2026-04-16] rf | Added rf-agent child project
- Added `wiki/projects/rf/rf-agent/` for the TinySA- and tshark-driven `rf-agent` CLI maintained in the local `RF_station` working tree.
- Recorded the current repository state, session-start workflow, high-level LLM command routing, and live TinySA validation status.
- Updated the RF parent index, map, and status pages so future sessions can discover the new child project quickly.

## [2026-04-17] hampter | Reframed TAIGA as a parent project and added signage
- Renamed the TAIGA experiment repository from `taiga-face` to `taiga`.
- Recorded the new monorepo layout with `taiga-face/` and `signage/` subdirectories.
- Moved the old direct child wiki pages under `projects/hampter/taiga/taiga-face/`.
- Added a new `projects/hampter/taiga/signage/` subproject with runtime, prompting, and hosting notes.

## [2026-04-17] taiga_pattern | Promoted TAIGA to a top-level wiki project
- Moved the TAIGA monorepo wiki pages from `projects/hampter/taiga/` to `projects/taiga_pattern/`.
- Reframed `hampter` and `taiga_pattern` as sibling top-level projects instead of parent and child.
- Updated root and project maps so future sessions navigate to TAIGA through the new top-level path.

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

## [2026-04-13] second-brain | Added wiki maintenance skills
- Added shared skills for wiki updates, project bootstrap, and public-repo safety.
- Added a project-specific maintenance workflow for the `second_brain` repository.
- Registered the new skill pages in `wiki/index.md`.

## [2026-04-13] hampter | Added tiaga_face_v0.1 as subproject
- Added `hampter` as a parent project in the wiki hierarchy.
- Filed `tiaga_face_v0.1` under `projects/hampter/subprojects/tiaga_face_v0.1/`.
- Recorded the face renderer's design, prompts, map, workflow, smile-shape findings, and repository metadata.

## [2026-04-13] hampter | Switched tiaga_face_v0.1 location references to git-first
- Rewrote hosting references to use GitHub repository URLs, clone URLs, remote names, and tracked branches as the canonical locations.
- Updated `tiaga_face_v0.1` documentation to point at `https://github.com/kawaiiTaiga/taiga-face` instead of local filesystem paths.

## [2026-04-13] hampter_lab_branding | Added website project hierarchy
- Added parent project pages for `hampter_lab_branding`.
- Added `website` as a subproject with status, map, skills, and hosting knowledge pages.
- Recorded the live website repository, Vercel deployment target, and the TAIGA face runtime integration approach.

## [2026-04-13] hampter_lab_branding | Expanded website operating knowledge
- Added brand-direction notes at the parent project level.
- Added website knowledge pages for content workflow, routes and surfaces, and TAIGA face runtime integration.
- Expanded the website skill page to include wiki usage and deployment troubleshooting rules.

## [2026-04-13] rf | Added RF parent project and startopolgy10 subproject
- Added `rf` as the parent wiki project for wireless topology and middleware work.
- Added `startopolgy10` under `projects/rf/subprojects/` to capture the Fleet AirLink star-topology implementation.
- Recorded implementation history, test results, hwsim/kernel notes, networking/router guidance, GUI/video routing behavior, current known gaps, and RF power guidance.

## [2026-04-13] rf | Added new-session quickstart pages for startopolgy10
- Added `skills/session-start.md` as the first-read handoff page for a fresh session.
- Added `knowledge/runtime-startup.md` with immediate runnable paths and sanity checks.
- Updated `status.md`, `skills/README.md`, `wiki/index.md`, and `wiki/log.md` so a new agent can start work without re-deriving state from chat history.

## [2026-04-13] rf | Added public repository reference for startopolgy10
- Added `knowledge/repository-access.md` with the canonical wiki repo name, HTTPS clone URL, and relevant subtree paths.
- Updated `skills/session-start.md` and `knowledge/README.md` so a new session can find the public wiki immediately.

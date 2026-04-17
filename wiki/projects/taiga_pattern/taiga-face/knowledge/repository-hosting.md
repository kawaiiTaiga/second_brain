# taiga-face Repository And Runtime Hosting

## Source Repository

- Owner: `kawaiiTaiga`
- Repository: `taiga`
- Remote name: `origin`
- Default branch: `main`
- Repository URL: <https://github.com/kawaiiTaiga/taiga>
- Clone URL: `https://github.com/kawaiiTaiga/taiga.git`

## Canonical Source Locations

- The TAIGA repository is now a monorepo.
- The face runtime lives under the `taiga-face/` subdirectory.
- Key face-runtime files are rooted at:
  - `/taiga-face/app.js`
  - `/taiga-face/dsl-runtime.js`
  - `/taiga-face/renderer.js`
  - `/taiga-face/index.html`
  - `/taiga-face/styles.css`
  - `/taiga-face/server.mjs`
  - `/taiga-face/analysis/`
  - `/taiga-face/artifacts/`
  - `/taiga-face/FACE_COORDINATE_ANALYSIS.md`
  - `/taiga-face/FACE_FORMULA_PROMPT_KO.md`
- The sibling signage runtime lives under `/signage/`.

## Documentation Repository

- Durable wiki pages for this project page live in the second-brain repository:
  - Repository URL: <https://github.com/kawaiiTaiga/second_brain>
  - Clone URL: `https://github.com/kawaiiTaiga/second_brain.git`
  - Remote name: `origin`
  - Branch: `main`
  - Wiki path inside that repository: `wiki/projects/taiga_pattern/taiga-face/`

## Development Runtime

- Start command: `cd taiga-face && npm start`
- Alternate start command: `cd taiga-face && node server.mjs`
- Default development port: `4173`


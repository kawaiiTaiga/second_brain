# taiga-face Map

Parent project:
- `taiga`

Source repository:
- <https://github.com/kawaiiTaiga/taiga>

Tracked branch:
- `origin/main`

## Repository Layout

```text
/
  README.md
  taiga-face/
    analysis/
      capture-smile-sweep.mjs
      compact-axis-analysis.mjs
    artifacts/
      ...
    app.js
    dsl-runtime.js
    renderer.js
    index.html
    styles.css
    server.mjs
    package.json
    FACE_COORDINATE_ANALYSIS.md
    FACE_FORMULA_PROMPT_KO.md
    transient-dsl-prompt.md
  signage/
    index.html
    app.js
    styles.css
    hampter-signage-design.md
    signage-simulator-summary.md
```

## Key Runtime Files

- `taiga-face/app.js` - browser entry point; wires UI, behavior engine, and renderer.
- `taiga-face/dsl-runtime.js` - DSL parser, formula compiler, compact mapping, transient overlay engine, idle/autonomy behavior, and evaluation helpers.
- `taiga-face/renderer.js` - WebGL2 renderer and fragment shader source.
- `taiga-face/index.html` - application shell and control panel.
- `taiga-face/styles.css` - UI styling.
- `taiga-face/server.mjs` - minimal static file server, default port `4173`.

## Analysis And Artifacts

- `taiga-face/analysis/capture-smile-sweep.mjs` - captures smile sweep images through the live app using Playwright.
- `taiga-face/analysis/compact-axis-analysis.mjs` - measures compact-coordinate effects and writes analytical summaries.
- `taiga-face/artifacts/smile-sweep-strip.png` - current smile sweep overview image.
- `taiga-face/FACE_COORDINATE_ANALYSIS.md` - generated analysis summary for the compact coordinate system.

## Prompt And Documentation Assets

- `taiga-face/FACE_FORMULA_PROMPT_KO.md` - current formula-generation prompt for external models.
- `taiga-face/transient-dsl-prompt.md` - older transient-oriented prompt.
- `taiga-face/FACE_DSL_SYSTEM.md` - older system note; keep with caution because some terminal environments show mojibake when reading it.

## Related Wiki Pages

- `wiki/projects/hampter/status.md` - HAMPTER parent project summary.
- `wiki/projects/hampter/taiga/status.md` - TAIGA parent project summary.
- `wiki/projects/hampter/taiga/taiga-face/knowledge/repository-hosting.md` - canonical repository and runtime metadata.

## Execution Notes

- Start the app with `npm start` or `node server.mjs` from `taiga-face/`.
- Default development port is `4173`.
- If `EADDRINUSE` appears, the server is usually already running on `4173`.

## Search Hints

- Search for `mapCompactChannelsToFace` in `taiga-face/dsl-runtime.js` for compact coordinate behavior.
- Search for `sampleEnvelope` in `taiga-face/dsl-runtime.js` for transient timing.
- Search for `smileCurve`, `smileBandDist`, and `smileShapeBlend` in `taiga-face/renderer.js` for the smile renderer regime.


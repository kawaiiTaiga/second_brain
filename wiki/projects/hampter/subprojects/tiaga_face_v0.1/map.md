# tiaga_face_v0.1 Map

Parent project:
- `hampter`

Source repository:
- <https://github.com/kawaiiTaiga/taiga-face>

Tracked branch:
- `origin/main`

## Repository Layout

```text
/
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
```

## Key Runtime Files

- `app.js` - browser entry point; wires UI, behavior engine, and renderer.
- `dsl-runtime.js` - DSL parser, formula compiler, compact mapping, transient overlay engine, idle/autonomy behavior, and evaluation helpers.
- `renderer.js` - WebGL2 renderer and fragment shader source.
- `index.html` - application shell and control panel.
- `styles.css` - UI styling.
- `server.mjs` - minimal static file server, default port `4173`.

## Analysis And Artifacts

- `analysis/capture-smile-sweep.mjs` - captures smile sweep images through the live app using Playwright.
- `analysis/compact-axis-analysis.mjs` - measures compact-coordinate effects and writes analytical summaries.
- `artifacts/smile-sweep-strip.png` - current smile sweep overview image.
- `FACE_COORDINATE_ANALYSIS.md` - generated analysis summary for the compact coordinate system.

## Prompt And Documentation Assets

- `FACE_FORMULA_PROMPT_KO.md` - current formula-generation prompt for external models.
- `transient-dsl-prompt.md` - older transient-oriented prompt.
- `FACE_DSL_SYSTEM.md` - older system note; keep with caution because some terminal environments show mojibake when reading it.

## Related Wiki Pages

- `wiki/projects/hampter/status.md` - parent project summary.
- `wiki/projects/hampter/subprojects/tiaga_face_v0.1/knowledge/repository-hosting.md` - canonical repository and runtime metadata.

## Execution Notes

- Start the app with `npm start` or `node server.mjs`.
- Default development port is `4173`.
- If `EADDRINUSE` appears, the server is usually already running on `4173`.

## Search Hints

- Search for `mapCompactChannelsToFace` in `dsl-runtime.js` for compact coordinate behavior.
- Search for `sampleEnvelope` in `dsl-runtime.js` for transient timing.
- Search for `smileCurve`, `smileBandDist`, and `smileShapeBlend` in `renderer.js` for the smile renderer regime.

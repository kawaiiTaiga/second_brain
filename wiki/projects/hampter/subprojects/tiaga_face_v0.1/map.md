# tiaga_face_v0.1 Map

Parent project:

- `hampter`

## Repository Layout

```text
C:\Users\dukes\Downloads\hampter_lab\TAIGA_FACE
  artifacts/
  node_modules/
  app.js
  dsl-runtime.js
  renderer.js
  index.html
  styles.css
  server.mjs
  package.json
  package-lock.json
  transient-dsl-prompt.md
  FACE_DSL_SYSTEM.md
  roundtrip-transient-doubt.yaml
  eve-eyes-v2.html
  Anki-Eyes.jpg
```

## Key Runtime Files

- `app.js` - browser entry point; wires UI controls, behavior engine, and renderer.
- `dsl-runtime.js` - DSL parsing, formula compilation, preset definitions, compact mapping, transient overlay logic, and autonomous behavior helpers.
- `renderer.js` - WebGL2 renderer and shader source for the eye display.
- `index.html` - application shell with presets, DSL editor, sliders, and live output panel.
- `styles.css` - standalone UI styling for the local runtime.
- `server.mjs` - minimal local server for the standalone app.
- `package.json` - local start command definition.

## Prompt And Usage Assets

- `transient-dsl-prompt.md` - current real prompt asset present in the repo.
- `FACE_DSL_SYSTEM.md` - system explanation document; usable as a reference but terminal rendering can be garbled.
- `roundtrip-transient-doubt.yaml` - example DSL artifact.

## Repository Facts

- Local git repo exists in `C:\Users\dukes\Downloads\hampter_lab\TAIGA_FACE\.git`
- Remote: `origin`
- GitHub URL: <https://github.com/kawaiiTaiga/taiga-face>

## Execution Notes

- Start command: `npm start`
- Alternate start command: `node server.mjs`
- Default local URL from the current server implementation: `http://127.0.0.1:4173`

## Search Hints

- Search `PRESETS` in `dsl-runtime.js` for built-in behavior examples.
- Search `applyBehavior` in `app.js` for the current user execution path.
- Search `createBehaviorEngine` in `dsl-runtime.js` for the execution model.
- Search `createRenderer` in `renderer.js` for the draw path.

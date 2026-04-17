# TAIGA Face Runtime

## Integration Strategy

- The TAIGA face runtime is integrated directly into the main Astro site
- It is not treated as a separate public website
- The runtime is served at `/makes/taiga_face/`

## Important Files

- `C:\Users\dukes\Downloads\hampter_lab\src\pages\makes\taiga_face.astro`
- `C:\Users\dukes\Downloads\hampter_lab\src\components\TaigaDemo.astro`
- `C:\Users\dukes\Downloads\hampter_lab\src\scripts\taiga-face\app.js`
- `C:\Users\dukes\Downloads\hampter_lab\src\scripts\taiga-face\dsl-runtime.js`
- `C:\Users\dukes\Downloads\hampter_lab\src\scripts\taiga-face\renderer.js`

## Runtime Notes

- The renderer is a client-side WebGL2 face display
- Runtime logic is client-side and does not require a separate backend for the current preview
- The UI was restyled to match the monochrome HAMPTER LAB surface instead of reusing the old standalone TAIGA_FACE page styling

## Local Reference Source

- The current experiment source is the TAIGA monorepo at `https://github.com/kawaiiTaiga/taiga`
- The face runtime lives under the `taiga-face/` subdirectory in that repo
- The signage runtime lives beside it under `signage/`
- The website repository remains separate and should not absorb the TAIGA monorepo directly

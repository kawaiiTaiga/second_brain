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

- There is a separate local working folder named `TAIGA_FACE` under the website workspace
- It is treated as a reference/prototype source
- The main website repository ignores that folder so it is not accidentally committed into the site repo

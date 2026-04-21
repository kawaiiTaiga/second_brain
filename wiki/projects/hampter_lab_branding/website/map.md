# website Map

## Repository Layout

```text
/
  src/
    components/
      DevLogList.astro
      MakesCarousel.astro
      TaigaDemo.astro
    layouts/
      BaseLayout.astro
    pages/
      index.astro
      makes/
        taiga_face.astro
      lab/
        index.astro
    scripts/
      taiga-face/
        app.js
        dsl-runtime.js
        renderer.js
    styles/
      global.css
  public/
    images/
      brand-logo.png
  package.json
  astro.config.mjs
```

## File Roles

- `src/pages/index.astro` - Homepage with About, Makes, and Dev Log sections.
- `src/pages/makes/taiga_face.astro` - TAIGA face runtime page entry.
- `src/pages/lab/index.astro` - Archive landing page, currently empty-state only.
- `src/components/TaigaDemo.astro` - Site-integrated TAIGA face console UI.
- `src/scripts/taiga-face/app.js` - Browser bootstrap that wires the page UI to the runtime.
- `src/scripts/taiga-face/dsl-runtime.js` - TAIGA face DSL behavior engine.
- `src/scripts/taiga-face/renderer.js` - WebGL2 face renderer.
- `src/styles/global.css` - Shared monochrome site styling and runtime panel styling.
- `public/images/brand-logo.png` - Main HAMPTER LAB logo asset.
- `package.json` - Astro scripts: `dev`, `build`, `preview`.

## Notes

- Source-of-truth repository: <https://github.com/kawaiiTaiga/hampter-lab>
- The site is a static Astro build.
- Runtime interactivity is handled client-side inside the built site.
- The TAIGA runtime source now lives in the separate `taiga` monorepo and is treated as a reference source rather than part of the website repo.
- Durable operating notes are split further into `knowledge/repository-hosting.md`, `knowledge/content-workflow.md`, `knowledge/routes-and-surfaces.md`, and `knowledge/taiga-face-runtime.md`.

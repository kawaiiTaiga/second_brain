# tiaga_face_v0.1 Design

## Core Product Position

The project should be understood as an LLM-to-expression runtime.

The key value is:

- an LLM can output formula DSL,
- that DSL can be pasted into the runtime,
- the runtime evaluates it continuously and renders a face.

The key value is not simply "there is a web page with eyes on it."

## Operating Philosophy

- The runtime stays alive and evaluates formulas every frame.
- The LLM should produce behavior artifacts, not frame-by-frame commands.
- The face is a continuously computed result of formulas plus transient overlays.
- A valid formula should remain runnable after generation without a live LLM connection.

## Architectural Layers

### Runtime Layer

`dsl-runtime.js` owns:

- behavior parsing,
- formula compilation,
- evaluation helpers,
- preset definitions,
- compact channel mapping,
- transient overlays,
- idle/autonomous behavior logic.

### Rendering Layer

`renderer.js` owns:

- WebGL2 setup,
- shader program creation,
- eye rendering and black/white compositing.

### Surface Layer

`index.html` and `app.js` own:

- preset browsing,
- DSL paste/apply flow,
- reactive input sliders,
- live output inspection,
- the prompt-to-runtime usability path.

## UX Interpretation

The most important user journey should be:

1. user describes a desired expression in natural language,
2. an LLM converts that request into YAML formula DSL,
3. user pastes the result into the app,
4. runtime executes it immediately.

That means the prompt surface is part of the product, not just documentation.

# tiaga_face_v0.1 Known Issues

## YAML Indentation Matters

External models sometimes return YAML with missing indentation.

This can cause:
- `behavior` to stop being a nested object,
- `face` to parse incorrectly,
- transient overlays to fail or behave like a base face.

Always normalize indentation before judging the formula itself.

## Root Documentation Encoding

`FACE_DSL_SYSTEM.md` may display garbled text in some terminal locales.

Treat the wiki pages and the newer prompt/analysis files as the safer references until that document is repaired.

## Prompt Surface Gap

The current app surface does not yet expose a first-class copyable canonical prompt.

That is a product gap because the main value proposition depends on users being able to move cleanly from natural-language request to LLM-generated DSL.

## Port Reuse On Local Server

If `node server.mjs` returns `EADDRINUSE`, the usual cause is that the server is already running on port `4173`.

In that case:
- open `http://127.0.0.1:4173`,
- or stop the existing process and restart.

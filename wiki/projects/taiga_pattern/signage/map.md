# signage Map

Parent project:
- `taiga_pattern`

Source repository:
- <https://github.com/kawaiiTaiga/taiga>

Tracked branch:
- `origin/main`

## Repository Layout

```text
/signage
  app.js
  index.html
  styles.css
  README.md
  hampter-signage-design.md
  signage-simulator-summary.md
```

## File Roles

- `app.js` - parser-driven signage runtime, preset definitions, selector matching, and canvas rendering.
- `index.html` - simulator shell and control panel.
- `styles.css` - signage UI styling.
- `README.md` - quick orientation and run instructions.
- `hampter-signage-design.md` - design note for the DSL and authoring model.
- `signage-simulator-summary.md` - implementation summary and architecture notes.

## Execution Notes

- Open `signage/index.html` directly in a browser for quick local inspection.
- A static file server is sufficient when a served URL is preferred.
- The simulator currently uses browser Canvas rather than a full text-layout engine.

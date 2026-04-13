# tiaga_face_v0.1 Design

## High-Level Philosophy

This project follows the HAMPTER idea of separating thinking from acting.

- The runtime is always alive.
- The LLM does not control the face frame-by-frame.
- The LLM outputs a behavior artifact: a formula DSL that the runtime evaluates every frame.
- The last valid behavior must keep running even without a live model connection.

The DSL is therefore a behavior description, not a pose snapshot.

## Architecture

### Runtime layer

`dsl-runtime.js` owns:
- DSL parsing,
- formula compilation,
- evaluation scope (`time`, `local_time`, helpers),
- compact-coordinate mapping,
- transient overlay timing,
- idle/base behavior state,
- evaluation helpers for testing.

### Rendering layer

`renderer.js` owns:
- WebGL2 setup,
- fragment shader source,
- eye rendering,
- final black-and-white compositing.

The renderer should receive numbers and draw. It should not become a story engine.

## DSL Model

There are two useful face-entry styles:

1. Direct low-level eye parameters.
2. `face.mode: compact`, which is the preferred control space.

Compact channels:
- `openness`
- `squint`
- `smile`
- `roundness`
- `slant`
- `asymmetry`
- optional `spacing`
- `gaze`
- `glow`
- `warmth`

The project currently assumes models can handle coordinate-like parameters if the prompt is precise enough.

## Time Model

This is not a keyframe system.

Each numeric field may be:
- a constant,
- or a formula evaluated every frame.

Important symbols:
- `time` - global time since the app started.
- `local_time` - time since the current transient started.
- `env(attack, hold, release)` - per-channel envelope.
- `decay(rate)` - local exponential decay.
- `progress(duration)` - normalized local progress.

The transient layer is separate from per-channel timing:
- `behavior.attack/hold/release` controls the whole overlay lifetime.
- `env(...)` lets one channel bloom and fade inside that lifetime.

## Design Position On Parameter Naming

This project no longer treats human readability as the top constraint.

The better rule is:
- coordinate precision first,
- prompt clarity second,
- human intuition third.

If a more coordinate-like basis is better for the LLM, that is acceptable as long as the documentation is strong.

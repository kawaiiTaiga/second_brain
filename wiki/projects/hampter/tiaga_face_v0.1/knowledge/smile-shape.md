# tiaga_face_v0.1 Smile Shape Notes

## Why Smile Was Hard

Most expressions in this project can be approximated by:
- an eye base shape,
- plus lid clipping,
- plus tilt and width changes.

Strong smile could not.

The repeated failure mode was:
- the eye narrowed,
- but it read as a sneer, frown, or sharp `^^`,
- instead of a soft rounded smile.

The root cause was geometric:
- lid-clipped eyes converge toward a flat or angular band,
- but the intended closed-eye smile is closer to two rounded parentheses rotated 90 degrees.

## Current Solution

The renderer now has a smile-specific shape regime.

At high enough smile activation:
- it computes a smile centerline (`smileCurve`),
- computes a band thickness (`smileThickness`),
- builds a smile band distance field (`smileBandDist`),
- and blends from the normal eye shape into that crescent-like band.

Important consequence:
- ordinary `HAPPY` should not live too deep in this regime,
- extreme smile can.

## Current Practical Rule

- Soft or ordinary happy:
  - medium `smile`
  - low `squint`
  - near-zero `slant`
  - high enough `openness`
- Strong closed-eye smile:
  - high `smile`
  - lower `openness`
  - modest `squint`
  - low `asymmetry`
  - near-zero `slant`

## Current Failure To Watch For

If a happy face starts to look like a joker grin or sneer, the likely causes are:
- `smile` too high for the intended expression,
- `squint` too high,
- `slant` too negative,
- or the smile renderer regime being entered too early.

Fix order:
1. lower the preset or formula values,
2. delay the smile-shape blend threshold,
3. only then reconsider geometry.

# rf-agent Testing And Validation

## Unit Test Status

- Full suite command:
  - `PYTHONPATH=src python3 -m unittest discover -s tests -v`
- Current observed passing count:
  - `33` tests after the `tx-validate` addition and TinySA connection refactor.

## Real TinySA Validation

The following checks were verified against real hardware on April 16, 2026:

- `rf info --port /dev/ttyACM0` succeeded and reported `tinySA Ultra`.
- `rf daemon status --json` reported a running daemon on `/dev/ttyACM0`.
- Narrow live scans around `2437 MHz` succeeded.
- `rf tx-validate` succeeded on a real emitter span and returned a structured judgment.

## Observed Live Result

The live `tx-validate` smoke run around the active `2437 MHz` signal reported:

- observed carrier near `2437785754 Hz`
- `operational_state: stable`
- `spectral_cleanliness: harmonics-visible`
- `overall_assessment: locked-but-spectrally-dirty`

## Validation Rules

- Do not claim a TinySA workflow works until it has been exercised on the real device.
- A passing unit suite is necessary but not sufficient for RF workflow changes.
- Use a live smoke pass after changes to serial transport, daemon reuse, locking, or high-level RF workflows.

# rf-agent Workflow Design

## Purpose

This page captures the durable design rule for how `rf-agent` should evolve for LLM use.

## Core Rule

The project should not grow by exposing many narrow TinySA wrappers. It should grow by giving the LLM a small number of strong task-level workflows and a skill that routes to them reliably.

## Current High-Level Workflow Set

- `rf tx-validate` - Full emitter validation for "is this transmitter OK?"
- `rf survey` - Multi-band discovery when the active band is unknown.
- `rf follow-peak` - Lock onto the strongest carrier inside a known band.
- `rf clean-check` - Harmonic and spur judgment for a known carrier.
- `rf track` - Stability and intermittence checks for a known span.
- `rf panel goal` - Goal-state TinySA front-panel control instead of low-level touch scripting.

## Durable Design Rules

- Add a new command only when the LLM would otherwise repeat the same fragile low-level sequence in the same order.
- Prefer prompt or skill routing changes when the problem is command selection, not task execution.
- Keep raw serial and panel primitives available as escape hatches, but do not make them the default path.
- Prefer structured judgment fields so later reasoning does not depend on parsing free-form text.

## Current Evidence

- The TinySA connection selection logic was factored into `src/rf_agent/tinysa_connection.py`.
- `rf tx-validate` was added as the first explicit LLM-oriented task command.
- The bundled `rf-master-agent` skill now routes transmitter-validation questions to `tx-validate` first and prefers fewer, stronger workflows overall.

## Related ADRs

- `docs/adr/0001-live-rf-agent-architecture.md`
- `docs/adr/0002-tinysa-daemon-and-locking.md`
- `docs/adr/0003-goal-based-panel-control.md`

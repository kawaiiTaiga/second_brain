# rf-agent Status

## Summary

`rf-agent` documents the Orange Pi focused `rf_agent` CLI maintained in the local `RF_station` working tree. The project is built for real TinySA operation, daemon-backed serial reuse, panel goal control, `tshark`-based packet capture, and structured high-level workflows that an LLM can use without hand-building low-level serial sequences.

## Start Here

If a new session needs to become productive quickly, read these in order:

1. `projects/rf/rf-agent/skills/session-start.md`
2. `projects/rf/rf-agent/map.md`
3. `projects/rf/rf-agent/knowledge/testing-and-validation.md`
4. `projects/rf/rf-agent/knowledge/workflow-design.md`

## Current State

- The codebase exposes live TinySA workflows including `tx-validate`, `survey`, `follow-peak`, `clean-check`, `track`, `scan`, and `panel goal`.
- TinySA connectivity is designed around daemon-backed serial reuse and command-ownership locking, with connection logic factored into `src/rf_agent/tinysa_connection.py`.
- The bundled `rf-master-agent` skill was updated so future LLM sessions prefer a few strong task-level workflows instead of chaining low-level commands.
- The local git repository exists on branch `main` with an initial commit, but no GitHub remote has been connected yet.
- Real hardware validation was completed against a `tinySA Ultra` on April 16, 2026, including `rf info`, daemon status, narrow live scans, and a live `tx-validate` run.

## Current Priorities

- Publish the local `rf-agent` repository to GitHub when repository creation is available.
- Keep the repo-bundled `skills/rf-master-agent/` copy aligned with the installed Codex skill.
- Re-run the real TinySA smoke checks after substantial RF workflow or transport changes.

## Next

- Create the planned GitHub repository for `rf-agent` and push `main`.
- Record the public repository URL in `knowledge/repository-access.md` once publication happens.
- Expand wiki knowledge when new RF workflows or hardware-specific quirks become durable.

## Decisions

- Prefer a few task-level workflows over many narrow serial wrappers.
- Treat real TinySA measurements as the source of truth for workflow validation.
- Keep daemon-based connection lifecycle management separate from command-ownership locking.
- Keep the TinySA front panel synchronized with the active measurement span.

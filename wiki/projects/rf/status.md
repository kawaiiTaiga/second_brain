# rf Status

## Summary

`rf` is the parent wiki project for radio/networking systems, topology bring-up, live measurement tooling, and wireless middleware. The currently documented child projects are `startopolgy10`, which captures the Fleet AirLink star-topology-10 work in the `communication` repository, and `rf-agent`, which captures the TinySA- and tshark-based `RF_station` measurement tool.

## Current State

- `startopolgy10` documents Fleet AirLink implementation state, test results, video/GUI routing, and networking guidance.
- `rf-agent` documents the Orange Pi based TinySA measurement CLI, the bundled `rf-master-agent` skill, and the current validation status for live hardware workflows.
- Parent-level RF knowledge currently focuses on keeping Linux networking/router responsibilities separate from application-level middleware.

## Child Projects

- `startopolgy10` - Fleet AirLink v0.1 scaffold, simulator, hwsim tests, video token routing, and GCS GUI work.
- `rf-agent` - Real TinySA control, daemon-backed sessions, panel goal control, packet capture, and LLM-oriented RF workflows.

## Next

- Keep the `rf-agent` child project synchronized with the local `RF_station` codebase as commands, tests, and publication state change.
- Add more RF child projects under `rf` instead of flattening them at top level.
- Keep parent-level wireless/networking guidance here when it applies across multiple related projects.

## Decisions

- `rf` is the parent node for wireless/topology work in the wiki.
- Use direct child folders for concrete codebases or deployment variants.
- Do not store credentials, private IP addresses, or personal machine paths in this public wiki.

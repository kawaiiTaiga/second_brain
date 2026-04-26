# hampter Status

## Summary

`hampter` is now the top-level project context for HAMPTER Local, the HAMPTER device SDK, and the formula-driven hardware behavior system around MCP-controllable devices.

## Current State

- Canonical app repository: <https://github.com/kawaiiTaiga/hampter-local>.
- Canonical device SDK repository: <https://github.com/kawaiiTaiga/hampter-device-sdk>.
- HAMPTER Local has moved from a Docker-first developer shape toward a standalone Windows app shape.
- The standalone app runs a local MQTT broker, MCP bridge, and Manager UI together so users do not need to start and stop Docker manually.
- The Manager UI is intended to absorb the older dashboard responsibilities instead of sending users to a separate dashboard surface.
- MCP control remains a core product requirement: the app is for humans, but LLMs must also be able to inspect, route, and control devices through MCP.
- A SHT40 temperature/humidity device and a LED ring device were validated end-to-end through OutPort to InPort routing.
- The key validated route was `temperature_c -> var_a`, with the LED firmware acknowledging the applied value through `ports/state`.

## Related Top-Level Projects

- `taiga_pattern` - a separate top-level wiki project that documents the `taiga` GitHub monorepo.

## Next

- Keep HAMPTER Local and Device SDK handoff notes in this project.
- Continue merging dashboard-only features into HAMPTER Local when they are part of the same user workflow.
- Treat device provisioning as an in-app connection-manager workflow: scan HAMPTER setup APs, let the user choose the device and Wi-Fi, then inject MQTT host/port automatically.
- For future device work, keep device-specific code in `src/modules/` and push shared runtime fixes into the device SDK.

## Decisions

- `hampter` and `taiga_pattern` are peer top-level projects in the wiki.
- The TAIGA monorepo is no longer filed under `hampter`.
- HAMPTER Local should be documented by GitHub URLs and canonical repo paths, not by one machine's local clone paths.
- Standalone app distribution is the preferred user-facing path; Docker remains useful as a development/reference topology.


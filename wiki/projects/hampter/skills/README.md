# hampter Skills

Read this page after [../index.md](../index.md). This is the parent-level workflow hub for HAMPTER.

## Current State

- HAMPTER work should start from the canonical GitHub repositories listed in [../map.md](../map.md).
- For per-device firmware behavior, edit the SDK/project `src/modules/` area first.
- For shared MQTT, provisioning, command, port parsing, or acknowledgement behavior, fix the shared runtime in the device SDK and keep downstream device projects synchronized.
- For route debugging, always verify both sides:
  - device serial logs should show the received MQTT topic and applied InPort value;
  - HAMPTER Local `/port-debug` should show `last_bridge_value`, `last_device_value`, and `last_device_accepted`.
- For user-facing app work, prefer improving HAMPTER Local itself rather than sending users into a separate dashboard.
- For MCP work, keep both human UI and LLM control paths working. The app should be controllable through Manager UI and through MCP tools/resources.

## Rules

- Keep parent-level process here.
- Keep project-specific workflow inside each child project's `skills/` folder.
- Preserve the `hampter -> <name>` hierarchy in the wiki.
- Do not commit local runtime state such as generated device lists, routing config with private device data, projection config with user edits, virtual tool state, Wi-Fi passwords, or tokens.
- Use GitHub URLs when documenting file locations.

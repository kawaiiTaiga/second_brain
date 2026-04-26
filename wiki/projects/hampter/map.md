# hampter Map

## Wiki Hierarchy

```text
wiki/
  projects/
    hampter/
      status.md
      map.md
      skills/
      knowledge/
```

## Canonical Repositories

- HAMPTER Local: <https://github.com/kawaiiTaiga/hampter-local>
- HAMPTER Device SDK: <https://github.com/kawaiiTaiga/hampter-device-sdk>
- Persistent wiki: <https://github.com/kawaiiTaiga/second_brain/tree/main/wiki/projects/hampter>

## HAMPTER Local Repository Map

Use GitHub paths as the canonical location references:

- <https://github.com/kawaiiTaiga/hampter-local/tree/main/HampterLocalApp> - Windows desktop app shell and user-facing Manager UI host.
- <https://github.com/kawaiiTaiga/hampter-local/tree/main/bridge_mcp> - MCP bridge server, HTTP APIs, MCP tools, device registry, projection, and signal control.
- <https://github.com/kawaiiTaiga/hampter-local/tree/main/bridge_v2> - newer runtime composition/services around device sessions, commands, and routing.
- <https://github.com/kawaiiTaiga/hampter-local/tree/main/mcp_manager> - Manager UI/backend surface for local device and configuration management.
- <https://github.com/kawaiiTaiga/hampter-local/tree/main/config> - example config files and runtime config shape. Real generated config JSON is local state and should stay out of git.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/run_standalone.py> - standalone process orchestrator for broker, bridge, and manager.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/run_standalone.ps1> - PowerShell entry point for local standalone runs.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/hampter_local_broker.py> - built-in local MQTT broker fallback.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/hampter_mcp_stdio_proxy.py> - stdio proxy for local MCP clients such as Claude Desktop and Codex-style setups.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/port_routing.py> - legacy-compatible PortStore/RoutingMatrix/PortRouter implementation used for OutPort to InPort signal routing.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/package_hampter_local.ps1> - fast local packaging path for `HAMPTER Local.exe`.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/make_hampter_release.ps1> - release zip builder.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/STANDALONE.md> - standalone running and packaging guide.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/DEVELOPMENT_AND_RELEASE.md> - development and release checklist.

## Device SDK Repository Map

- <https://github.com/kawaiiTaiga/hampter-device-sdk/tree/main/esp32_c3_dev> - ESP32-C3 PlatformIO SDK template.
- <https://github.com/kawaiiTaiga/hampter-device-sdk/tree/main/esp32_c3_dev/src/modules> - device-specific tools, ports, and hardware behavior. Prefer changing this area for per-device work.
- <https://github.com/kawaiiTaiga/hampter-device-sdk/tree/main/esp32_c3_dev/src/apps/HAMPTER> - shared runtime entry point for Wi-Fi, provisioning, MQTT, tools, and ports.
- <https://github.com/kawaiiTaiga/hampter-device-sdk/tree/main/esp32_c3_dev/lib/port> - shared port registry runtime, including InPort parsing and `ports/state` acknowledgement behavior.
- <https://github.com/kawaiiTaiga/hampter-device-sdk/tree/main/esp32_c3_dev/lib/mcp-sdk> - shared MCP/device command runtime.
- <https://github.com/kawaiiTaiga/hampter-device-sdk/blob/main/readme.md> - SDK usage, port system, and troubleshooting guide.

## Runtime Shape

Standalone HAMPTER Local mirrors the old Docker topology:

- MQTT broker: `0.0.0.0:1883` for devices on the same LAN.
- Bridge/MCP: `http://127.0.0.1:8083`, with Streamable HTTP MCP at `/mcp` and SSE at `/sse`.
- Manager UI/API: `http://127.0.0.1:8084`.
- PC browser and local Manager can use `127.0.0.1`; devices must use the PC's LAN IP as MQTT host.

## Build And Distribution

- Fast local package: run `package_hampter_local.ps1` from the HAMPTER Local repo.
- Release package: run `make_hampter_release.ps1` from the HAMPTER Local repo.
- Release artifact shape: `HAMPTER-Local-<version>-win-x64.zip`.
- Current dev release reference: <https://github.com/kawaiiTaiga/hampter-local/releases/tag/v0.1.0-dev>.
- Windows/PlatformIO builds can fail when the project path contains non-ASCII characters. Use an ASCII-only checkout path or a temporary ASCII junction for build/upload work.

## Role Of This Top-Level Project

- Parent-level HAMPTER context belongs here.
- TAIGA monorepo implementation details no longer live under this folder.
- Use sibling top-level project folders when a project deserves its own hub and hierarchy.

## Notes

- Keep HAMPTER-wide philosophy or conventions at this level.
- The TAIGA monorepo now lives at `wiki/projects/taiga_pattern/`.
- Do not record private local clone paths as canonical references. Use GitHub URLs and repo-relative paths.


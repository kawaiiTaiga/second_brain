# HAMPTER Local Standalone Architecture

## Canonical Repository

- Repository: <https://github.com/kawaiiTaiga/hampter-local>
- Standalone guide: <https://github.com/kawaiiTaiga/hampter-local/blob/main/STANDALONE.md>
- Development/release guide: <https://github.com/kawaiiTaiga/hampter-local/blob/main/DEVELOPMENT_AND_RELEASE.md>

## Product Direction

HAMPTER Local is moving from a Docker-first developer setup into a user-facing standalone desktop app. The user should not need to manually start/stop Docker just to use local devices.

The standalone app should be the main surface for:

- device discovery and provisioning;
- Manager UI workflows;
- dashboard-like device control and routing;
- MCP client connection setup;
- local broker/bridge/manager lifecycle.

`OPEN DASHBOARD` is not expected to remain a separate primary workflow long term. Alias, hiding/projection, routing, and device control should live inside HAMPTER Local when they are part of the same local user journey.

## Runtime Services

Standalone HAMPTER Local mirrors Docker's service shape with local processes:

- MQTT broker on `0.0.0.0:1883`, using Mosquitto or the built-in fallback broker.
- MCP bridge on `http://127.0.0.1:8083`.
- Manager on `http://127.0.0.1:8084`.

Important endpoints:

- `http://127.0.0.1:8083/healthz` - bridge health.
- `http://127.0.0.1:8083/mcp` - Streamable HTTP MCP endpoint.
- `http://127.0.0.1:8083/sse` - SSE MCP endpoint.
- `http://127.0.0.1:8083/signals` - LLM-friendly signal source/target/routes snapshot.
- `http://127.0.0.1:8083/port-debug` - live port telemetry and route debugging.
- `http://127.0.0.1:8084` - Manager UI.

## Key Repo Paths

- <https://github.com/kawaiiTaiga/hampter-local/tree/main/HampterLocalApp> - Windows app shell.
- <https://github.com/kawaiiTaiga/hampter-local/tree/main/bridge_mcp> - FastAPI/MCP bridge, tools, device registry, projection, signals API.
- <https://github.com/kawaiiTaiga/hampter-local/tree/main/bridge_v2> - service composition for sessions, commands, and routing.
- <https://github.com/kawaiiTaiga/hampter-local/tree/main/mcp_manager> - Manager UI/backend.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/run_standalone.py> - process orchestrator for local broker, bridge, and manager.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/hampter_local_broker.py> - built-in broker fallback.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/hampter_mcp_stdio_proxy.py> - stdio MCP proxy for local MCP clients.
- <https://github.com/kawaiiTaiga/hampter-local/blob/main/port_routing.py> - port store, routing matrix, transform, and async router.

## MCP Connection Model

Claude Desktop and Codex-style local MCP clients can use stdio/SSE/HTTP locally depending on client support. ChatGPT remote MCP cannot connect directly to `localhost`; it needs a public HTTPS URL for the bridge's `/mcp` endpoint.

The app should provide a connection-oriented UI rather than raw endpoint text first. The desired direction is:

- detect likely clients such as Claude Desktop, Codex/OpenAI tooling, ChatGPT remote MCP, and generic stdio/Streamable HTTP clients;
- show each as a connection card or target;
- let the user install or copy the right config with one clear action;
- keep service-specific differences visible without making the app feel like a developer-only settings panel.

## Packaging

Fast local package:

```powershell
.\package_hampter_local.ps1
```

Release zip:

```powershell
.\make_hampter_release.ps1
```

Current development release reference:

- <https://github.com/kawaiiTaiga/hampter-local/releases/tag/v0.1.0-dev>

Do not commit generated runtime state or bundled build output. Keep generated device/config state local and keep sample config in git.

# Port Routing And InPort Acknowledgement

## Solved Issue

A SHT40 temperature/humidity device was routed into a LED ring device, but the LED appeared to stay at the minimum/default state. The bridge believed the route was working because it was dispatching `temperature_c -> var_a`, but the LED firmware was using a stale runtime that rejected incoming `ports/set` messages.

The serial symptom on the stale LED firmware was:

```text
[MQTT] RX topic='mcp/dev/dev-8B52D8/ports/set' (35/36 bytes)
[MQTT] ports.set missing 'port'
```

The fix was not in the LED-specific `src/modules` code. The LED project needed the current shared runtime from the HAMPTER Device SDK.

## Canonical Runtime Expectations

Use the current SDK runtime from:

- <https://github.com/kawaiiTaiga/hampter-device-sdk/tree/main/esp32_c3_dev/lib/port>
- <https://github.com/kawaiiTaiga/hampter-device-sdk/tree/main/esp32_c3_dev/src/apps/HAMPTER>
- <https://github.com/kawaiiTaiga/hampter-device-sdk/tree/main/esp32_c3_dev/lib/mcp-sdk>

The runtime should:

- parse `ports/set` payloads through `PortRegistry::parseInPortSetPayload(...)`;
- accept `port`, `port_name`, `name`, or a `target` path such as `dev-XXXX/var_a`;
- call `PortRegistry::handleInPortSet(portName, value, "mqtt.ports.set", true)`;
- publish `mcp/dev/{id}/ports/state` after applying the value;
- expose the device-applied value back to HAMPTER Local so `/port-debug` can show `last_device_value` and `last_device_accepted`.

## Validated Flow

Observed device pair:

- Sensor device: `dev-D3A7C4`.
- LED device: `dev-8B52D8`.
- Source: `dev-D3A7C4/temperature_c`.
- Target: `dev-8B52D8/var_a`.
- Transform: direct/raw Celsius value.

After runtime sync and upload, LED serial logs showed:

```text
[MQTT] RX topic='mcp/dev/dev-8B52D8/ports/set' (36 bytes)
[PORT] InPort 'var_a' set to 25.123
```

Bridge `/port-debug` showed both sides:

- `last_bridge_value` around `25.1`.
- `last_device_value` around `25.1`.
- `last_device_accepted: true`.
- `last_device_source: mqtt.ports.set`.

This confirms the route is not merely dispatched by the bridge; the device actually applied and acknowledged the InPort value.

## LED Thermometer Pattern

The LED device had a persistent slot named `SHT40 Thermometer`. The slot maps Celsius directly through `var_a`, with a rough 18 C to 32 C range:

- normalized temperature: `max(0,min(1,(var_a-18)/14))`
- hue shifts from cooler to warmer as temperature rises
- brightness fills a ring segment according to the normalized temperature

The route intentionally sends raw Celsius into `var_a`; the pattern expression performs the normalization.

## Debugging Checklist

When a route looks alive in HAMPTER Local but hardware does not respond:

1. Check `/signals` for source, target, and route summary.
2. Check `/port-debug` for `last_bridge_value`, `last_device_value`, and `last_device_accepted`.
3. Watch device serial for received `ports/set` and applied InPort lines.
4. If the device logs parser errors, sync shared runtime files from the SDK instead of changing `src/modules`.
5. If the device applies values but LEDs still look wrong, debug LED wiring, LED pin/type, active slot, or formula rendering.

## PlatformIO Path Note

Windows/PlatformIO builds can fail when a project path contains non-ASCII characters. Build from an ASCII-only checkout path or use an ASCII-only junction when compiling/uploading firmware.

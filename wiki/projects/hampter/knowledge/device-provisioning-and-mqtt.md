# Device Provisioning And MQTT

## Core Rule

During provisioning, the MQTT host shown to the device must be the PC's LAN IP on the same Wi-Fi, not `127.0.0.1`.

- PC browser and Manager UI: `127.0.0.1:8084`.
- MCP bridge from the PC: `127.0.0.1:8083`.
- Device MQTT setting: `<PC_LAN_IP>:1883`.

From the device's point of view, `127.0.0.1` means the device itself, not the PC.

## Docker Versus Standalone

Docker and standalone should be compatible from the device's perspective:

- Docker publishes MQTT `1883:1883`.
- Standalone binds the local broker to `0.0.0.0:1883`.
- In both cases, devices on the same LAN should connect to the PC's LAN IP on port `1883`.

This is why a device that previously connected to the Docker version should be able to connect to HAMPTER Local standalone if the MQTT host is the same PC LAN IP and the broker is reachable.

## Desired In-App Provisioning Flow

The preferred UX is a Connection Manager inside HAMPTER Local:

1. User opens Connection Manager.
2. App continuously scans for setup APs such as `MCP-SETUP-*`, `HAMPTER-*`, or `HAMPTER_*`.
3. User selects the setup device.
4. User chooses the target Wi-Fi and enters the Wi-Fi password.
5. App fills MQTT host/port automatically using the PC LAN IP and `1883`.
6. App connects to the setup AP, posts provisioning data to the device, reconnects the PC to the target Wi-Fi, and waits for the device to appear in the bridge.

This avoids making users manually move between Wi-Fi settings, browser setup pages, and MQTT host discovery.

## Relevant Repo Paths

- Connection manager guide: <https://github.com/kawaiiTaiga/hampter-local/blob/main/STANDALONE.md>
- Standalone runner: <https://github.com/kawaiiTaiga/hampter-local/blob/main/run_standalone.py>
- Device provisioning runtime: <https://github.com/kawaiiTaiga/hampter-device-sdk/tree/main/esp32_c3_dev/lib/provisioning>
- Device app runtime: <https://github.com/kawaiiTaiga/hampter-device-sdk/tree/main/esp32_c3_dev/src/apps/HAMPTER>

## Public Wiki Safety

Do not record Wi-Fi passwords, claim tokens, secret tokens, or private device credentials in this public wiki. Record only the shape of the flow and non-secret endpoint conventions.

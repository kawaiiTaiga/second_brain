# startopolgy10 Implementation History

## Initial Scaffold

The repository was turned from specification-only state into a runnable Python scaffold with:

- `pyproject.toml`
- `proto/airlink.xml`
- `src/fleet_airlink/common/`
- `src/fleet_airlink/gcs_linkd/main.py`
- `src/fleet_airlink/air_linkd/main.py`
- `configs/`
- `tests/`
- `IMPLEMENTATION_TODO.md`

The current wire format is a JSON datagram scaffold that preserves the intended message semantics while deferring full MAVLink code generation/signing integration.

## Logical Simulator

A logical simulator was added in `src/fleet_airlink/sim/main.py` so the scheduling/state behavior could be tested without hardware.

This covers:

- multi-drone activation
- packet loss simulation
- emergency injection
- beacon blackout / `LOST_BEACON`

## mac80211_hwsim Integration

`mac80211_hwsim` support was enabled for the current kernel, built, and installed. Integration work then added `scripts/run_fleet_hwsim.sh` and related docs so the stack could run under:

- `mac80211_hwsim`
- `hostapd`
- `wpa_supplicant`
- Linux network namespaces

A durable gotcha from this work is that the hwsim script should reuse the default `wlanX` interfaces created by hwsim, not try to create extra interfaces on top.

## Video Token and Routing Work

Video gating was added on the drone side and routing/fan-out was added on the GCS side.

Main results:

- drone local video ingress listener
- owner-only video send gate
- queue limit and drop accounting
- live video forward for the selected owner stream
- preview fan-out so the GUI can show thumbnails for multiple drones

## Runtime Control API

The GCS daemon now exposes a minimal HTTP control API for:

- `GET /state`
- `POST /focus`
- `POST /video-owner`
- `POST /route`

This lets operators or GUI code change focus and video ownership at runtime without restarting processes.

## GUI and Helper Scripts

A Tk + ffmpeg GUI was added for:

- per-drone thumbnails from preview fan-out ports
- larger live view for the currently selected drone
- route switching by selecting a drone in the GUI

Supporting helper scripts were added for:

- ffmpeg send/receive
- GStreamer send/receive
- local video demo bring-up
- one-shot demo + GUI bring-up

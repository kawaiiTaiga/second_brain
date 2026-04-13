# startopolgy10 Status

Parent project:
- `rf`

## Summary

`startopolgy10` documents the Fleet AirLink v0.1 implementation work for a GCS-centered star topology with up to 10 drones, based on `whattodo.md` in the `communication` repository. The spelling `startopolgy10` is preserved to match the requested wiki path.

## Start Here

If a new session starts and the agent needs to become productive quickly, read these in order:

1. `projects/rf/subprojects/startopolgy10/skills/session-start.md`
2. `projects/rf/subprojects/startopolgy10/map.md`
3. `projects/rf/subprojects/startopolgy10/knowledge/runtime-startup.md`
4. `projects/rf/subprojects/startopolgy10/knowledge/known-gaps.md`

Use the local demo and test commands from those pages instead of assuming any process is already running.

## Current State

- A Python 3.10 stdlib scaffold exists for `common`, `gcs_linkd`, `air_linkd`, and `sim`.
- `proto/airlink.xml`, example configs, README, TODO breakdown, and tests exist.
- Logical simulation works for multi-drone, loss, blackout, and emergency scenarios.
- `mac80211_hwsim` support was built for the current kernel and integrated into `scripts/run_fleet_hwsim.sh`.
- Video token routing is implemented: per-drone ingress, owner-only live forward, preview fan-out, and queue gating.
- A GCS runtime control API exists for `/state`, `/focus`, `/video-owner`, and `/route`.
- A Tk + ffmpeg GCS GUI exists for thumbnails and selected live video.
- Local demo scripts exist for video routing and GUI bring-up.
- No real remote node has been configured yet from this host because reachable SSH/network path to the target node was not confirmed.

## Current Priorities

- Connect a real remote node after IP routing and SSH reachability are confirmed.
- Implement emergency retransmission and ACK retry logic.
- Replace the JSON datagram scaffold with real MAVLink 2 code generation/signing integration.
- Decide whether AP/router configuration should live in this repository or in external system tooling.

## Next

- Bring up one real non-local node using actual LAN addresses instead of loopback defaults.
- Validate two-radio backhaul/AP operation on hardware.
- Add retransmission tests for emergency behavior under loss.
- If the GUI evolves further, add telemetry overlays and operator controls.

## Decisions

- v1 remains star topology only: GCS as center, no mesh and no direct drone-to-drone traffic.
- TDMA is applied only to drone-to-GCS uplink shaping.
- Only one drone owns the live video stream at a time.
- GCS preview fan-out was added so the GUI can show thumbnails for multiple drones while still keeping a single-owner live stream.
- Linux networking must provide reachability first; the middleware is not the router.

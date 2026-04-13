# startopolgy10 Map

Parent project:
- `rf`

Repository root:
- `communication/`

Primary spec and planning docs:
- `whattodo.md` - original Fleet AirLink v0.1 specification.
- `IMPLEMENTATION_TODO.md` - execution-oriented breakdown of the spec.
- `TEST_REPORT.md` - simulation and hwsim validation summary.
- `README.md` - current user-facing execution guide.

## Repository Layout

```text
/
  configs/
    gcs.example.json
    drone-1.example.json
    dev-signing.key
  kernel-build-backups/
    config-5.10.160-rockchip-rk3588-mesh2-before-mac80211_hwsim
  proto/
    airlink.xml
  scripts/
    run_fleet_hwsim.sh
    demo_video_token_local.sh
    run_gcs_gui_demo.sh
    video_sender_ffmpeg.sh
    video_sender_gst.sh
    video_receiver_ffplay.sh
    video_receiver_ffmpeg.sh
    video_receiver_gst.sh
  src/fleet_airlink/
    common/
    gcs_linkd/
    air_linkd/
    sim/
    gcs_gui/
  tests/
    hwsim/
    test_config.py
    test_control_api.py
    test_gcs_gui.py
    test_protocol.py
    test_simulation.py
    test_state.py
    test_video.py
```

## Key Runtime Files

- `src/fleet_airlink/common/config.py` - typed config models and validation.
- `src/fleet_airlink/common/protocol.py` - current datagram wire format and custom message helpers.
- `src/fleet_airlink/common/state.py` - GCS/drone state machines.
- `src/fleet_airlink/common/timebase.py` - monotonic clock and timesync helpers.
- `src/fleet_airlink/gcs_linkd/main.py` - GCS control plane, video fan-out, and control API.
- `src/fleet_airlink/air_linkd/main.py` - drone control plane, slot send logic, and video gate.
- `src/fleet_airlink/sim/main.py` - logical simulator.
- `src/fleet_airlink/gcs_gui/main.py` - thumbnail/live view GUI client.

## Port and Stream Conventions

- AirLink control: UDP `14600`
- MAVLink data proxy: UDP `14550`
- GCS per-sysid video receive: UDP `5600 + sysid`
- Demo-only drone local video ingress: UDP `5700 + sysid`
- GCS live forwarded video: UDP `6600 + sysid`
- GCS preview fan-out for thumbnails: UDP `7600 + sysid`
- GCS control API: HTTP `17000`

## Execution Notes

- Local daemon bring-up:
  - `PYTHONPATH=src python3 -m fleet_airlink.gcs_linkd.main --config configs/gcs.example.json`
  - `PYTHONPATH=src python3 -m fleet_airlink.air_linkd.main --config configs/drone-1.example.json`
- Local video demo:
  - `./scripts/demo_video_token_local.sh`
- Local GUI + demo launcher:
  - `./scripts/run_gcs_gui_demo.sh`
- Logical tests:
  - `PYTHONPATH=src python3 -m unittest discover -s tests -v`
- hwsim preflight:
  - `./scripts/run_fleet_hwsim.sh --preflight`

## Related Wiki Pages

- `wiki/projects/rf/knowledge/router-vs-middleware.md` - parent-level boundary between Linux networking and middleware.
- `wiki/projects/rf/subprojects/startopolgy10/knowledge/testing-and-validation.md` - what has actually been validated.
- `wiki/projects/rf/subprojects/startopolgy10/knowledge/networking-and-node-onboarding.md` - how to move from loopback demo to real nodes.

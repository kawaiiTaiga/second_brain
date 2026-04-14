# startopolgy10 Video Routing and GUI

## Routing Model

The video path is currently split into three stages:

1. local sender to `air-linkd`
2. drone uplink from `air-linkd` to `gcs-linkd`
3. GCS fan-out from `gcs-linkd` to preview and live consumer ports

## Drone-Side Rules

`air-linkd` only accepts/sends video when all of the following are true:

- the drone is the current `video_owner_sysid`
- a valid video window is active
- timesync is stable
- the drone is not in `LOST_BEACON` or `FAILSAFE`

It also enforces queue limits and drop accounting.

## GCS-Side Rules

`gcs-linkd` now does two things with incoming per-drone video packets:

- always mirror each drone to the preview fan-out port (`7600 + sysid` by current convention)
- only forward the current owner to the live consumer port (`6600 + sysid` by current convention)

This is what enables thumbnails for multiple drones while keeping the live-view policy at one owner stream.

## Control API and GUI Behavior

The GUI polls the control API and uses:

- `/state` to discover active drones and counters
- `/route` to set both `focus_sysid` and `video_owner_sysid`

The GUI uses:

- preview ports for thumbnails
- live ports for the selected drone's large view

## Helper Scripts

Relevant scripts:

- `scripts/video_sender_ffmpeg.sh`
- `scripts/video_sender_gst.sh`
- `scripts/video_receiver_ffplay.sh`
- `scripts/video_receiver_ffmpeg.sh`
- `scripts/video_receiver_gst.sh`
- `scripts/demo_video_token_local.sh`
- `scripts/run_gcs_gui_demo.sh`

## Durable Local-Demo Notes

- Local single-machine demos must separate drone local ingress ports from GCS receive ports.
- The ffmpeg receiver helper now forces overwrite (`-y`) so short smoke captures do not stall on pre-existing files.
- The GStreamer sender uses `h264parse config-interval=-1` to make mid-stream join behavior more robust.

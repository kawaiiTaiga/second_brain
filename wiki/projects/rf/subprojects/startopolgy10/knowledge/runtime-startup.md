# startopolgy10 Runtime Startup

## Purpose

This page is the quick operating checklist for starting useful work right away in a fresh session.

## Safe Baseline

Assume nothing is already running. Start by confirming process state and then choose one of the startup paths below.

Recommended initial checks:

```bash
ps -ef | grep -E 'fleet_airlink\.(gcs_linkd|air_linkd|gcs_gui)|demo_video_token_local|run_gcs_gui_demo' | grep -v grep
PYTHONPATH=src python3 -m unittest discover -s tests -v
```

## Path 1: Local Single-Machine Demo

Use this when the goal is to validate core control/video behavior quickly on one host.

```bash
./scripts/demo_video_token_local.sh
```

Expected result:
- local GCS + 2 drones start
- ffmpeg senders inject test video
- `/state` changes as focus/video owner moves from drone 1 to drone 2

## Path 2: Local GUI Demo

Use this when the goal is operator-facing validation.

```bash
./scripts/run_gcs_gui_demo.sh
```

Expected result:
- demo stack starts first
- GUI opens after the GCS API becomes reachable
- thumbnails come from preview fan-out ports
- selected live video comes from live forward ports

## Path 3: Direct Daemon Bring-up

Use this when debugging the daemons without the helper scripts.

```bash
PYTHONPATH=src python3 -m fleet_airlink.gcs_linkd.main --config configs/gcs.example.json
PYTHONPATH=src python3 -m fleet_airlink.air_linkd.main --config configs/drone-1.example.json
```

Then inspect:

```bash
curl -s http://127.0.0.1:17000/state
```

## Path 4: hwsim Preflight

Use this before attempting namespace-based wireless integration runs.

```bash
./scripts/run_fleet_hwsim.sh --preflight
```

If preflight passes, a longer hwsim run can follow.

## When Not To Use These Paths

- Do not use local demo configs as-is for real multi-node deployment.
- Do not try GUI startup before the control API exists.
- Do not diagnose remote-node onboarding until ping/SSH/routing are confirmed.

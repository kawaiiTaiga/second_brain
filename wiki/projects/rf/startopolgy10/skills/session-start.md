# startopolgy10 Session Start

Parent project:
- `rf`

Use this page when a new session starts and the agent should be able to work immediately without re-deriving project state from chat history.

## Repository

- Shared wiki repo: `kawaiiTaiga/second_brain`
- HTTPS clone URL: `https://github.com/kawaiiTaiga/second_brain.git`
- Project path inside the wiki: `wiki/projects/rf/startopolgy10/`
- Detailed reference: `projects/rf/startopolgy10/knowledge/repository-access.md`

## Read Order

Read these pages in order:

1. `projects/rf/startopolgy10/status.md`
2. `projects/rf/startopolgy10/map.md`
3. `projects/rf/startopolgy10/knowledge/runtime-startup.md`
4. `projects/rf/startopolgy10/knowledge/known-gaps.md`
5. task-specific knowledge pages only if needed

## Default Assumptions

Start with these assumptions unless the live environment proves otherwise:

- no daemons are running yet
- the GCS control API is not guaranteed to be up
- local single-machine demos use loopback-friendly configs and helper scripts
- real remote-node work requires actual LAN routing and is not implied by the local demo
- Linux networking is still responsible for AP/router reachability

## Fastest Useful Paths

### If the task is understanding current implementation

Read:
- `status.md`
- `map.md`
- `knowledge/implementation-history.md`
- `knowledge/testing-and-validation.md`

### If the task is running something immediately on one machine

Use:
- `knowledge/runtime-startup.md`
- `./scripts/demo_video_token_local.sh`
- `./scripts/run_gcs_gui_demo.sh`

### If the task is real hardware or another node

Read:
- `knowledge/networking-and-node-onboarding.md`
- `projects/rf/knowledge/router-vs-middleware.md`
- `knowledge/rf-power-and-antenna-guidance.md`

### If the task is video or GUI related

Read:
- `knowledge/video-routing-and-gui.md`

## First Commands To Run

Use these as the initial baseline checks:

```bash
PYTHONPATH=src python3 -m unittest discover -s tests -v
./scripts/demo_video_token_local.sh
./scripts/run_gcs_gui_demo.sh
./scripts/run_fleet_hwsim.sh --preflight
```

## Immediate Warnings

- Do not assume a remote node is reachable just because its IP is known.
- Do not assume the GUI can start unless the GCS API is already up.
- Do not assume `fleet_airlink` itself creates AP/router behavior.
- Do not start debugging middleware before checking basic reachability and process state.

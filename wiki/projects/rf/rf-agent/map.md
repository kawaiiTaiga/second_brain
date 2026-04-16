# rf-agent Map

Repository root:
- Local working tree folder name: `RF_station`

Python package and invocation:
- Package name: `rf_agent`
- Preferred command shape: `PYTHONPATH=src python3 -m rf_agent ...`

Primary docs:
- `README.md` - GitHub-oriented overview, install, quick start, workflow routing, and smoke tests.
- `rf-agent-spec.md` - Project specification and intent.
- `docs/adr/0001-live-rf-agent-architecture.md` - Live-hardware-first architecture decisions.
- `docs/adr/0002-tinysa-daemon-and-locking.md` - Separation of connection lifecycle and command locking.
- `docs/adr/0003-goal-based-panel-control.md` - Goal-based TinySA panel control rationale.

## Repository Layout

```text
/
  config.example.yaml
  README.md
  docs/
    adr/
  scripts/
    install_codex_skill.sh
    manual_tinysa_track.py
  skills/
    rf-master-agent/
  src/rf_agent/
    cli.py
    tinysa.py
    tinysa_connection.py
    tinysa_daemon.py
    analyze.py
    net_tshark.py
    rf_utils.py
  tests/
    test_cli_tinysa_actions.py
    test_tinysa_connection.py
    test_tinysa_daemon.py
    test_tinysa.py
    test_analyze.py
```

## Key Runtime Files

- `src/rf_agent/cli.py` - CLI entry point and high-level RF workflow commands.
- `src/rf_agent/tinysa_connection.py` - Runtime selection logic for direct TinySA access versus daemon reuse.
- `src/rf_agent/tinysa_daemon.py` - Persistent TinySA daemon implementation.
- `src/rf_agent/tinysa.py` - TinySA transport and command helpers.
- `src/rf_agent/analyze.py` - RF plus network artifact correlation.
- `src/rf_agent/net_tshark.py` - Packet capture and summary helpers.
- `skills/rf-master-agent/SKILL.md` - Repo-bundled Codex skill for high-level RF operation.
- `tests/test_cli_tinysa_actions.py` - CLI workflow tests, including `tx-validate`.
- `tests/test_tinysa_connection.py` - Direct tests for TinySA connection selection and daemon fallback behavior.

## Execution Notes

- Full test suite:
  - `PYTHONPATH=src python3 -m unittest discover -s tests -v`
- TinySA connectivity:
  - `PYTHONPATH=src python3 -m rf_agent rf info --port /dev/ttyACM0`
- Daemon status:
  - `PYTHONPATH=src python3 -m rf_agent rf daemon status --json`
- Full validation workflow:
  - `PYTHONPATH=src python3 -m rf_agent rf tx-validate -s 2.4GHz -e 2.5GHz -d 10 --port /dev/ttyACM0 --json`

## Related Wiki Pages

- `wiki/projects/rf/rf-agent/knowledge/repository-access.md` - Local repository state and future publication target.
- `wiki/projects/rf/rf-agent/knowledge/testing-and-validation.md` - What has actually been validated on unit tests and real hardware.
- `wiki/projects/rf/rf-agent/knowledge/workflow-design.md` - Why the project prefers high-level workflows for LLM use.

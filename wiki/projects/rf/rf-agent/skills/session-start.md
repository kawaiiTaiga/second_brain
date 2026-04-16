# rf-agent Session Start

Read this page first when a new session needs to work on the `rf-agent` codebase quickly.

## Read Order

1. `projects/rf/rf-agent/status.md`
2. `projects/rf/rf-agent/map.md`
3. `projects/rf/rf-agent/knowledge/testing-and-validation.md`
4. `projects/rf/rf-agent/knowledge/workflow-design.md`
5. `projects/rf/rf-agent/knowledge/repository-access.md`

## Immediate Checks

- Confirm the local repository is the `RF_station` working tree and that `main` is clean before making new changes.
- Use `PYTHONPATH=src python3 -m rf_agent --help` if command availability needs a quick sanity check.
- For real TinySA work, verify `rf info` and daemon status before assuming the device is reachable.

## Workflow Bias

- For emitter judgment, prefer `rf tx-validate` before manually chaining `recover`, `follow-peak`, `track`, and `clean-check`.
- Use `rf survey` when the active band is not known.
- Use `rf follow-peak` when the band is known but the carrier inside it is not.
- Use `rf clean-check` only when the carrier is already known and the task is specifically cleanliness.
- Use `rf track` when the span is known and the question is stability or intermittence.

## Publication Reminder

- This project has local git history but no public repository URL yet.
- If GitHub publication happens, update `knowledge/repository-access.md` in the same pass.

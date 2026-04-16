# rf-agent Skills

Read this page after [../index.md](../index.md). This is the local workflow hub for `rf-agent`.

## Deep Pages

- `session-start.md` is the first page a new session should read.
- Treat it as the handoff page that gets an agent from zero context to productive context quickly.

## Rules

- Read `status.md` first, then `map.md`, then the specific knowledge pages needed for the task.
- Prefer `PYTHONPATH=src python3 -m rf_agent ...` from the repository root.
- Prefer the highest-level RF workflow that matches the task instead of chaining low-level steps.
- Validate meaningful RF changes with `python3 -m unittest discover -s tests -v`, then re-run real TinySA smoke checks when the change could affect hardware behavior.
- Keep the repo-bundled `skills/rf-master-agent/` copy synchronized with the installed Codex skill when routing rules change.
- Keep private serial paths, credentials, and machine-specific details out of the public wiki unless the exact value is safe and operationally required.
- File durable hardware quirks, workflow findings, and publication changes into `knowledge/` instead of leaving them only in chat history.

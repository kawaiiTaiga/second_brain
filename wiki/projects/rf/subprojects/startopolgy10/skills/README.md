# startopolgy10 Skills

Parent project:
- `rf`

Use this folder for repeatable workflows that govern how the Fleet AirLink star-topology work should be maintained.

## Start Here

- `session-start.md` is the first page a new session should read.
- Treat it as the handoff page that gets an agent from zero context to productive context quickly.

## Working Rules

- Read `status.md` first, then `map.md`, then the specific knowledge pages needed for the task.
- Keep local single-machine demo assumptions separate from real multi-node deployment guidance.
- Before attempting remote-node setup, verify ping, SSH, and routing first; do not assume cross-subnet reachability.
- Treat AP/router setup as OS/network configuration work; treat `fleet_airlink` as middleware layered on top.
- Keep private LAN addresses, credentials, and absolute home-directory paths out of wiki pages; use placeholders instead.
- Validate code changes with `python3 -m unittest discover -s tests -v`, then use hwsim/demo scripts when the change affects integration behavior.
- File durable quirks into `knowledge/` instead of leaving them only in chat history.

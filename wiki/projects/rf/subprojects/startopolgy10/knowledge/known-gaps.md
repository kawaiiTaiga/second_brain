# startopolgy10 Known Gaps

## Emergency Retransmission

Emergency retransmission is not implemented yet.

Current consequence:
- if an `AIRLINK_EMERGENCY` packet is lost, a drone can miss the command and never ACK it

This is already visible in the logical test results under packet loss.

## Real MAVLink 2 Integration

The current stack still uses a JSON datagram scaffold for message transport semantics.

Missing major work:
- real MAVLink XML code generation in the runtime path
- real signing integration in the live transport path

## Router/AP Bring-up Outside the Repo

The repository does not yet own a concrete `hostapd`/`dnsmasq`/firewall bring-up workflow for real hardware deployment.

## Remote Node Not Yet Onboarded

A real second node has not yet been fully onboarded from this host because the attempted target did not present a confirmed reachable SSH path during setup time.

## GUI Dependency Boundary

The GUI depends on:

- the control API already running
- `ffmpeg` installed
- `python3-tk` installed

If the GCS API is not up, the GUI cannot do anything meaningful yet.

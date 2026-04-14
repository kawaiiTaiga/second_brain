# startopolgy10 Testing and Validation

## Unit and Logic Tests

The repository has test coverage for:

- config validation
- protocol encoding/decoding
- state-machine transitions
- logical simulation
- control API behavior
- video routing behavior
- GUI helper logic

The last recorded full local unit test run passed with `22` tests.

## Logical Simulation Findings

The logical simulator validated:

- 10-drone baseline scheduling and activation
- fleet-wide emergency in a no-loss case
- continued operation under modest random packet loss
- `LOST_BEACON` transition and fallback report behavior

The main uncovered gap is emergency retransmission: under packet loss, one dropped emergency datagram can still produce a missing ACK.

## hwsim Validation

The hwsim stack was validated for:

- single AP + single STA smoke
- 3-drone run
- 3-drone debug run confirming TIMESYNC/BEACON/REPORT traffic
- 10-drone run confirming full discovery

See `TEST_REPORT.md` for the detailed counts and observations that were recorded during these runs.

## Video and GUI Smoke Checks

Local demo validation confirmed:

- owner stream forwarding from drone 1 and later switching to drone 2
- preview fan-out counters increasing per drone
- live forwarded counters following the currently selected owner
- GUI startup against the local demo, with separate preview and live ports

A durable local-demo gotcha is that on a single machine, the drone local video ingress ports must be different from the GCS per-sysid receive ports to avoid bind collisions.

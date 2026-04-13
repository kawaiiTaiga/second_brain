# startopolgy10 Networking and Node Onboarding

## Core Model

This project assumes a star topology:

- one GCS node at the center
- up to 10 drone nodes
- no direct drone-to-drone traffic
- all traffic goes through the GCS

## Loopback Demo vs Real Nodes

The example configs use loopback-friendly values for local testing. For real nodes, replace loopback addresses with actual LAN addresses.

What must change for a real drone node:

- `gcs_ip` must point to the real GCS LAN IP
- each node needs a unique `system_id`
- each node needs its own `bind_port`
- each node should use its own `video_base_port`
- if the video sender is local to the drone node, `video_ingress_port` should point at that local sender path

## Safe Template for a Real Drone Config

Use placeholders instead of hard-coding private infrastructure into the wiki:

```json
{
  "role": "drone",
  "system_id": 2,
  "bind_ip": "0.0.0.0",
  "bind_port": 14602,
  "gcs_ip": "<gcs-lan-ip>",
  "gcs_control_port": 14600,
  "video_base_port": 5602,
  "video_ingress_port": 5702
}
```

## Bring-up Sequence for Another Node

1. Confirm IP reachability between the node and the GCS.
2. Confirm SSH reachability if remote setup is intended.
3. Start the GCS daemon with a non-loopback `bind_ip` or `0.0.0.0`.
4. Start the drone daemon with `gcs_ip=<gcs-lan-ip>`.
5. Check `GET /state` on the GCS control API and confirm the new `system_id` appears in `active_sysids`.
6. Only then layer on video senders and the GUI.

## Remote-Node Setup Lesson

An attempted remote-node configuration from the current host could not proceed because the target node did not present a reachable SSH path from this machine.

Durable rule:
- if SSH or basic routing is not working first, do not spend time changing app config yet
- verify network path, routing, and firewall before diagnosing middleware

## Router and AP Guidance

If a node should also act as a router/AP:

- OpenWrt is optional, not required
- regular Linux with `hostapd`, `dnsmasq`, and `nftables`/`iptables` is sufficient
- `fleet_airlink` still remains middleware on top of that network path

## One Radio vs Two Radios

- One radio is possible mainly for Ethernet uplink + Wi-Fi AP, or for chipsets that truly support concurrent AP+STA well.
- Two radios are strongly preferred when a node must do Wi-Fi uplink/backhaul and Wi-Fi AP/downlink simultaneously.
- In practice, two radios make topology, routing, and debugging much simpler.

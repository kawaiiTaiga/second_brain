# rf Router vs Middleware

## Durable Rule

Treat `fleet_airlink` as application-level wireless middleware, not as the AP/router itself.

## What the Current Code Does

- GCS and drone link daemons
- superframe scheduling and timesync logic
- telemetry and video gating
- GCS runtime control API
- thumbnail/live-video GUI on top of routed UDP streams

## What It Does Not Do

- create Wi-Fi APs
- run DHCP
- enable IP forwarding or NAT
- configure `hostapd`, `wpa_supplicant`, or firewall rules
- create Linux routes between subnets

## Operational Consequence

Another node can join only after all of the following exist outside the middleware:

- IP reachability to the GCS node
- AP/STA association or other routed backhaul
- firewall rules that allow the required UDP control and video ports

## Router Bring-up Notes

- OpenWrt is optional. Regular Linux with `hostapd` + `dnsmasq` + `nftables`/`iptables` is sufficient.
- Two RF chips are strongly preferred when one box must do Wi-Fi uplink/backhaul and Wi-Fi AP/downlink at the same time.
- One RF chip is mainly practical for Ethernet uplink + Wi-Fi AP, or for chipsets that truly support concurrent AP+STA well.

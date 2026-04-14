# startopolgy10 RF Power and Antenna Guidance

## Basic Terms

- TX power is what the radio transmits, usually in `dBm`.
- Antenna gain is usually discussed in `dBi`.
- Effective radiated power depends on both, plus cable loss.

Durable formula:

- `EIRP(dBm) = TX power(dBm) + antenna gain(dBi) - cable loss(dB)`

## Practical Guidance

Do not default to maximum TX power.

Too much power can cause:
- self-interference between radios on the same box
- receiver overload at short range
- poor link symmetry
- extra noise without useful range improvement

## Two-Radio Starting Strategy

A practical starting pattern for a dual-radio node is:

- backhaul/uplink radio on `5 GHz`
- local AP/downlink radio on `2.4 GHz`

Reason:
- simpler separation of roles
- less self-interference
- easier field tuning

## Conservative Starting Ranges

These are starting points, not universal rules:

- local AP with omni antenna: around `8-12 dBm` TX, antenna around `2-5 dBi`
- short backhaul: around `8-14 dBm` TX, antenna around `5-9 dBi`
- longer directional backhaul: around `10-17 dBm` TX, higher-gain directional antenna

## Tuning Goal

Start low, measure RSSI/noise/retries, then increase only as needed.

A practical target is a healthy link rather than the strongest possible transmit power.

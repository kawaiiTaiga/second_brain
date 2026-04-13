# startopolgy10 hwsim and Kernel Notes

## Kernel State

The hwsim work was validated on kernel:

- `5.10.160-rockchip-rk3588-mesh2`

A config backup from before enabling hwsim support is kept in:

- `kernel-build-backups/config-5.10.160-rockchip-rk3588-mesh2-before-mac80211_hwsim`

## Module Change

The key kernel config change was:

- `CONFIG_MAC80211_HWSIM=m`

The module was then built and installed so the test environment could run real Linux wireless user-space components against simulated radios.

## Operational Script Notes

Use `scripts/run_fleet_hwsim.sh` as the entry point.

Important lessons from the bring-up work:

- reuse the default interfaces created by `mac80211_hwsim`
- do not assume extra interface creation is needed
- validate with the script's `--preflight` mode before running a full test

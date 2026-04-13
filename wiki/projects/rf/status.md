# rf Status

## Summary

`rf` is the parent wiki project for radio/networking systems, topology bring-up, and wireless middleware. The currently documented subproject is `startopolgy10`, which captures the Fleet AirLink star-topology-10 work in the `communication` repository.

## Current State

- `startopolgy10` is the only documented RF subproject so far.
- The subproject records implementation state, test results, video/GUI routing, and networking guidance.
- Parent-level RF knowledge currently focuses on keeping Linux networking/router responsibilities separate from application-level middleware.

## Subprojects

- `startopolgy10` - Fleet AirLink v0.1 scaffold, simulator, hwsim tests, video token routing, and GCS GUI work.

## Next

- Add more RF subprojects under `rf` instead of flattening them at top level.
- Keep parent-level wireless/networking guidance here when it applies across multiple subprojects.

## Decisions

- `rf` is the parent node for wireless/topology work in the wiki.
- Use `subprojects/` for concrete codebases or deployment variants.
- Do not store credentials, private IP addresses, or personal machine paths in this public wiki.

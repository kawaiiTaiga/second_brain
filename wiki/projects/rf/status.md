# rf Status

## Summary

`rf` is the parent wiki project for radio/networking systems, topology bring-up, and wireless middleware. The currently documented child project is `startopolgy10`, which captures the Fleet AirLink star-topology-10 work in the `communication` repository.

## Current State

- `startopolgy10` is the only documented RF child project so far.
- The child project records implementation state, test results, video/GUI routing, and networking guidance.
- Parent-level RF knowledge currently focuses on keeping Linux networking/router responsibilities separate from application-level middleware.

## Child Projects

- `startopolgy10` - Fleet AirLink v0.1 scaffold, simulator, hwsim tests, video token routing, and GCS GUI work.

## Next

- Add more RF child projects under `rf` instead of flattening them at top level.
- Keep parent-level wireless/networking guidance here when it applies across multiple related projects.

## Decisions

- `rf` is the parent node for wireless/topology work in the wiki.
- Use direct child folders for concrete codebases or deployment variants.
- Do not store credentials, private IP addresses, or personal machine paths in this public wiki.

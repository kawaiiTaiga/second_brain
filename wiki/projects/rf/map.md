# rf Map

## Wiki Hierarchy

```text
projects/rf/
  status.md
  map.md
  skills/
    README.md
  knowledge/
    README.md
    router-vs-middleware.md
  startopolgy10/
    status.md
    map.md
    skills/
    knowledge/
  rf-agent/
    status.md
    map.md
    skills/
    knowledge/
```

## Scope

- Parent layer: reusable RF/networking conventions that apply across multiple efforts.
- Child-project layer: concrete implementation notes, validation data, and deployment guidance.

## Current Child Projects

- `startopolgy10` - Fleet AirLink v0.1 work for a GCS-centered star topology with up to 10 drones.
- `rf-agent` - Orange Pi focused CLI and skill bundle for live TinySA work, packet capture, and RF-plus-network correlation.

## Documentation Boundaries

- Keep AP/router, RF topology, and hardware bring-up guidance in `projects/rf/` if it applies broadly.
- Keep repository-specific implementation details in `projects/rf/startopolgy10/`.
- Keep TinySA, daemon, panel-control, and RF-agent workflow details in `projects/rf/rf-agent/`.
- Use placeholders such as `<gcs-lan-ip>` instead of real private infrastructure details.

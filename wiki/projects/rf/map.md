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
  subprojects/
    startopolgy10/
      status.md
      map.md
      skills/
      knowledge/
```

## Scope

- Parent layer: reusable RF/networking conventions that apply across multiple efforts.
- Subproject layer: concrete implementation notes, validation data, and deployment guidance.

## Current Subprojects

- `startopolgy10` - Fleet AirLink v0.1 work for a GCS-centered star topology with up to 10 drones.

## Documentation Boundaries

- Keep AP/router, RF topology, and hardware bring-up guidance in `projects/rf/` if it applies broadly.
- Keep repository-specific implementation details in `projects/rf/subprojects/startopolgy10/`.
- Use placeholders such as `<gcs-lan-ip>` instead of real private infrastructure details.

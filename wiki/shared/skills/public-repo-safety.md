# Public Repo Safety

This repository is public. Treat every committed line as publishable.

## Do Not Store

- Secrets, tokens, passwords, or private keys.
- Internal-only URLs, dashboards, or admin endpoints unless they are intentionally public.
- Absolute local machine paths if they reveal personal usernames, download folders, or private workstation details.
- Private business notes, customer data, or anything that should not appear in public search results.

## Before Pushing

1. Scan new pages for credentials, private URLs, and machine-specific paths.
2. Replace sensitive local paths with a neutral description unless the exact path is essential and safe.
3. Check whether deployment details are meant to be public.
4. If the wiki needs to hold private operating context, change repository visibility before adding it.

## Safe Alternatives

- Use canonical GitHub URLs instead of workstation paths.
- Use role-based descriptions like `production site` or `local preview server` when exact internals are unnecessary.
- Keep sensitive details in a private system and link only if the destination is also intended to be public.

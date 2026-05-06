# Review Journal

I treated `silver-mesh-lease-mesh` as a project where the smallest useful behavior should still be inspectable.

The local checks classify each case as `ship`, `watch`, or `hold`. That gives the project a small review vocabulary that matches its distributed systems focus without claiming live deployment or external usage.

## Cases

- `baseline`: `quorum health`, score 100, lane `hold`
- `stress`: `lease drift`, score 168, lane `ship`
- `edge`: `replica lag`, score 154, lane `ship`
- `recovery`: `membership churn`, score 151, lane `ship`
- `stale`: `quorum health`, score 136, lane `watch`

## Note

This file is intentionally plain so the fixture remains the source of truth.

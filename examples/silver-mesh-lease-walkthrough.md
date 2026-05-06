# Silver Mesh Lease Mesh Walkthrough

This note is the quickest way to read the extra review model in `silver-mesh-lease-mesh`.

| Case | Focus | Score | Lane |
| --- | --- | ---: | --- |
| baseline | quorum health | 100 | hold |
| stress | lease drift | 168 | ship |
| edge | replica lag | 154 | ship |
| recovery | membership churn | 151 | ship |
| stale | quorum health | 136 | watch |

Start with `stress` and `baseline`. They create the widest contrast in this repository's fixture set, which makes them better review anchors than the middle cases.

The useful comparison is `lease drift` against `quorum health`, not the raw score alone.

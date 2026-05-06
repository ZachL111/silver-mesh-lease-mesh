# silver-mesh-lease-mesh

`silver-mesh-lease-mesh` explores distributed systems with a small SQL codebase and local fixtures. The technical goal is to implement an SQL distributed systems project for lease storage recovery, using log and snapshot fixtures and replay consistency checks.

## Reason For The Project

The project exists to keep a narrow engineering decision visible and testable. For this repo, that decision is how quorum health and replica lag should influence a review result.

## Silver Mesh Lease Mesh Review Notes

The first comparison I would make is `lease drift` against `quorum health` because it shows where the rule is most opinionated.

## What It Does

- `fixtures/domain_review.csv` adds cases for quorum health and lease drift.
- `metadata/domain-review.json` records the same cases in structured form.
- `config/review-profile.json` captures the read order and the two review questions.
- `examples/silver-mesh-lease-walkthrough.md` walks through the case spread.
- The SQL code includes a review path for `lease drift` and `quorum health`.
- `docs/field-notes.md` explains the strongest and weakest cases.

## How It Is Put Together

The core code exposes a scoring path and the added review layer uses `signal`, `slack`, `drag`, and `confidence`. The domain terms are `quorum health`, `lease drift`, `replica lag`, and `membership churn`.

The SQL checks add a separate view over the domain review fixture.

## Run It

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

## Check It

That command is also the regression path. It verifies the domain cases and catches mismatches between the CSV, metadata, and code.

## Boundaries

The repository is intentionally scoped to local checks. I would expand it by adding adversarial fixtures before adding features.

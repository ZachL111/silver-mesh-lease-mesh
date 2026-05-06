# silver-mesh-lease-mesh

`silver-mesh-lease-mesh` explores distributed systems in SQL. The repository keeps the core rule set compact, then surrounds it with examples that show how the decisions move.

## Silver Mesh Lease Mesh Notes

The quickest review path is the verifier first, then the fixtures, then the operations note. That order makes it easy to see whether the code, data, and explanation still agree.

## Implementation Notes

The design is intentionally direct: parse or construct a signal, score it, classify it, and verify the expected branch. This makes the repository useful for studying distributed systems behavior without needing a service or database unless the language project itself is SQL. The SQL project uses sqlite fixtures, views, and assertions to keep query behavior inspectable.

## Why This Exists

This project keeps the domain idea close to the tests. That makes it useful as a reference implementation, a small experiment, or a starting point for a more specialized tool.

## Feature Notes

- Uses fixture data to keep quorum behavior changes visible in code review.
- Includes extended examples for lease timing, including `surge` and `degraded`.
- Documents message ordering tradeoffs in `docs/operations.md`.
- Runs locally with a single verification command and no external credentials.
- Stores project constants and verification metadata in `metadata/project.json`.

## Example Scenarios

`examples/extended_cases.csv` adds six named cases. I kept the names plain so failures are easy to read in a terminal: baseline, pressure, surge, degraded, recovery, and boundary.

## Code Tour

- `tests`: verification harness
- `fixtures`: compact golden scenarios
- `examples`: expanded scenario set
- `metadata`: project constants and verification metadata
- `docs`: operations and extension notes
- `scripts`: local verification and audit commands
- `schema.sql`: sqlite schema and view definitions

## Local Setup

Use a normal shell with SQL available on `PATH`. The verifier is written as a PowerShell script because the portfolio was assembled on Windows.

## Try It

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

This runs the language-level build or test path against the compact fixture set.

## Tests

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/audit.ps1
```

The audit command checks repository structure and README constraints before it delegates to the verifier.

## Boundaries

The repository favors determinism over breadth. It does not pull live data, keep secrets, or depend on network access for verification.

## Roadmap

- Add a short report command that prints the score breakdown for a single scenario.
- Add malformed input fixtures so the failure path is as visible as the happy path.
- Split the scoring constants into a typed configuration object and validate it before use.
- Add one more distributed systems fixture that focuses on a malformed or borderline input.

# Issue

**Title:** mOTUs DB fetcher: deterministic default identifier + value override (+galaxy2)

## Description

### What

The mOTUs DB identifier — the `motus_db_versioned` data-table **value**, which is also used as the on-disk directory name — was generated from the job's wall-clock time:

```python
time = datetime.utcnow().strftime("%Y-%m-%dT%H%M%SZ")
db_value = "db_from_{0}".format(time)
```

So every build of the *same* mOTUs release produced a different `db_from_<timestamp>`, and no two servers (or two rebuilds on one server) could ever agree on a value for a given DB. That makes the reference data non-reproducible and breaks portability of workflows/entries that pin a specific value.

### Change

- **Deterministic default**: derive the identifier from the Zenodo record's `publication_date` instead of the build time → `db_from_<YYYY-MM-DD>` (e.g. `db_from_2023-03-28` for 3.1.0, `db_from_2021-07-27` for 3.0.1, `db_from_2021-04-26` for 3.0.0). Same release → same value, every time, everywhere.
- **Override**: add an optional `--value` parameter (empty by default) so an admin can reproduce or match an entry already published on another server (e.g. `db_from_2026-04-27T094930Z`).
- Bump to `+galaxy2`.

Two tests: the default (asserts `db_from_2023-03-28`) and an explicit override.

### Why

We're building the mOTUs DB as a reference-data bundle for `idc.galaxyproject.org` (shared via CVMFS) and need the published value to match what already exists on usegalaxy.eu (`db_from_2026-04-27T094930Z`) rather than minting a fresh timestamp each build. The deterministic default also makes any future rebuild reproducible.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `083065f1da49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
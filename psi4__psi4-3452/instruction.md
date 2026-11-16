# Issue

**Title:** libpsio: remove multi-volume file striping

## Description

## Summary

Removes the long-unused **multi-volume file striping** from `libpsio`. A PSIO
unit could historically be striped across up to `PSIO_MAXVOL` (8) physical
files, with consecutive 64 KiB pages distributed round-robin across the
volumes. In practice the feature was never exercised:

- The default was hard-wired to a single volume (`NVOLUME=1`) and nothing in
  the tree ever configured more.
- The per-volume path lookup (`get_volpath`) was already dead code — `open()`
  discarded its result and used `PSIOManager::get_file_path()` instead.
- No code outside `libpsio` reads `numvols`, `PSIO_MAXVOL`, or `psio_vol[]`
  (verified by an exhaustive grep of `src/`, `include/`, and `driver/`).

Each unit is now backed by a single file.

## Changes

- **`psio_ud`**: drop `numvols` and the `vol[PSIO_MAXVOL]` array → a single
  `psio_vol vol`.
- **`config.h`**: drop `PSIO_MAXVOL` and the three striping-only error codes
  (`MAXVOL`, `NOVOLPATH`, `IDENTVOLPATH`). Their numeric values (3, 4, 19) are
  left as gaps so the remaining **public** error-code values are unchanged.
- **`rw.cc`**: seek once and stream sequentially, instead of seeking every
  volume and selecting one per page.
- **`volseek.cc`**: drop the `numvols` dimension (final offset is
  `page*PAGELEN + offset`); the overflow-safe chunked `lseek` is preserved.
- **`open`/`exists`/`close`/`init`**: collapse the per-volume loops to a single
  file; drop the now-meaningless identical-volume-path check.
- Delete `get_numvols.cc` and `get_volpath.cc`; stop seeding the `NVOLUME` /
  `VOLUMEn` default keywords.

Net: **−254 lines**, 2 files removed.

## Validation

The standalone `psio_roundtrip` test (added in #3430) passes unchanged. It
deliberately spans the **single-partial-page**, **multi-full-page**
(`3*PSIO_PAGELEN + 137` bytes), and **trailing-partial-page** branches of
`PSIO::rw`, so the rewritten sequential I/O path is covered.

## Stacking

Stacked on **#3430** (libpsio config.h modernization); both edit
`libpsio/config.h`. GitHub shows the cumulative diff until #3430 merges, after
which this rebases to the incremental change. Review the last commit only, or
compare against `libpsio/modernize`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a39a6acef89`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** libpsio: factor out unit-filename generation (on #3452)

## Description

## Description

Follow-up cleanup from #3514 (item 3), now that #3452 is merged.

`PSIO::open()` and `PSIO::exists()` each rebuilt the on-disk filename with the same `get_filename` + `PSIOManager::get_file_path` + `malloc`/`sprintf`/`strdup`/`free` sequence. This factors it into a single private helper `PSIO::get_unit_filename(unit)` that composes the path with `std::string` (`<path><name>.<unit>`), removing the duplication and the manual C-string juggling on the file-open path. Behaviour is unchanged.

## User API & Changelog headlines
- No user-facing change (internal refactor).

## Dev notes & details
- New private member `std::string PSIO::get_unit_filename(size_t unit)` composes `<path><name>.<unit>` via `std::string`.
- `PSIO::open()` and `PSIO::exists()` call it instead of each re-implementing the same path construction with `malloc`/`sprintf`/`strdup`/`free`.
- Pure refactor: no behavioural change on the file-open/exists paths.

## Questions
- None.

## AI
- Refactor drafted with Claude Code (identifying the duplicated path-construction, extracting the helper); reviewed and verified by me.

## Checklist
- [x] Tests added for any new features — n/a (no new feature; covered by existing `psio_roundtrip` test)
- [x] Docstring or narrative docs/sphinxman/source updated if needed — n/a

## Status
- [x] Ready for review

---

Verified: the `psio_roundtrip` standalone test passes (4/4), and a normal SCF (which round-trips PSIO to disk) gives the expected energy.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5da6bbf05148`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
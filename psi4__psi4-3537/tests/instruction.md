# Issue

**Title:** cc: replace malloc'd C-string arrays with owning std::string containers

## Description

## Description

Modernizes a cluster of obsolete owned C-string arrays in the CC modules, replacing manual `malloc()`/`strdup()`/`free()` bookkeeping with owning `std::string` containers. This is a follow-up to the libpsio `get_filename()` modernization, found while sweeping the tree for the same antipattern.

## User API & Changelog headlines
- [ ] None — internal cleanup, no user-facing or numerical change.

## Dev notes & details
- [x] ccresponse `polar`/`roa`/`optrot`: the per-call `char **cartcomp` (a `malloc(3)` + `strdup("X"/"Y"/"Z")` + `free`) becomes a `const std::array<std::string, 3>`.
- [x] cceom: the `char **irr_labs_lowercase` MOInfo member (`malloc` + per-irrep `strdup` + manual `free` in `cleanup()`) becomes a `std::vector<std::string>`, matching the `std::vector<std::string> irr_labs` it is copied from and sits next to.
- [x] The existing `sprintf()` label-building sites are unchanged apart from a `.c_str()` on the array element.
- [x] The lower-casing loop now casts to `unsigned char` before `std::tolower()` (the previous code passed a raw `char`).
- [x] Behavior-preserving and mechanical; all six touched TUs compile clean locally.

## Questions
- [ ] None.

## AI
- [x] The antipattern survey and the mechanical conversion were done with Claude Code; the change is behavior-preserving and human-reviewed.

## Checklist
- [x] Tests added for any new features — n/a (no behavior change; exercised by existing ccresponse/cceom tests)
- [x] Docstring or narrative docs/sphinxman/source updated if needed — n/a

## Status
- [x] Ready for review

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e8935afcf3df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
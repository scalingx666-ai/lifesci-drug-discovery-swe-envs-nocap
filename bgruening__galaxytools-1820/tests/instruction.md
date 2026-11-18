# Issue

**Title:** Polish split_file_to_collection and splitfasta help with diagrams

## Description

## Summary

- **split_file_to_collection**: Added PNG diagram showing record distribution across output files (alternating mode). Rewrote help with structured Description sections for record allocation, splitting modes, and tabular column split.
- **splitfasta**: Added PNG diagram showing FASTA split into per-sequence collection. Rewrote help with Description/Examples format. Bumped version to 0.5.2.
- SVG sources shipped in `static/images/`, PNG referenced via `$PATH_TO_IMAGES`

## Test plan

- [x] `planemo t` split_file_to_collection — all 20 tests pass
- [x] `planemo t` splitfasta — all 2 tests pass
- [x] `planemo l` — lint passes (pre-existing warnings only on split_file_to_collection due to legacy profile)
- [ ] Verify help rendering in Galaxy UI

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb3de341fc1a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
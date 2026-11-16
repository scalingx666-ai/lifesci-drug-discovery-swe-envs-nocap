# Issue

**Title:** Backmerge: #3882 – Patch Result SVG Glyph IDs

## Description

Backmerge of #3928 from `master` into `release/1.49`.
Master commit: 3e5070498 (squash merge of #3928). The diff matches it exactly: 11 files, +388 / −2.

Adds the `render-svg-unique-id` render option (default `true`). Every id in a rendered SVG, and every reference to it, gets a per-render prefix. Several Indigo SVGs inlined into one HTML page no longer share glyph, gradient or mask ids. With `false` the output is the same as before, byte for byte. Full description in #3928.

## Backmerge request
- [x] PR name follows the pattern `Backmerge: #3882 – `
- [x] PR is linked with the issue
- [x] base branch (release/1.49) is correct
- [x] code contains only backmerge changes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bee890b2687b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
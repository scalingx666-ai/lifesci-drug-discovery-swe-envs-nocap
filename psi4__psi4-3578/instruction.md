# Issue

**Title:** Rebalance RPA/TDA Tightness

## Description

## Description
This PR is a followup from #3572. That PR got _a_ test passing, but to get all my tests passing, I found it necessary to adjust the numerical zero of orthogonalization as well. All other tests pass, so no further follow-ups are needed. This should be the last warm-up PR before the DFT Manager code.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] r_convergence for TD-SCF is now capped at 1e-9. Any tighter thresholds will be raised up to that.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] `_gs_orth`'s default numerical threshold raised to `NUM_ZERO`
- [x] `NUM_ZERO` and `eigmax_to_error` parameters. Those were marked as needing numerical experimentation, and upon changing `_gs_orth`, they can be lowered.
- [x] Adjusts test added in #3572 to be tighter, given these new, tighter parameters
- [x] Adds that RPA test that @TiborGY asked for in #3572, now that I have an actual example   

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [x] None

## Checklist
- [x] Tests added for any newly improved features

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `23be3de4b1f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
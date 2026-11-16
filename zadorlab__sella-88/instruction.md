# Issue

**Title:** Report Hessian diagonalization progress

## Description

## Summary

- Add opt-in Hessian progress reporting with `hessian_progress=True`; default logging remains the ordinary optimization table.
- Announce the start of iterative Hessian diagonalization, then report and flush each completed finite-difference force evaluation with a timestamp.
- Report completion or failure and the total number of force evaluations.
- Count both evaluations used by three-point finite differences.

Progress lines begin with `#` so existing parsers can distinguish them from optimizer-step rows.

## Testing

- `346 passed` in `fc_env`

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c83b3cf34b08`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
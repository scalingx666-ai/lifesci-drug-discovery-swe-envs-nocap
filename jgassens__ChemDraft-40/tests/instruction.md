# Issue

**Title:** chore: track the ORCA/SMD microstate probe and its parser fixture

## Description

Two files from the pKa QM campaign that have lived untracked in the main checkout since 2026-08-30, as the only copies:

- `qm_orca.py`: the ORCA port of the tracked `qm_microstate.py`. Its docstring designs a two-run experiment (`legacy-ddcosmo` vs `legacy-smd`) to test whether the solvation model explains the glycine log Kz failure. Neither run has been done; this just stops the script from being one `git clean` away from gone.
- `qm-orca-fixture.txt`: an excerpt of a real ORCA 6.1.1 job on Juno (320337, 2026-08-08) that the script's `--self-test` parses.

Also deletes the untracked `deployability.scratch.real.test.ts` from the same afternoon, per its own header ("delete once the comparison is written up").

Not run here: the self-test needs rdkit, which no Python on this Mac has. The script parses (`ast.parse`). No app code changes, so no build-stamp bump.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21508f7baf0c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
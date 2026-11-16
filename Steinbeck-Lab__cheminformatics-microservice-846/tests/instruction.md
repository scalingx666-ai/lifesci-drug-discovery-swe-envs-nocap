# Issue

**Title:** fix(deps): bump Pillow to 13.0.0 and run CI on Python 3.11

## Description

Fixes all open Dependabot alerts. Every one is Pillow, fixed in 13.0.0, in `requirements.txt` and `docs/requirements.txt`.

Pillow 13 needs Python 3.11. The Docker images and Read the Docs already run 3.11, so the test workflow moves from 3.10 to 3.11 to match.

Replaces the closed Dependabot PR #843, which bumped Pillow but would have failed CI on Python 3.10.

Checked locally on Python 3.11 with Pillow 13.0.0: 1696 tests pass. The only 2 failures are the SURGE tests, because the `surge` binary is not installed locally; CI installs it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4be2b07c213d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
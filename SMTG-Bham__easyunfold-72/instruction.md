# Issue

**Title:** fix: propagate make exit code through tee pipe in docs workflows

## Description

`make ... 2>&1 | tee check.log` silently swallows `make` failures — the pipeline exit code comes from `tee` (always 0), not `make`. Adding `set -o pipefail` makes bash use the exit code of the rightmost failing command in the pipeline.

Also migrates the deprecated `::set-output` syntax to `$GITHUB_OUTPUT` in both workflow files.

**Changes**
- `docs.yaml`, `docs-deploy.yaml`: prepend `set -o pipefail` to the `make | tee` step
- `docs.yaml`, `docs-deploy.yaml`: replace `echo "::set-output name=broken::..."` with `echo "broken=..." >> "$GITHUB_OUTPUT"`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60cd2c494cb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
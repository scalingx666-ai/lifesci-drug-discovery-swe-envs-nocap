# Issue

**Title:** Constrain phonopy build backend in CI

## Description

The Python 3.9 Actions job failed while building phonopy: scikit-build-core 0.10+ rejects phonopy’s `cmake.verbose` setting.

- **CI install:** Apply a build-only constraint while installing the test extra, preserving `sumo` and runtime dependency resolution.

```bash
printf 'scikit-build-core<0.10\n' > "$RUNNER_TEMP/build-constraints.txt"
pip install --build-constraint "$RUNNER_TEMP/build-constraints.txt" -e ".[test]"
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c76f927ff49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
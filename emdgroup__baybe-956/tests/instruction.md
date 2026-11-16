# Issue

**Title:** Fix desirability posterior offsets for minimized targets

## Description

## Problem

For a minimized desirability target, the sampled objective uses `1 - transform(y)`, but the analytic posterior transform only used `-transform(y)`. With arithmetic aggregation, its mean was therefore too small by the sum of the normalized weights of the minimized targets. Its covariance was already correct.

For example, with weights `(1, 3)`, minimized cost transformed by `0.1 * cost - 1`, and maximized yield transformed by `0.01 * yield + 0.1`:

- At `(cost, yield) = (12, 70)`, the objective is `0.8`, but the posterior transform returned `0.55`.
- At `(16, 30)`, the objective is `0.4`, but the posterior transform returned `0.15`.

These are supported affine targets with `require_normalization=False` and `scalarizer="MEAN"`. Minimized identity targets have the same missing-constant problem. This is not a claim that every desirability configuration is affected.

The acquisition builder already computes `best_f` using the sampled-objective orientation. Consequently, the missing posterior offset can change analytic expected-improvement values and recommendations, not merely the displayed score.

## Fix

Reuse `_oriented_targets`, the existing canonical target orientation, instead of maintaining a second negate-only implementation. Preserve the Gaussianity checks, pre-transformation path, signed coefficients and covariance calculation. No API or dependency change; analytic acquisition values for affected configurations intentionally change.

The necessary regression independently calculates Gaussian means and correlated-output variances for all four minimization-direction combinations, unequal weights, affine shifts and a negative affine factor.

## Verification

- New regression on pristine `ed54e0092acd0dc07b2a920ef4b58198f608bfa1`: **3 failed, 1 passed**; failures are the missing minimization offsets. The all-maximize control passes.
- `python -m pytest tests/test_objective.py tests/test_acquisition.py -q --tb=short`: **30 passed** on Python 3.12.6 / Torch 2.15.0+cpu / BoTorch 0.18.1, and **30 passed** on Python 3.10.1 / Torch 2.14.1+cpu / BoTorch 0.16.1.
- An actual fitted BayBE `CompositeSurrogate` / `GaussianProcessSurrogate` / `ExpectedImprovement` consumer, with five synthetic observations and a 201-point dose grid, was compared with the independent Gaussian EI formula from raw posterior means and variances. With identical float64 inputs and seed 17, the unfixed grid optimum was 0.27 versus the reference 0.23. The fix selects 0.23, and maximum acquisition error drops from 0.00834071464919663 to 1.3010426069826053e-16. This is a constructed correctness example, not a physical-lab result, complete `recommend` run, benchmark or sample-efficiency claim. Existing TorchScript-deprecation and legacy-EI numerical warnings remained visible.
- Minimized identity-target API smoke: actual and independently calculated score both 0.7666666666666666.
- Changed-file pre-commit hooks passed, using `SKIP=pyrefly-check` as in the repository's tox lint configuration; the separate tox typecheck did execute Pyrefly. Pinned Ruff 0.16.10 lint/format and docstring checks passed.
- `uv tool run --from tox --with tox-uv tox -e typecheck-py310 --runner uv-venv-runner`: Pyrefly reports **0 errors**, but the command is **not green**. Mypy stops at the installed external `rdkit-stubs/Chem/rdmolfiles.pyi:332` with invalid/duplicate parameters. Running the same Mypy environment on pristine source produces the same two stub syntax errors. No stub edit, warning suppression or unrelated dependency pin was added. No full-repository, GPU or all-Python CI claim.

Prepared with AI assistance. The submitting user reviewed the exact patch and this text before publication.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d22aeda83cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
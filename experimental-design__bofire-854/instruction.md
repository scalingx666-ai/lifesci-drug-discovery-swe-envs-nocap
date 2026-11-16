# Issue

**Title:** Fix sigmoid objective gradients during acquisition optimization

## Description

## What is fixed?
.

Sigmoid rewards can be finite while their gradients are NaN: the explicit exponential overflows during backward. With a steep but valid threshold, this aborts a real `MultiplicativeSoboStrategy.ask(1)` inside BoTorch's acquisition optimizer, even in float64.

Use `torch.sigmoid` for the four affected callable variants and `scipy.special.expit` for their matching public NumPy evaluators. Evaluate decreasing factors at the negative logit directly instead of subtracting an almost-one value. This also preserves small, representable rewards above a minimizing threshold or outside a target window.

- Covers maximize, minimize, moving-maximize and target-window objectives.
- Keeps adaptation, weights, shapes, output indexing and Series labels unchanged.
- No clipping, warning suppression, new dependencies or optimizer changes; SciPy is already required.

## Verification
- Eight necessary saturation/analytic-gradient regressions: **all eight fail on untouched main**, all pass after the fix (float32/float64, batched samples, nonzero output index, moving threshold, decreasing tails, Series/ndarray evaluation with overflow set to raise).
- `pytest tests/bofire/utils/test_torch_tools.py -q`: **54 passed**.
- Affected SOBO objective/acquisition construction cases: **17 passed, 1 skipped**.
- Entire data-model suite in a separate core-dependencies-only environment: **1,877 passed, 55 skipped**. Public objective evaluation also succeeds with no torch installed.
- Independent 120-digit Decimal value/derivative oracle: **24 combinations** (four objectives × two dtypes × three steepness scales), including target-window boundaries and saturated tails.
- Actual fitted two-output GP, qSR acquisition and software-only experiment loop: untouched main fails its first `ask(1)` with `OptimizationGradientError`; patched source completes three `ask → simulate → tell` rounds, growing from six to nine observations. Recommendations `0.7278 → 0.7428 → 0.7516` approach the simulated performance optimum at `0.75`.
- Repository-wide Ruff 0.6.5 lint and format checks pass (466 files).
- Full Ty 0.0.16 check exits successfully after installing the declared LLM extras; existing configured warnings remain.

No physical instruments or experiments were controlled.

## Checklist
- [x] Necessary regression coverage included.
- [x] Affected tests, independent math oracle and actual optimization scenario run locally.
- [x] Existing objective documentation and changelog updated.

AI-assisted implementation, investigation and independent agent review. I supervised and checked the work as it progressed.

### Upstream CI status
Checked the posted head in Actions: the workflow explicitly says **“This workflow is awaiting approval from a maintainer.”** No CI jobs have launched yet; the local passing checks above are not a claim that upstream CI is green.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00f9dabe360a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
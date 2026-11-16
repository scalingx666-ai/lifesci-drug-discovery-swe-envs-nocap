# Issue

**Title:** Fix NChooseK residuals for mixed experiment tables and labelled rows

## Description

## What is fixed?
.

NChooseK residual evaluation currently converts the entire experiment table to NumPy before selecting its numeric features. A categorical solvent, string metadata or timestamp column makes that array object-typed, and the Gaussian's `np.exp` fails on otherwise valid numeric formulation inputs.

The returned Series also loses experiment labels. Combining this residual with a linear constraint via `Constraints.__call__` then silently expands two labelled experiments into four rows containing NaNs.

Select the constrained columns before conversion and return the original experiment index. This removes the redundant whole-table array copy; the Gaussian relaxation, count bounds, `none_also_valid`, discrete feasibility and optimizer logic are unchanged. Missing constrained columns now naturally raise `KeyError`, matching the other feature-projected constraints.

## Verification
- Five necessary mixed-table/alignment regression cases: **all five fail on untouched main**, all pass after the fix. Covers categorical/datetime/output metadata, reordered features, duplicate named row labels, a Gaussian interior point, four min/max bands and composition with a linear constraint.
- Entire data-model suite with core dependencies only: **1,882 passed, 55 skipped**.
- Existing optimizer utilities and NChooseK pruning tests: **145 passed**.
- Independent active-ingredient count oracle: **2,808 formulation rows across 80 constraint bands**, with mixed metadata and duplicate labels.
- Actual software-only formulation campaign: `RandomStrategy.ask(4) → simulated yield → composed residual evaluation → tell`, repeated three times. Untouched main fails on its first residual evaluation; patched source records **12 experiments**, with aligned `(4, 2)` residual matrices and zero violations each round. No hardware control.
- Repository-wide Ruff 0.6.5 lint/format and Ty 0.0.16 checks exit successfully; existing configured type warnings remain.

## Checklist
- [x] Necessary behavioral regressions included; no source-text or wiring tests.
- [x] Runtime failure reproduced before and campaign exercised after repair.
- [x] Existing documentation and changelog updated.

This is separate from #842's joint-feasibility/pattern-generation issue and #740's nonlinear optimizer integration.

AI-assisted implementation, investigation and independent agent review. I supervised and checked the work as it progressed.

### Upstream CI status
Checked the posted head in Actions: the workflow explicitly says **“This workflow is awaiting approval from a maintainer.”** No CI jobs have launched yet; the local passing checks above are not a claim that upstream CI is green.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `86dbfc40982f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
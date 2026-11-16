# Issue

**Title:** Document the acquisition function data models

## Description

Fourth package batch of the migration started in #802 (#803 objectives/priors, #806 features). Drains the `acquisition_functions` allowlist to zero — **28 field descriptions and 16 class docstrings**, taking the ratchet from 459 to 415 remaining entries.

Almost none of it was harvestable: only `qLogPF` carried an `Attributes:` block, so this is close to 44 pieces of new prose. It is also the package that most needed it — the level-2 digest prototype in #804 is literally this union, and it currently reports `qUCB beta=0.2` with nothing about what `beta` does.

## Deduplication

`n_mc_samples` was declared on **13 of the 14** concrete acquisition functions and `alpha` on **all 5** multi-objective ones. Since redeclaring a field drops the inherited description, each copy would have needed its own duplicate of the same sentence.

A new `MCAcquisitionFunction` base carries `n_mc_samples`; `alpha` moves onto the existing `MultiObjectiveAcquisitionFunction`. `pTS` keeps inheriting `SingleObjectiveAcquisitionFunction` alone — it is sample-path based and takes no Monte Carlo sample count, which is exactly the distinction the new base draws. `qMFHVKG` redeclares `n_mc_samples` because its default is 32 rather than 512.

Verified additive — no accepted input changes, no spec needed touching:

```
pTS has n_mc_samples : False
qEI  n_mc_samples    : 512 (inherited, described)
qMFHVKG n_mc_samples : 32  (own default and description)
qMFHVKG alpha        : inherited description
qUCB model_dump      : {'type': 'qUCB', 'n_mc_samples': 512, 'beta': 0.2}
```

`prune_baseline` stays duplicated: its four classes straddle both branches, so their only common ancestor is one that `pTS` shares too.

## Claims I derived rather than read

Flagging these explicitly, because the semantics here are BoTorch's rather than BoFire's and three of my inferences were caught in review on the last two PRs. BoFire only forwards these parameters (`sobo.py:90-105`, `mobo.py:80-94`), so the meanings below come from BoTorch, not from anything in this repo:

- **`alpha`** — "tolerance for approximating the partitioning of the objective space; 0 partitions exactly, larger trades accuracy for speed"
- **`tau`** — "temperature smoothing the improvement indicator so it can be differentiated"
- **`beta`** — "how strongly uncertainty is rewarded relative to the predicted mean". Directionally right; I have not spelled out BoTorch's internal scaling
- **`prune_baseline`** — "drops already-observed points unlikely to be the best / on the Pareto front"
- **The recommendations** — that `qLogNEI` and `qLogNEHVI` are the usual defaults, and that the log variants keep a gradient where the plain ones underflow

`num_fantasies` and `num_pareto` I read from `multi_fidelity_knowledge_gradient.py:221-276` rather than inferring.

## One thing to decide separately

**`qMFHVKG.alpha` appears to be inert.** Its strategy reads `n_mc_samples`, `num_fantasies` and `num_pareto` (`multi_fidelity_knowledge_gradient.py:132-134`) and never `alpha`, so a caller can set it and nothing happens. That predates this PR — `qMFHVKG` already declared the field, it now inherits it instead — and I have deliberately **not** documented it as intended behaviour, since it looks more like something to fix than to describe. Worth its own look.

## Also

- `qNegIntPosVar.weights` used `Field(default_factory=lambda: None)` — a factory returning a constant, which kept the default out of `model_json_schema()` (the #804 defect). Now a literal default, and it appears there.
- `CLAUDE.md` and `CONTRIBUTING.md` record the rule from the #806 review: describe only what a caller can set or observe, never a BoFire-internal artefact; state the consequence instead.

## Rename candidates

Carried forward, not acted on: **`alpha`** and **`tau`** are BoTorch names whose meaning the field name does not convey at all — both descriptions exist purely to compensate.

## Verification

- `pytest tests/bofire/data_models` — 1880 passed, 4 skipped
- `pytest tests/bofire -k "sobo or mobo or acquisition or active_learning or qparego or knowledge"` — 207 passed, 8 skipped
- ruff 0.6.5 clean
- `ty==0.0.16` — 158 diagnostics, identical to the merged-main baseline (the count rose from 151 with #724, not with this PR)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce7530bbd1f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
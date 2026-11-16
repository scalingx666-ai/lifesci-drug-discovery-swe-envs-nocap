# Issue

**Title:** Fix qParEGO batch generation to sample independent scalarizations

## Description

## Motivation

.

`QparegoStrategy.ask(q)` currently gives every candidate the same randomly sampled Chebyshev scalarization. This PR draws an independent scalarization for each candidate, while continuing to generate candidates sequentially with previously selected points supplied through `X_pending`.

Baseline predictions, objective transformations, and output constraints are prepared once per batch. Each scalarized objective has its own closure, preserving its weights throughout optimization. The existing qEI, qLogEI, qNEI, and qLogNEI choices remain supported.

## Benchmark evidence

Extended to **six problems, q=4 and q=8, and 20 paired seeds per case**: 480 optimization runs in total (360 new runs and 120 reused original q=8 runs). Each run starts with 16 Sobol observations and adds 64 evaluations, ending at 80 observations. Both policies use sequential, pending-aware qLogNEI with 128 MC samples, 4 restarts, 128 raw samples, and maxiter=200. Only the frequency of sampling scalarization weights changes. Initial designs and the first scalarization per round are matched; the first candidate of the first batch is identical in all 240 pairs.

Relative change in **mean final hypervolume** with independent weights:

| Problem | Objectives | q=4 | q=8 |
|---|---:|---:|---:|
| DTLZ2 | 3 | +34.8% **†** | +64.0% **†** |
| DTLZ7 | 3 | +1.6% | +4.8% |
| Branin–Currin | 2 | +5.1% **†** | +9.1% **†** |
| DTLZ2 | 5 | +4.2% | +5.4% |
| ZDT3 | 2 | +7.7% | +12.8% |
| VehicleSafety | 3 | +0.9% | +3.6% **†** |

† Clear gain: the 95% paired bootstrap interval excludes zero and the two-sided Wilcoxon signed-rank p-value remains below 0.05 after one Holm adjustment across all 12 comparisons. There are **5 clear gains, 7 inconclusive cases, and no clear losses** under this criterion. All sample means favor independent weights, but individual seeds can favor shared weights. In particular, the five-objective results are variable and inconclusive. This supports the change for Pareto-front learning without establishing a universal quality advantage. The full report contains paired intervals, wins/losses, and adjusted p-values.

The shared policy explores 16 weight vectors at q=4 and 8 at q=8; per-candidate sampling explores 64 at either q. Independent weights increase the number of sampled trade-offs but do not guarantee uniform front coverage.

![q=4 scalarization comparison: means and pointwise 95% bootstrap confidence intervals](https://raw.githubusercontent.com/Jimbo994/bofire/8d50ede87ca45c5411aca76aae0ec8325aafa55b/benchmark/extended_results/quality_q4.png)

![q=8 scalarization comparison: means and pointwise 95% bootstrap confidence intervals](https://raw.githubusercontent.com/Jimbo994/bofire/8d50ede87ca45c5411aca76aae0ec8325aafa55b/benchmark/extended_results/quality_q8.png)

[Full extended report](https://github.com/Jimbo994/bofire/blob/8d50ede87ca45c5411aca76aae0ec8325aafa55b/benchmark/extended_results/report.md) · [Reproduction instructions](https://github.com/Jimbo994/bofire/blob/8d50ede87ca45c5411aca76aae0ec8325aafa55b/benchmark/README.md) · [Paired statistics](https://github.com/Jimbo994/bofire/blob/8d50ede87ca45c5411aca76aae0ec8325aafa55b/benchmark/extended_results/paired_comparisons.csv) · [Per-round data](https://github.com/Jimbo994/bofire/blob/8d50ede87ca45c5411aca76aae0ec8325aafa55b/benchmark/extended_results/all_results.csv) · [Raw run/candidate archive](https://github.com/Jimbo994/bofire/blob/8d50ede87ca45c5411aca76aae0ec8325aafa55b/benchmark/extended_results/raw_runs.zip) · [Benchmark script](https://github.com/Jimbo994/bofire/blob/8d50ede87ca45c5411aca76aae0ec8325aafa55b/benchmark/benchmark_parego_scalarization.py)

Evidence is on a separate branch; the PR diff contains only the strategy fix, regression tests, and changelog. These noiseless, short-horizon experiments compare policy subclasses rather than a before/after rerun of the production patch. Original q=8 results for DTLZ2 (3 objectives), DTLZ7, and Branin–Currin were collected on November 4; all remaining results are new. The report records source commits, runner hash, dependencies, and configuration. Historical runs used four workers and new runs eight, each with one CPU thread, so absolute runtime comparisons across batch sizes include different CPU contention. Within each q, the policies have equal observation budgets. q=4 also provides twice as many model updates as q=8.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

### Have you updated `CHANGELOG.md`?

Yes, under Unreleased / Fixed.

## Test Plan

- `python -m pytest -q tests/bofire/strategies/test_qparego.py tests/bofire/utils/test_multiobjective.py --runslow`: **49 passed**, including the slow pending-candidate cases.
- New regression cases cover q=1 and q=3 for all four acquisition choices; prescribed weights must prefer different objective-space trade-offs. They also verify that prediction is performed once per batch.
- A batch-generation test checks that existing pending points and all previously selected candidates reach each subsequent optimization.
- Confirmed that the regression fails with the original batch-construction path (`sample_simplex` called once instead of three times).
- Ruff lint/format and the repository's commit hooks pass. Targeted ty check passes with the pre-existing `redundant-cast` warning suppressed.
- Extracted the archived runs and regenerated the paired statistics; the resulting CSV is byte-identical to the published one.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf9c73b3c561`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
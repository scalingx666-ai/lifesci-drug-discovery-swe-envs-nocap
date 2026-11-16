# Issue

**Title:** Enable Coefficients for `DiscreteSumConstraint` and `from_simplex`

## Description

use-case motivated addition:
- `DiscreteSumConstraint` gets a `coefficients` that works akin to whats been done in the continuous constraint
- `from_simplex` gets a `simplex_coefficients` keyword that allows specifying coefficients for the simplex parameters. This is possible by changing the way the max/min incoming sums are assessed
- I'm using matrix multiplication `@` for `from_simplex` because we ensure by construciton that the incoming array is contiguous and does not have to be copied for a reshape and multiplication. This contiguousness is not guaranteed for `data[params]` in `get_invalid` in `DiscreteSumConstraint` so its more memory efficient to use per-column approaches in the assumption of a small countable amount of parameters (usually the case)
- The restriction that `values` of simplex parameters must be positive has been lifted (no longer needed)

**Unrelated optimization**
I also replaced the inner loop of `from_simplex` to use numpy and not pandas. This is also motivated by memory and time efficiency. This commit can be dropped tho if undesired, but there are singificant time and mem savings:

| Scenario | Rows | main time (s) | feature time (s) | Δ time | main mem (MB) | feature mem (MB) | Δ mem |
|---|---:|---:|---:|---:|---:|---:|---:|
| 4p × 11v | 1,001 | 0.025 | 0.005 | -81% | 0.3 | 0.2 | -48% |
| 6p × 11v | 8,008 | 0.068 | 0.005 | -93% | 4.1 | 1.6 | -62% |
| 8p × 11v | 43,758 | 0.280 | 0.010 | -96% | 32.9 | 10.8 | -67% |
| 6p × 21v | 230,230 | 0.904 | 0.019 | -98% | 137.3 | 46.2 | -66% |
| 6p × 21v boundary | 53,130 | 0.961 | 0.020 | -98% | 137.3 | 45.5 | -67% |

(p = simplex parameters, v = values)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e609fc5e6fdd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
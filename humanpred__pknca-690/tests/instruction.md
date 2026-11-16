# Issue

**Title:** fix(be): widen only the endpoints each expanding-limits guidance allows

## Description

## Summary

The EMA, Health Canada, and GCC frameworks widened the acceptance limits of every endpoint. Their guidances do not:

| Framework | Widened | Other endpoints | Source |
|---|---|---|---|
| EMA | Cmax (up to 69.84-143.19%) | 90% CI within 80.00-125.00% | EMA BE guideline Rev. 1, sections 4.1.8 and 4.1.10 |
| GCC | Cmax, EMA rules (replaces the old fixed 75.00-133.33%) | 80.00-125.00% | GCC guidelines v3.2 (2024), sections 3.1.8 and 3.1.10 |
| HC | AUC (up to 66.7-150.0%) | Cmax by its point estimate alone (80.0-125.0%, no CI) | HC HVDP policy (2018); Comparative Bioavailability Standards, section 2.1 |

FDA RSABE, NTID, and HVNTID are unchanged; they apply to both AUC and Cmax.

## Changes

- Each endpoint is classified by its PKNCA parameter concept (`peak_conc` or `auc`), and the framework's rule for that concept is applied.
- New `rule` column: the criterion each row's decision used (`ABE`, `ABEL`, `PE`, `RSABE`, `NTID`, or `HVNTID`). A widened endpoint below the 30% switch, and the FDA unscaled fallback, report `ABE`.
- New `widen_endpoints` argument: adds endpoints to each framework's own choice, for example `"ctrough"` for Ctau,ss of a modified-release product (EMA MR guideline, section 6.8.2.2).
- New `widen_default` argument: `FALSE` drops the framework's own choice, as when the protocol did not specify widening in advance.
- `be_compare()` applies both arguments to the expanding-limits frameworks only, and each framework adds `widen_endpoints` to its own choice.
- An endpoint that is not a PKNCA parameter keeps 80.00-125.00% under these frameworks, with a classed warning, unless it is named in `widen_endpoints`.
- Widened limits never narrow below 80.00-125.00%. The rounded k = 0.76 made them fractionally narrower for a within-reference CV just above 30%; PowerTOST does not clamp.
- The caption names each endpoint's rule and cites its source guidance.
- `be_regulator()` documents every framework's limits, with links to ICH M13A, the EMA, Health Canada, and GCC documents, and the FDA progesterone, warfarin, and dabigatran guidances.

This is a breaking change for EMA, HC, and GCC results; see NEWS.

## Testing

- New tests for each framework's rules, the Health Canada point-estimate rule, both arguments (including `be_compare()` across EMA, HC, GCC, and FDA), the clamp, factor endpoints, and the concept classification.
- Full test suite and R CMD check pass.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `191c27ac7583`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
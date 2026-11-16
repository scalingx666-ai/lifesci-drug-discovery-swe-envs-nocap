# Issue

**Title:** feat: add Tobit regression half-life estimation (hl_method = 'tobit')

## Description

Tobit regression treats BLQ observations as left-censored rather than discarding them, improving half-life accuracy when measurements fall below the LLOQ.

New function arguments for pk.calc.half.life():
  - lloq: required scalar or vector LLOQ when hl_method = "tobit"
  - hl_method: "log-linear" (default) or "tobit"; reads from PKNCA.options when not supplied, resolved via match.arg otherwise
  - tobit_n_points_penalty: exponent for n-point selection criterion
  - tobit_optim_control: list passed to stats::optim

New PKNCA options (underscore style):
  - hl_method (default "log-linear")
  - tobit_n_points_penalty (default 0)
  - tobit_optim_control (default list())

New NCA output columns:
  - tobit_residual, adj_tobit_residual (Tobit method only)
  - lambda.z.n.points_blq (BLQ point count; Tobit method only)
  - lambda.z.n.points counts all points for Tobit (including BLQ)

New internal functions: fit_half_life_tobit, fit_half_life_tobit_LL

Vignette v06-half-life-calculation-tobit fleshed out with worked examples, BLQ comparison, global option usage, and control parameters.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70f8dfbd9853`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
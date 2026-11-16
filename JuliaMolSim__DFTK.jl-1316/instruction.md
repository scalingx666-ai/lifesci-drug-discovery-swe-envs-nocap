# Issue

**Title:** Add breaks_TRS term predicate and guard compute_dynmat

## Description

## Summary

- Adds a `breaks_TRS` dispatch on term builders, mirroring the existing `breaks_symmetries`. Default is `false`; `Magnetic` and `Anyonic` are marked as breaking TRS.
- `compute_dynmat` now asserts that no term in the model breaks TRS. The phonon response solver folds the +q and −q Sternheimer equations into a single one at +q (with a factor of 2), which is only valid under TRS —  and Dal Corso, https://arxiv.org/abs/1906.11673.
- Documents the derivation of the dropped \`δψ̄·ψ\` term in \`compute_δρ\` from scratch (without going through χ₀): tracks the four Fourier components of \`δρ\`, picks out the +q part, and uses TRS (\`ψ_{−k} = ψ_k*\`) to identify the second +q contribution with the first, justifying the factor 2.

## Test plan

- [ ] `Pkg.test("DFTK"; test_args=["minimal"])` passes
- [ ] Existing phonon tests still pass (no Magnetic / Anyonic terms in those models)
- [ ] Confirm the assertion fires on a phonon-style call with a `Magnetic` term in the model

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77903d69d447`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
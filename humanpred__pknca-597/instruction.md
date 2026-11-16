# Issue

**Title:** docs: correct registry description strings to match the implementation

## Description

. Replaces #590, which predates the 40-character `desc` limit — its
replacement strings run 63–243 characters and conflict in 9 places.

- **`adj.r.squared.factor`** described itself as a factor multiplied by the
  number of data points and added to the adjusted r². The code instead accepts
  every regression whose adjusted r² is within `adj.r.squared.factor` of the
  best and picks the one using the most points. Built by `paste()` for
  `PKNCA.options()`, so not subject to the length limit.
- **`span.ratio`** described itself as half-life ÷ duration, the inverse of
  what `half.life.R` computes: `(max(time) - min(time))/half.life`. The roxygen
  for `pk.calc.half.life()` already had it right, so the registry string also
  contradicted the manual page.
- **The eight dose-aware `aucint*`/`aumcint*` parameters ending in `.dose`**
  described themselves as `AUCdn`/`AUMCdn`. Here `dn` means dose *normalized*
  (`auclast.dn`, `aucinf.obs.dn`), while these use dose-*aware* interpolation —
  as their own `pretty_name` has always said. All replacements fit in 40 chars.

The `aucint.inf`/`aumcint.inf` copy-paste that #590 also fixed is already
correct on main; the new tests pin it. Tests enumerate the parameter sets
rather than listing cases, so a newly added interval parameter is covered.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1149e17f6b71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
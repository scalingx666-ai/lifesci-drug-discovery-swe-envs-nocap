# Issue

**Title:** Secondary parameters: composed units and the vignette

## Description

Implements the plan's §6.4 (revised from §6.1 during review; issue 76), completing the four-phase secondary-parameters work:

- The units of a secondary result compose from the units of its actual sources, through the same units table and join as every other unit. Secondary result rows carry `<group column>_ref` columns naming the reference profile, and the units table gains reference-keyed rows: renal clearance reports `amountu/(timeu*concu)` with the concentration units of the plasma profile it used, and ratios and bioavailability report the own/ref quotient. When the quotient is dimensionally unitless, `PPSTRES`/`PPSTRESU` standardize it to `"fraction"`; when it is not (a `mg` dose against a `mg/kg` dose), the composite units say so instead of a silent `"fraction"`. Values are never converted or set `NA` for unit reasons, and a hand-supplied units table without `_ref` columns behaves exactly as today.
- A new vignette, "Secondary Parameters" (`v09`), works through the whole feature: linking intervals by hand, letting PKNCA derive the reference, steering it with `group_ref`, `interval_add_secondary()`, bioavailability and its AUC bases, exclusion propagation, composed units, and current limitations. "Writing PKNCA Parameter Functions" gains the `pknca_ref()` registration contract.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea7996fc5421`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
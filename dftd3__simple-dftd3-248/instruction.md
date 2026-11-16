# Issue

**Title:** Keep PySCF dispersion state consistent across molecule resets

## Description

PySCF dispersion corrections must track molecule changes during resets and scanner calls. No-argument resets currently clear the dispersion molecule, while Hessian resets are unimplemented.

- **Reset handling:** Preserve the molecule on no-argument energy resets; propagate Hessian resets through the mean-field base. Gradient resets use the existing base propagation.
- **Regression coverage:** Cover all three wrappers and compare energy/gradient scanners against fresh calculations after geometry changes.

<!-- START COPILOT CODING AGENT SUFFIX -->

-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4db8e3ee1a5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
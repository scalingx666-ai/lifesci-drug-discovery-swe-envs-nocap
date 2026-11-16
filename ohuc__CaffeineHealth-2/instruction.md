# Issue

**Title:** Add optional SNP genotypes, hormonal status, and editable health profile

## Description

Allow users to optionally provide CYP1A2 and AHR genotype data and hormonal status (pregnancy trimester / hormonal contraceptives) to refine caffeine half-life estimates using a multiplicative PK model.

All onboarding health factors (age, weight, smoking, medications, etc.) are now persisted and editable directly from Settings > Caffeine Profile without re-running onboarding. Changing any factor recomputes the derived half-life and sleep threshold.

Other improvements:
- Weight input supports direct text entry in addition to +/- stepper
- Hormonal contraceptives synced bidirectionally between medications and hormonal status selections to prevent double-counting

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c4ebd2ebd5db`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
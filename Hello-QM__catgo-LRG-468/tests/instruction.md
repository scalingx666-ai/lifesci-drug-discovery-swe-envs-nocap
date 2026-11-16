# Issue

**Title:** fix(lammps): any unknown section header ends the current section

## Description

— with coordinates fixed, the kerogen file rendered but with absurd elements (**He₁₀₄₆₄Te₂₁₆Sb₂₁₆Cd₂₁₆In₇₂H₄₈** instead of C/H/O/N).

## Root cause

The section scanner recognized only Masses/Atoms/Bonds/Angles/Dihedrals/Impropers. `Pair Coeffs` (present in every force-field `write_data` output) didn't reset `current_section`, so its rows kept feeding the Masses parser — the LJ **sigma column (~3.5) overwrote every atom mass**, and mass→element mapped everything to He/heavy junk (Bond/Angle Coeffs magnitudes → Te/Sb/Cd).

## Fix

Any other capitalized section header (`Pair Coeffs`, `Bond Coeffs`, `Velocities`, …) resets the section. Title lines can't match (they contain digits/punctuation).

## Verification

Regression test: Masses + Pair Coeffs interference keeps O/C. Full suite: 4,410 pass. Kerogen legend now C/H/O/N (browser-verified below).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `729fe4ed5cd4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
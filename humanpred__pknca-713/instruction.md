# Issue

**Title:** Accept mcg as a unit, an alias of ug

## Description

Concentration, dose and amount units spelled with mcg (for example "mcg/mL") stopped unit conversion, because udunits knows ug but not mcg: converting "min*mcg/mL" to "hr*ng/mL" failed with "'mcg' is not recognized by udunits".

Loading PKNCA now installs mcg as an alias of ug, beside the existing "fraction" unit, through the new internal pknca_install_units(). It does nothing when mcg is already defined, and reinstalling the same definition is a no-op, so loading twice is safe. units::install_unit() changes the udunits database of the whole R session, so mcg is then available to every package that uses units (as are its SI-prefixed forms, which udunits derives for any installed unit); the NEWS bullet and the unit-conversion vignette say so.

Tests pin the factors mcg/mL to ng/mL (1000), mcg to ug (1) and min*mcg/mL to hr*ng/mL (1000/60), a units table with concu mcg/mL and preferred units, and a repeat install.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4d5a7365f7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add excretion rate parameters

## Description

## Description
- Defined the calculation of Excretion Rate parameters and used column `conc.duration`  for rate calculations. The functions are: `pk.calc.ertmax`, `pk.calc.ermax` and `pk.calc.ertlst`
- Refactored checking for missing volume and conc in `pk.calc.ae` and used it for the new functions created
- Created tests with 100% coverage

## Definition of Done
- [ ] Tmax excretion rate: "ERTMAX", "Time of Max Excretion Rate"
- [ ] Max excretion rate: "ERMAX", "Max Excretion Rate" ( = Amount excreted / Time (end - start))
- [ ] ~~Midpoint last:     "MIDPTLST", "Midpoint of Collection Interval"~~ `ERTLST`, "Midpoint of Interval of Last Nonzero ER"

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8f3d1f62dd4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
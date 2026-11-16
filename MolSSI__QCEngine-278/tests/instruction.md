# Issue

**Title:** adds gcp harness

## Description

<!-- Thank you for your contribution! -->

## Description
Adds harness for the `gcp` program that calculates a geometrical counter poise correction.
The method's parametrization depends on the basis set and (to a less extent) on the Hamiltonian (HF or DFT).
The manual or help from the binary lists what combinations are available. The gCP part for the `3c` correction is also accessible (method = `hf3c` or `pbeh3c`). Minimal example:
```
task = qcel.models.AtomicInput (
    molecule= mol,
    driver="gradient",
    model={"method": "HF/SV"},
)
 qcengine.compute(task,"gcp")
```

There are already some provisions in place for a planned update of the `gcp` code for a smoother interoperability (version output, better custom param file support). Note that the current, uncommon version `2.02` gets changed to `2.2` somewhere.

## Changelog description
Addition of `gcp` harness.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] tests added
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6adbccc2a3d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
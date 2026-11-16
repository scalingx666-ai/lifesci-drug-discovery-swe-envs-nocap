# Issue

**Title:** add procedure for pyberny geometry optimizer

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Following a discussion with @dgasmith, this PR adds a procedure for the [pyberny](https://github.com/jhrmnn/pyberny) geometry optimizer.

The PR is functional, the following test case runs sucessfully:

```python
import qcelemental as qcel
import qcengine as qcng

mol = qcel.models.Molecule(
    geometry=[[0, 0, 0], [0, 1.5, 0], [0, 0, 1.5]], symbols=["O", "H", "H"], connectivity=[[0, 1, 1], [0, 2, 1]]
)
opt_input = {
    "keywords": {"program": "mopac"},
    "input_specification": {"driver": "gradient", "model": {"method": "PM7"}},
    "initial_molecule": mol,
}
opt = qcng.compute_procedure(opt_input, "berny")
print(opt)
```

However, the PR is still a work in progress. The following needs to be resolved before merging, and I would welcome input from the QCEngine maintainers:

- [x] there is a lot of boilerplate shared with `GeometricProcedure`. `found()`, `build_input_model()`, `Config`, also it seems that if we have `found`, there should be no need to check for the presence of the package in `compute()` again. Is this necessary?
- [x] how to handle logging? Currently Berny logs verbosly, and this is adjustable by passing appropriate argumetns. How is this handled in QCEngine in general? (Pyberny doesn't use the `logging` module, but I can change that if QCEngine would prefer that.)
- [x] where to store paramters for Berny?


## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Added a new geometry optimizer: [pyberny](https://github.com/jhrmnn/pyberny)

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43441eb945ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
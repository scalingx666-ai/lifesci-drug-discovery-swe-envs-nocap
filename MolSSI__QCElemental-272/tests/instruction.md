# Issue

**Title:** add return_gradient property

## Description

<!-- Thank you for your contribution! -->

## Description
When one runs a driver=energy, the energy is available through the return and the `atres.properties["return_energy"]`. For driver=gradient, the gradient is returned and the corresponding energy is still available in properties but not the grad. For driver=hessian, there's no place at all for the gradient if available. This rounds out the return fields in properties. There was discussion of this at some point, but I can't find it in qcsk, qcel, or qcng repos.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e8728d360e6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
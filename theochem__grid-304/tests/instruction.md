# Issue

**Title:** PR1 :  implement analytical Coulomb potential for Gaussian densities

## Description

First inital PR for Improvement of the robustness of poisson equation . 
This PR implements the core mathematical engine for evaluating the exact analytical electrostatic (Coulomb) potential of $s$-type and $p$-type radial Gaussian charge densities. The math is derived from the exact formulations and $r \to 0$ limits outlined in the course project reference (https://qchem.qc-edu.org/problems/HF_dft.html). This PR contains the standalone `coulomb.py` module and an isolated unit test suite validating math correctness across various distances and normalization schemes, establishing the foundation for the subsequent robust Poisson solver scaffolding.
related to issue ->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa06fb496ef3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
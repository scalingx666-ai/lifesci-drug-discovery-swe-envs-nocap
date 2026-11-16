# Issue

**Title:** Fix Psi4NumPy-Basics Typos

## Description

## Description
Fixes a few simple typos I found in the Psi4NumPy-Basics tutorial.

## What are your new additions? Please provide a brief list.
* **New Features**
  - None
* **Changes**
  - [x] [1d](https://github.com/kcpearce/psi4numpy/blob/master/Tutorials/01_Psi4NumPy-Basics/1d_wavefunction.ipynb) - wfn.nalpha() to h2o.nalpha() to match example
  - [x] [1d](https://github.com/kcpearce/psi4numpy/blob/master/Tutorials/01_Psi4NumPy-Basics/1d_wavefunction.ipynb) - wfn.Fa() to wfn.Fb()
  - [x] [1e](https://github.com/kcpearce/psi4numpy/blob/master/Tutorials/01_Psi4NumPy-Basics/1e_mints-helper.ipynb) - fixes O(N^2) inline latex rendering for Github
  - [x] Update links to Crawford's Programming Projects
## Any questions for the community?
- [x] I found an instance of a latex equation rendering issue [here](https://github.com/kcpearce/psi4numpy/blob/master/Tutorials/01_Psi4NumPy-Basics/1f_tensor-manipulation.ipynb). The issue seems to arise because Github doesn't like the multi-line latex aligned equations. While they are rendered correctly when opened as an iPython notebook, Github does not render them correctly. Maybe it doesn't matter that they are not rendering correctly on Github, but I figured it would look cleaner if they rendered correctly on both. Any idea why GH has trouble rendering in this instance, but has no problem with analogous multi-line latex equations in many other places (e.g. [here](https://github.com/kcpearce/psi4numpy/blob/master/Tutorials/03_Hartree-Fock/3a_restricted-hartree-fock.ipynb))?

## Status
- [x] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `066f378f2624`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
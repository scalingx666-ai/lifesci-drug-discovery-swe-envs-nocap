# Issue

**Title:** Index Kernel

## Description

DevPR, parent is #745 

Adds the `IndexKernel` and `PositiveIndexKernel` classes

The new factory design added in #746 offers full customization of the GP, following a composition approach. To reach the full potential that this offers, having BayBE `IndexKernel` classes to let the user to construct custom architectures is the natural next step, in particular because there other reasonable choices than just having the standard ICM product, such as: 
* Selecting the type of index kernel (e.g. regular vs positive)
* Implementing multi-fidelity approaches ()
* Creating kernels that can handle multiple task parameters

In addition:
* It finally provides an interface for configuring the kernel itself, e.g. its rank (which used to be a TODO for ages)
* And it offers the new parameter-named BayBE for conveniently specifying active dimensions for the above tasks.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8732a0f805bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
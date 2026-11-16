# Issue

**Title:** Fix parallel execution of gmx_MMPBSA

## Description

**Description of the error**

`mpirun -nt 12 gmx_MMPBSA (...)` runs well in the frontend but if `ssh` to a node, the same command fails because how the node is set and its architecture. Raising the MPI error:

> (...)
> Either request fewer slots for your application, or make more slots
> available for use.
> (...)

Basically we were asking for physical cores that were not available on the node.

**Changed**

- Switch to logic process core instead of physical ones with the flag `--use-hwthread-cpus` on MPI execution of `gmx_MMPBSA`
- On SLURM configuration from `cpus-per-task={threads}` to `ntasks: {threads}  cpus-per-task=1`. Now MPI detect `ntasks` as "slots".

**Added**

- Prompt the error in case `gmx_MMPBSA` still fails.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f07a39a2a46b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** feat: add heavy atom count support ('#') to AtomCountDescriptor

## Description

Adds the ability to calculate the Heavy Atom Count directly via AtomCountDescriptor using the '#' parameter, which safely excludes pseudo-atoms and hydrogens.

Also includes a few minor cleanups:
Minor updates to javadoc
Switched tests to use SilentChemObjectBuilder
Added testHeavyAtomCount to verify exclusion of explicit H and pseudo-atoms

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a5c46c4613f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
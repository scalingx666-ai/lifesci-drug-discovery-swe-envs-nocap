# Issue

**Title:** Synthon space shape search: use new optimizer option

## Description

#### Reference Issue
No issue.

#### What does this implement/fix? Explain your changes.
In the synthon shape search, a hit is first built from the hit synthons as they are left aligned with the fragments.  It now uses the new conformation optimiser to refine the torsions before using it.

#### Any other comments?

There was never a test using bestHits=false.  I have used it here to show that the initial hit geometry is frequently useful for a relatively much quicker search.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fbb0f798a5d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
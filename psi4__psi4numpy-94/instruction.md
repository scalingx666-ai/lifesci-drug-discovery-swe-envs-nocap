# Issue

**Title:** LCCSD

## Description

## Description
Adds LCCSD for @loriab. I've tested RHF with and without FC against `fnocc`. I have _not_ done UHF tests because `fnocc` can't do that and no other module in Psi knows `lccsd`, but it should be correct. Because this is a spinorbital code, the difference between RHF and UHF is only in the integrals, and if the integrals were wrong, we'd see UHF/LCCD behave badly. (Which was exactly the case in my last PR.)

For future reference: `fnocc` assumes you have canonical orbitals. Disagreements between my implementation and `fnocc` in that case are expected.

## What are your new additions? Please provide a brief list.
* **New Features**
  - [x] LCCSD

## Status
- [x] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `efe51de4ce2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
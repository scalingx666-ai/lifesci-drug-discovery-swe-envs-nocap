# Issue

**Title:** DF-LCCSD

## Description

## Description
The second to last one on my list for @loriab. What I found out only at the end was that Psi doesn't actually _have_ a DF-LCCSD implementation. While Psi will not complain if you set `cc_type` to be `DF` and request `lccsd`, `proc.py:run_cepa` never actually checks `cc_type` before sending you to `fnocc`, so the computation proceeds using conventional integrals.

Accordingly, I test my reference implementation against the value I got when I constructed the DF integrals as four-index quantities and applied the tested conventional code. It's not an ideal test, but it'll do.

## What are your new additions? Please provide a brief list.
* **New Features**
  - [x] DF-LCCSD

## Status
- [x] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9646f2d8238`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Remove old ForwardDiff complex workarounds

## Description

Checklist to be examined:
- [x] power
- [x] exp
- [x] erfc
      - has to stay for now
- [x] ForwardDiff.value(::Complex{<:Dual})
      - has to stay for now

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f9afe769b0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
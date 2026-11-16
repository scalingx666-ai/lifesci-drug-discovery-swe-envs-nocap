# Issue

**Title:** Replace inconsistent norm threshold with explicit zero check

## Description

Addresses review feedback on #324 regarding the `norm < 1e-7_wp` threshold being inconsistent with `eps_norm` (~1e-154 for double precision).

After the norm inversion guard, `norm` is either 0.0 or an inverted value (1.0/norm). The condition `norm < 1e-7_wp` only catches the zero case, making it redundant.

**Changes:**
- Replace `norm < 1e-7_wp` with `norm == 0.0_wp` in d4.f90 (lines 302, 320)
- Replace `norm < 1e-7_wp` with `norm == 0.0_wp` in d4s.f90 (lines 304, 317)

```fortran
! Before
if (is_exceptional(gwk) .or. norm < 1e-7_wp) then

! After
if (is_exceptional(gwk) .or. norm == 0.0_wp) then
```

<!-- START COPILOT CODING AGENT TIPS -->
---

💬 We'd love your input! Share your thoughts on Copilot coding agent in our [2 minute survey](https://gh.io/copilot-coding-agent-survey).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0bec7fe996f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
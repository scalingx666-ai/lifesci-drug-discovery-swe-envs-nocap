# Issue

**Title:** Fix #1174. We need better logic when the ring closures are near exten…

## Description

…ded tetrahedral inserting the implicit neighbours in two different locations.

```
C(=[C@]=CBr)F.C1=[C@]=CBr.F1.F1.C1=[C@]=CBr.C([H])(F)=[C@]=CBr
```

Before:

![image](https://github.com/user-attachments/assets/b11c31ef-85fd-480f-94c2-741c4a00ee41)

After:

![image](https://github.com/user-attachments/assets/12bb529c-7726-405b-a4ee-747a832aae74)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81e1afce98bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
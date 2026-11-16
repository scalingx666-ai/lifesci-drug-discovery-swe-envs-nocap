# Issue

**Title:** Improve ionic bond depictions - fixes https://github.com/cdk/depict/i…

## Description

…ssues/26 and 

We now only create ionic bonds if the charged atom has less than 3 connected bonds - otherwise we are almost certainly going to have a lot of congestion. When laying out components we prefer to depict the positively charged component first.

<img width="229" height="80" alt="image" src="https://github.com/user-attachments/assets/deb78a78-b570-4a1f-92eb-45668153eb66" />


<img width="282" height="99" alt="Screenshot 2026-03-03 at 13 13 42" src="https://github.com/user-attachments/assets/7f51abd8-ce73-4d66-bf01-6a49728507ec" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c21d5b211f4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
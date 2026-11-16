# Issue

**Title:** Dial in the alignment of components above/below the arrow.

## Description

Took a bit of trail and error but better now. I noticed we were slightly off center:

<img width="414" height="85" alt="rxn_FORWARD" src="https://github.com/user-attachments/assets/b927361b-915f-42f3-a54b-6057fb6566c6" />

Fix that and given the feedback from discord I now account for the arrow heads so they move left/right depending on that.

Nudged Slightly Back:
<img width="414" height="85" alt="rxn_FORWARD" src="https://github.com/user-attachments/assets/1596453e-ef3f-433a-a0ed-cee1346892e1" />
Nudged Slightly Forward:
<img width="414" height="85" alt="rxn_BACKWARD" src="https://github.com/user-attachments/assets/7beef10e-f1a3-48eb-aa80-61e97be05ab9" />
Dead Center:
<img width="414" height="85" alt="rxn_BIDIRECTIONAL" src="https://github.com/user-attachments/assets/3512c8e3-9068-4c22-8767-2fead3e42fa7" />
<img width="414" height="85" alt="rxn_RESONANCE" src="https://github.com/user-attachments/assets/9e12b2d5-2260-4b94-9ada-8eeb6b542a61" />

Also made sure it works when we have multiple columns.

<img width="425" height="85" alt="rxn_FORWARD" src="https://github.com/user-attachments/assets/db592812-583b-4da4-b44d-626deb4a2198" />
<img width="425" height="85" alt="rxn_BACKWARD" src="https://github.com/user-attachments/assets/51299f53-c33a-4c01-8291-6da84a1b0766" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d12b2fc99198`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
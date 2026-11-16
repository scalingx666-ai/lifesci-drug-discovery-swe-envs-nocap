# Issue

**Title:** Generalise the code for placing the reaction condition text to one wh…

## Description

…ich allows molecules to be placed below the arrow in a reaction.

Molecules are tagged with a property (PLACE_BELOW_ARROW) which tells the layout which ones should go below.

# All Above (default)

<img width="438" height="121" alt="all-above" src="https://github.com/user-attachments/assets/0fb58872-8515-421c-923c-61d8fdb3376a" />

# All Below

<img width="438" height="121" alt="all-below" src="https://github.com/user-attachments/assets/0933b8b0-3ac5-476a-8b2d-4f3a643ef3a1" />

# One above / below

<img width="438" height="102" alt="all-below-b" src="https://github.com/user-attachments/assets/609bd285-2ebb-40c3-b187-be238fd4e22d" />
<img width="438" height="102" alt="all-below-a" src="https://github.com/user-attachments/assets/2b0aa017-8be6-4c57-9b44-96ba54008243" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b32f06f30eb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
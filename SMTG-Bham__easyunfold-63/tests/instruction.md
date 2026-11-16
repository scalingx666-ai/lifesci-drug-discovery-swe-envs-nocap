# Issue

**Title:** Plotting updates

## Description

This is a minor update to improve plotting aesthetics, including:
- Non-duplication of y-axis label for spin-polarised plotting
- Fixing a minor inaccuracy in the x-axis 
- Fixing the placement of the legend with spin-polarised plotting, with atoms/orbitals projections
- Adds titles for spin up/down so users know why two plots are shown

(Note that this does not solve @Iamkeli's issues in  – can you please have a look at this when you get a chance @zhubonan)

e.g. spin titles:
![image](https://github.com/user-attachments/assets/2aa90818-5e0e-41a9-a230-0cb3a2aaba24)


e.g. x-axis fix:
![image](https://github.com/user-attachments/assets/d6e50999-2abe-4abc-9ed6-5682779ffc9a)
![image](https://github.com/user-attachments/assets/295b42d2-2abd-4cc7-b519-fdce6934be0d)

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

- **Improvements**
  - Plot titles now consistently indicate spin channels when multiple spins are present.
  - Axis labeling is streamlined, reducing redundant y-axis labels in multi-spin plots.
  - X-axis limits are more accurately aligned with data indexing.
  - Legends in projected plots are better placed and only shown when appropriate.
  - Layout adjustments ensure legends and plots are displayed clearly.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4dc31a5f3c5d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
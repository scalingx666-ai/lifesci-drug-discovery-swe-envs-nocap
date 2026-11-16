# Issue

**Title:** Small ring path utility

## Description

We have efficient ways of ad-hoc querying the smallest ring size, this adds the option to fetch the path of bonds that form that ring.

This is extremely useful for something like the large cyclophane structure added in the test. We can generate coordinates but we can't render it (yet) due to some algorithms that need optimising. This is a step for that.

Note coordinates we generate aren't as good as the original but currently we can't even render the pre-laidout structure:

<img width="1508" height="2583" alt="image" src="https://github.com/user-attachments/assets/87d752a6-ea22-4ccc-a1fb-f5c087085e6f" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d12b2fc99198`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
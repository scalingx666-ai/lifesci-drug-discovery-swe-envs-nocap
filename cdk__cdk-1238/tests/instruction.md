# Issue

**Title:** Exhaustive fragmenter fix and improvements

## Description

#### Fix for Saturation Issues in `ExhaustiveFragmenter` ()

Aims to resolve the saturation-related issues in the [`ExhaustiveFragmenter`](tool/fragment/src/main/java/org/openscience/cdk/fragment/ExhaustiveFragmenter.java), as described in issue .  

#### Fixes & Improvements

Correct Fragment Saturation:
- the generated fragments are now explicitly copied, preventing unintended modifications
- added the ability to set and control the saturation state of returned fragments
- added setting to preserve stereochemistry

Bond Splitting Logic:
- improved performance by splitting a specific combination of bonds only once
- usage of new cycle detection which runs only once
- added setting of a maximum tree depth to regulate the upper limit of bonds that will be split

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `834d1ebbd3cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix optplot superscript

## Description

Example of old optplot output:
<img width="343" alt="Screenshot 2023-03-29 at 12 42 17" src="https://user-images.githubusercontent.com/1330638/228524862-f15d3388-1275-4f75-aa0b-c4f1bfff8f31.png">


Example of fixed output:
<img width="340" alt="Screenshot 2023-03-29 at 12 41 49" src="https://user-images.githubusercontent.com/1330638/228524756-b58d357d-885f-45b0-b846-557328f211f2.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `575996ed11ef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
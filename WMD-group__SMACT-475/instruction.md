# Issue

**Title:** Change Dependabot update schedule to daily

## Description

Changed the update schedule for GitHub Actions and pip dependencies from monthly to daily, and set the open pull requests limit to 10.


<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

## Release Notes

* **Chores**
  * Dependabot will now check for dependency updates daily rather than monthly.
  * Implemented a limit of 10 concurrent open dependency update pull requests.

<sub>✏️ Tip: You can customize this high-level summary in your review settings.</sub>

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b3cdf61e47a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
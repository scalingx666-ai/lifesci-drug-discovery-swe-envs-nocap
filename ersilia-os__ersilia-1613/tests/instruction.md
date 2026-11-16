# Issue

**Title:** update test workflows for ersilia cli

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [ ] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**

I am modifying the CICD tests that happen at PR and push in Ersilia with some improved rationale. To avoid overwriting, I have merged in a new file ersilia-test.yml the previous pr_check and test_and_cleanup yml files

**Changes to be made**

Revise we are not missing any key test and the triggering of workflows follows a better rationale (for example no workflow is activated if ruff is failing

**Status**

Ready for review

**To do**

Revise the nox jobs @Abellegese I did not want to modify those.

Is this pull request related to any open issue? If yes, replace issueID below with the issue ID

Related to #<issueID>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3342677f8aba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
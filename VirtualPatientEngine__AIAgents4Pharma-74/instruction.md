# Issue

**Title:** Feat/parameter scan

## Description

# For authors

## Description

https://github.com/user-attachments/assets/b7712063-f4be-4880-8003-f6ef9f9a69f4

This PR introduces a new `parameter_scan` tool. Please take a look at the demo video above. When an incorrect parameter name is provided (e.g., `kIL6RBIND` instead of `kIL6RBind`), the agent invokes the `get_modelinfo` tool to extract the correct parameter name and automatically reinvokes `parameter_scan`. This behaviour is demonstrated in the demo and supported by tests. Additionally, when a non-existent species name or parameter is entered (for example `AB` instead of `Ab{serum}`), the agent notifies the user of the error and suggests valid alternatives from the model. These features enable the agent/tool to handle minor inaccuracies intelligently and provide helpful feedback when corrections are not possible.

## Fixes # (issue) NA

## Type of change
Please delete options that are not relevant.
- [ ] Bug fix (non-breaking change which fixes an issue)
- [X] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [X] This change requires a documentation update

## How Has This Been Tested?
Please describe the tests you conducted to verify your changes. These may involve creating new test scripts or updating existing ones.
- [ ] Added new test(s) in the ```tests``` folder
- [X] Added new function(s) to an existing test(s) (e.g.: ```tests/testX.py```)
- [ ] No new tests added (Please explain the rationale in this case)

## Checklist
- [X] My code follows the style guidelines mentioned in the Code/DevOps guides
- [X] I have commented my code, particularly in hard-to-understand areas
- [X] I have made corresponding changes to the documentation (e.g. MkDocs)
- [X] My changes generate no new warnings
- [X] I have added or updated tests (in the ```tests``` folder) that prove my fix is effective or that my feature works
- [X] New and existing tests pass locally with my changes
- [X] Any dependent changes have been merged and published in downstream modules

# For reviewers

## Checklist pre-approval
- [ ] Is there enough documentation?  
- [ ] If a new feature has been added, or a bug fixed, has a test been added to confirm good behavior?
- [ ] Does the test(s) successfully test edge/corner cases?
- [ ] Does the PR pass the tests? (if the repository has continuous integration)

## Checklist post-approval
- [ ] Does this PR merge ```develop``` into ```main```? If so, please make sure to add a prefix (feat/fix/chore) and/or a suffix BREAKING CHANGE (if it's a major release) to your commit message.
- [ ] Does this PR close an issue? If so, please make sure to descriptively close this issue when the PR is merged.

## Checklist post-merge
- [ ] When you approve of the PR, merge and close it (Read this [article](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/about-merge-methods-on-github) to know about different merge methods on GitHub)
- [ ] Did this PR merge ```develop``` into ```main``` and is it suppose to run an automated release workflow (if applicable)? If so, please make sure to check under the "Actions" tab to see if the workflow has been initiated, and return later to verify that it has completed successfully.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1da9c0a3f979`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
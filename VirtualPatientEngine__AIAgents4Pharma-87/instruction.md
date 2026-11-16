# Issue

**Title:** fix: enhance exploration

## Description

# For authors

## Description

https://github.com/user-attachments/assets/e0dfb9c0-3e30-4fc8-9608-78ecdea34603

In this PR, I'd like to introduce two key improvements to make the agent more exploration-friendly, catering to users who may not be familiar with a model and may nevertheless wish to explore its contents.

1. Users can now enter abstract keywords instead of exact species names to retrieve relevant annotations (`get_annotation` tool). Implemented structured LLM output parsing to extract species names from abstract queries.
2. Previously, when queried for species or parameter information, the agent (`get_modelinfo` tool) returned only names. With this update, the agent can now also return initial concentration/value, compartment, and units for species and parameters.

## Fixes # (issue)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3363ccae69da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
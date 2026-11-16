# Issue

**Title:** fix: npm json bump

## Description

# For authors

## Description
npm lock file issue

## Fixes # (issue) Mention the issue number.

## Type of change
Please delete options that are not relevant.
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [x] This change requires a documentation update

## How Has This Been Tested?
Please describe the tests you conducted to verify your changes. These may involve creating new test scripts or updating existing ones.
- [ ] Added new test(s) in the ```tests``` folder
- [ ] Added new function(s) to an existing test(s) (e.g.: ```tests/testX.py```)
- [x] No new tests added (Please explain the rationale in this case)

## Checklist
- [x] My code follows the style guidelines mentioned in the Code/DevOps guides
- [x] I have commented my code, particularly in hard-to-understand areas
- [x] I have made corresponding changes to the documentation (e.g. MkDocs)
- [x] My changes generate no new warnings
- [x] I have added or updated tests (in the ```tests``` folder) that prove my fix is effective or that my feature works
- [x] New and existing tests pass locally with my changes
- [x] Any dependent changes have been merged and published in downstream modules

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60a7007f3aaf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
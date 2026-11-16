# Issue

**Title:** feat: add cpu fallback T2KG

## Description

# For authors

## Description
Added the CPU fallback for T2KG subgraph extraction's backend, now supports both CPU and GPU, added dynamic detection, based on the hardware and chooses the appropriate index and similarity metric

#### GPU Mode
<img width="827" height="546" alt="image" src="https://github.com/user-attachments/assets/afc0ca08-0a13-4f55-8e5a-f99d4497c6ac" />


#### CPU Mode
<img width="826" height="510" alt="image" src="https://github.com/user-attachments/assets/37809d11-f429-45fb-8f59-c5af973ca96a" />

#### Added streaming support
<img width="1570" height="753" alt="image" src="https://github.com/user-attachments/assets/2452400a-d06e-48b6-a84e-a9b9e2ff8c95" />


## Fixes # (issue) Mention the issue number.
#248 

## Type of change
Please delete options that are not relevant.
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [x] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [x] This change requires a documentation update

## How Has This Been Tested?
Please describe the tests you conducted to verify your changes. These may involve creating new test scripts or updating existing ones.
- [x] Added new test(s) in the ```tests``` folder
- [x] Added new function(s) to an existing test(s) (e.g.: ```tests/testX.py```)
- [ ] No new tests added (Please explain the rationale in this case)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `03aa8eeb758c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
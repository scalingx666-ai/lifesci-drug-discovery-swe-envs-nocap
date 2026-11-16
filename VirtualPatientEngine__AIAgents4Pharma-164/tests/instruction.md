# Issue

**Title:** Fix/aiagents4pharma docker pipeline

## Description

# For authors

<img width="799" alt="image" src="https://github.com/user-attachments/assets/8848a347-0f67-4531-88df-97760084f245" />

###### The pipeline was tested on my fork

## Description
Please:

This PR improves the Docker CI/CD pipeline by:

- Adding `app/` to the `paths-filter` and build conditions so all containers rebuild on shared code changes
- Adding dependency awareness: `talk2aiagents4pharma` now rebuilds if its own code, or any of its dependencies (`talk2biomodels`, `talk2knowledgegraphs`, or `app/`) change
- Fixing missing `app` output in the `changes` job
- All containers are now configured to rebuild when changes are detected in the shared `app/` directory.
- Removing `push` and `workflow_dispatch` to enforce release-driven automation
- Removing `short_sha` and `-dev` tags to simplify versioning
- Restricting builds to run **only after the `RELEASE` workflow**

###  **Why**
To avoid unnecessary builds, enforce consistent tagging, and ensure containers are rebuilt when shared or dependent modules are updated.

###### In the app/frontend/t2s  - I just fixed the sorted the imports to trigger the pipeline - no code changes were made(I use neovim, it has plugin which on saving the file sorts the import) - I also formatted the other streamlit apps, but I reverted the changes just to avoid any confusion, and only made changes to t2s

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `491ada2902cd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
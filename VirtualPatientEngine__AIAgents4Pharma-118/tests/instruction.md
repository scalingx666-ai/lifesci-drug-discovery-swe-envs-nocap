# Issue

**Title:** Feat/talk2scholars docker update

## Description

# For authors

<img width="1786" alt="image" src="https://github.com/user-attachments/assets/a455b5a7-c739-48fe-96cd-cb5a863b8f1a" />

##### Both Build and tested locally

## Description

This pull request introduces Docker support for the `talk2scholars` module, aligning it with the existing `talk2biomodels` setup. The changes include:

1. **Added a Dockerfile for `talk2scholars`**
   * Uses `python:3.12-slim` as the base image
   * Installs required dependencies, including `g++` and `build-essential` for compiling `pcst_fast`
   * Exposes port `8501` for Streamlit
   * Configures environment variables to be passed at runtime for security
   * Preventing API key exposure by passing them at runtime instead of storing them in the Dockerfile

---
#### Additional features on request of @gurdeep330 -> Please check the conversation thread below
2. **Enhanced GitHub Actions (`ci.yml`) for improved CI/CD**
   * Added trigger to automatically run after the RELEASE workflow completes
     * This ensures Docker images are built whenever a new version is released
     * Maintains backward compatibility with existing triggers (push, PR, manual)
   
   * Implemented module-specific build jobs with path filtering
     * Separate build jobs for `talk2biomodels` and `talk2scholars`
     * Only builds Docker images for modules that have been modified
     * Uses `dorny/paths-filter` to detect changes in specific directories
   
   * Added automatic versioning for Docker images
     * Uses semantic versioning from git tags for release builds
     * Adds both version tags and `latest` tags to all images
     * Includes git commit SHA in image tags for traceability
---

3. **Updated `README.md`**
   * Documented setup instructions for both `talk2biomodels` and `talk2scholars`
   * Running containers persistent and detached(-d) mode
   * Provided example commands for pulling and running the images

## Context and Motivation

The goal of this update is to streamline the deployment process for both `talk2biomodels` and `talk2scholars`, ensuring a consistent and scalable setup. By integrating `talk2scholars` into the CI/CD pipeline, the module can now be built and deployed automatically alongside `talk2biomodels`.

The enhanced CI workflow improves efficiency by only building Docker images for modules that have changed and automatically handling versioning, reducing maintenance overhead and ensuring consistency across releases.

## Dependencies

* Environment variables (`OPENAI_API_KEY`, `ZOTERO_API_KEY`, `ZOTERO_USER_ID`, `NVIDIA_API_KEY`) must be set when running the container.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3282e5549b27`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fix: CTD conversion to PubChem CID

## Description

# For authors

## Description

This PR introduces a fallback mechanism for resolving PubChem CIDs from CTD IDs in cases where direct mapping via the PubChem API fails. The updated approach includes the following enhancements:

#### Fallback Mapping Using CAS RN
1. Download the [CTD_chemicals](https://ctdbase.org/downloads/#allchems) file from the CTD database, which includes CTD IDs along with their associated CAS Registry Numbers (CAS RNs), when available.
2. Use the PubChem API to convert CAS RN to PubChem CID.
3. Compounds for which both direct and fallback conversions fail will be ignored.

#### Replace PubChemPy with PubChem API for SMILES Retrieval
1. While PubChemPy works well for most compounds, it occasionally fails to return the SMILES representation.
2. To improve reliability, we now use the PubChem REST API to fetch SMILES strings directly.

These changes are expected to enhance the accuracy of chemical identifier mapping and SMILES retrieval (please refer to the updated notebook).

## Fixes # (issue) None

## Type of change
Please delete options that are not relevant.
- [ ] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] This change requires a documentation update

## How Has This Been Tested?
Please describe the tests you conducted to verify your changes. These may involve creating new test scripts or updating existing ones.
- [ ] Added new test(s) in the ```tests``` folder
- [ ] Added new function(s) to an existing test(s) (e.g.: ```tests/testX.py```)
- [ ] No new tests added (Please explain the rationale in this case)

## Checklist
- [ ] My code follows the style guidelines mentioned in the Code/DevOps guides
- [ ] I have commented my code, particularly in hard-to-understand areas
- [ ] I have made corresponding changes to the documentation (e.g. MkDocs)
- [ ] My changes generate no new warnings
- [ ] I have added or updated tests (in the ```tests``` folder) that prove my fix is effective or that my feature works
- [ ] New and existing tests pass locally with my changes
- [ ] Any dependent changes have been merged and published in downstream modules

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `895c4e531bb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** feat: simulate and query multiple models

## Description

# For authors

## Description

https://github.com/user-attachments/assets/8d01d099-350c-497f-898f-1f97dc56e434

This PR introduces the capability to simulate and query multiple models within T2B. Key updates include enhancements to the state key `dic_simulated_data`, which now stores the results of all simulations conducted by the user. The structure of `dic_simulated_data` has been updated to hold a list of dictionaries, each containing simulation data the following keys:

- **`name`**: A unique identifier assigned to the simulation by the LLM.
- **`source`**: Indicates whether the model was uploaded by the user or loaded from the BioModels database.
- **`data`**: The simulation results associated with the model.
- **`tool_call_id`**: A unique identifier automatically assigned to the tool `simulate_tool` when the simulation request was made.

With this update, the LLM can leverage the state key `dic_simulated_data` to retrieve results from previous simulations. This enables answering user queries about specific simulations and generates custom plots.

The demo provided illustrates these updates in action.
 
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f65b0c853a66`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
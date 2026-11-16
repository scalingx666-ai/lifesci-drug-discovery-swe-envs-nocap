# Issue

**Title:** feat/textual enrichment

## Description

# For authors

## Description
I have developed a set of codes for performing textual enrichment for nodes/relations of knowledge graphs using LLMs provided by Ollama.

Following are several detailed key updates:

1. **Source Code**: Within the folder, `aiagents4pharma/talk2knowledgegraphs/utils/enrichments/` I included an abstract class `Enrichments`, followed by an implementation of `EnrichmentWithOllama` class for textual enrichment using a predefined LLM model.

2. **Pytest**: I included test cases of the above classes through `aiagents4pharma/talk2knowledgegraphs/tests/test_utils_enrichments_enrichments.py` and `aiagents4pharma/talk2knowledgegraphs/tests/test_utils_enrichments_ollama.py`.

3. **Tutorial Notebooks**: I added a basic interactive notebook for showcasing the use cases of the textual enrichment classes in `docs/notebooks/talk2knowledgegraphs/tutorial_starkqa_primekg_textual_enrichments.ipynb`. 

4. **Documentation**: I updated the related documentation using mkdocs, which is available in `docs/talk2knowledgegraphs/utils/enrichments/*`.

5. **Github Actions**: I modified Github Actions' workflow for pylint and pytest (with coverage) by taking into consideration cache files for both the Python virtual environment and Ollama models to save processing times (and costs). Note that, as of now, this cache-related workflow was only implemented for talk2knowledgegraph.

## Type of change
Please delete options that are not relevant.
- [x] New feature (non-breaking change which adds functionality)
- [x] This change requires a documentation update

## How Has This Been Tested?
Please describe the tests you conducted to verify your changes. These may involve creating new test scripts or updating existing ones.
- [x] Added new test(s) in the ```tests``` folder
- [x] Added new function(s) to an existing test(s) (i.e., `aiagents4pharma/talk2knowledgegraphs/tests/*`)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c6d95deeb9d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
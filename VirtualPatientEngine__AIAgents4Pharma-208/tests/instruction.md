# Issue

**Title:** feat: add-c2s-nb

## Description

# For authors

## Description

This PR introduces a new Jupyter notebook to the **T2C** agent, demonstrating an end-to-end single-cell analysis pipeline using publicly available data from a Crohn’s Disease (CD) patient.

The notebook covers the following key steps:

1. **Data Loading**  
   Loads single-cell RNA-seq data of a CD patient from an open-source repository.

2. **Preprocessing**  
   Applies standard preprocessing using `RAPIDS-singlecell` and `scanpy`.

3. **Enrichment Analysis**  
   Performs pathway enrichment using **Reactome** and **Gene Ontology (GO)**.

4. **C2SData Conversion**  
   Converts the processed `AnnData` object into the `C2SData` format.

5. **Model Inference**  
   Loads a pretrained **C2S model** for cell type prediction.

6. **Cell Type Annotation**  
   Annotates cells using the model's predictions.

7. **Export Results**  
   Saves enrichment results (Reactome, GO), DE genes, and predicted cell types to a single Excel workbook.

The generated Excel workbook is structured for direct use with **T2KG** and **T2AA4P**  
().

## Fixes # None

## Type of change
Please delete options that are not relevant.
- [ ] Bug fix (non-breaking change which fixes an issue)
- [X] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [X] This change requires a documentation update

## How Has This Been Tested?
Please describe the tests you conducted to verify your changes. These may involve creating new test scripts or updating existing ones.
- [ ] Added new test(s) in the ```tests``` folder
- [ ] Added new function(s) to an existing test(s) (e.g.: ```tests/testX.py```)
- [X] No new tests added (**Only notebook update**)

## Checklist
- [X] My code follows the style guidelines mentioned in the Code/DevOps guides
- [X] I have commented my code, particularly in hard-to-understand areas
- [X] I have made corresponding changes to the documentation (e.g. MkDocs)
- [X] My changes generate no new warnings
- [ ] I have added or updated tests (in the ```tests``` folder) that prove my fix is effective or that my feature works
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2ba91a4e77c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
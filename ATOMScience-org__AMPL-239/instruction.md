# Issue

**Title:** Prefeat smiles check

## Description

In this branch I did the following (sorry - I accidentally merged two branches before requesting pulls) 

4 commits in model_dataset.py from bug #237:
- create a check to see if all the smiles in a dataset are represented in the prefeaturized data
    - if not, raise assertion error
    - if so, allow
- raise the error up to get_featurized_data()

1 commit in diversity_plots.py: 
- I updated diversity_plots to allow a user-specified color palette and increase the resolution of the figure. No behavior will change unless you want to pass a color palette.

2 commits in featurization.py:
- reduce dataframe fragmentation by updating how the dataframe is constructed
- respect the original index of the file

1 commit in model_retrain.py:
- add a check so that if a model was originally trained and saved to the model tracker, it can be retrained and saved to the file system if the model tracker is unavailable (ie bringing a model tracker model outside LC)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72d1ff9a16a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
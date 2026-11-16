# Issue

**Title:** Add ensemble of GNINA models

## Description

## Description
This PR adds the `GNINAModelEnsemble` class, which allow to combine different pre-trained GNINA models into a single class. Related to #33 and #35.

This PR also adds functions to easily load an ensemble of pre-trained models using their names, and to perform inference from the CLI. For the time being, the CLI requires a list of protein-ligand pairs in a file, instead of the protein and ligand directly as in GNINA.

The class assumes that the models perform both pose prediction and binding affinity prediction (which is the case for the pre-trained GNINA models, hence the GNINA name). A less strict class to be used with custom models (pose prediction only, or pose and flexible residues) will follow.

The `dense` model is not yet available since it appears to be problematic and it is under investigation. This means that the GNINA `default` model is not yet available.

## PR Checklist
- [x] Tests
- [x] Documentation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90fa1a796b73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
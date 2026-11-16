# Issue

**Title:** Bug multiclass prediction

## Description

Fixes two bugs and creates 1 more test.

1. Class_number is saved in model_metadata.json so loading a model remembers how many classes there are.
2. Checks each subset to make sure every class is in every subset. This used to assume binary classification and throw a warning. Now it works with multiple classes and throws an exception since it causes metric calculation to crash.
3. Makes sure that class labels range from 0 to class_number. This is required by DeepChem and can cause crashes or bugs if not followed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bef979b08c57`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
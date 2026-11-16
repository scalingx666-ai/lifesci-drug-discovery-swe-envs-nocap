# Issue

**Title:** Add run columns name check and improve metadata validation errors

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**

Adds a validation check for the column names declared in `run_columns.csv`, and makes metadata validation failures report why they failed instead of always saying the field is empty. Also tightens slug validation and removes duplicated validation rules.

**Changes to be made**

- Add check_model_columns_name to the Model File Checks table
- Tighten slug validation (lowercase, hyphens, 1-4 words, max 60 chars)
- Delegate slug and title setters to BaseInformationValidator
- Report invalid values as InvalidEntry instead of EmptyField

**Status**

done


Related to #1899

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9fdbafb45725`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
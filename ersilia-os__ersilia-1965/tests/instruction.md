# Issue

**Title:** Add Apptainer image URL to model metadata

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**

Adds an `Apptainer` metadata field: the public URL of the model's Apptainer (Singularity) `.sif` image in the `models-sif` S3 bucket. It is filled in by the new `build-upload-sif.yml` workflow in ersilia-model-workflows, which installs ersilia from this branch to update Airtable and the model README.

**Changes to be made**

- `BaseInformation`: new `apptainer` property, validated as a URL to a `.sif` file (`ApptainerBaseInformationError` otherwise).
- `readme_formatter.py`: shows the Apptainer URL in the model README.
- `ersilia info`: shows the Apptainer URL in the Deployment section.

**Status**

Done. Merge together with the `apptainer-sif` PR in ersilia-model-workflows; the eos-template PR goes last.

**To do**

Nothing on this side.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88e3708e4cac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
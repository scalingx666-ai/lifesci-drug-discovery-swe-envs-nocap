# Issue

**Title:** Fix the GitHub Action tests.

## Description

Many trials and checks later, here is everything changed and discovered:

* Sequences canot be set as env variables
* Workflow-level env variables cannot be accessed outside of the `run` blocks
* Change directory in one step does not persist to other steps
* Artifacts operate like `scp target/* dest` rather than `scp target dest`
* Fixed a bug in the setup-cookiecutter so errors in Popen raise in the script
* Fixed templating confusion since top level GHA is not Cookiecutter->GHA
* Tested and built against all OS and relevant Python versions
* Sped up jobs by having cookiecutter run for all options inside single jobs
* Cannot use GHA env variables and bash variables in a single string, for reasons
* Conda-incubator cannot merge empty env files with single channel items in its Action
* Added channels to the test-env file
* Have GHA outside of Conda use the correct python versions

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18737c7cf50b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
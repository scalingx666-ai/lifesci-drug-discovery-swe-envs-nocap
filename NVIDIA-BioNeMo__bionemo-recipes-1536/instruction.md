# Issue

**Title:** Evo2 20b support and validation

## Description

### Description

* Adds in and verifies the evo2 20b checkpoint.
* Pulls in bugfix for CP from @moradza's #1524

#### Usage

See example notebooks. Output from the BRCA notebook with the 20b checkpoint:
<img width="783" height="499" alt="image" src="https://github.com/user-attachments/assets/2c9f3bc0-8b15-48be-8a99-e9184c43df5a" />


### Type of changes

<!-- Mark the relevant option with an [x] -->

- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Refactor
- [x] Documentation update
- [ ] Other (please describe):

### CI Pipeline Configuration

Configure CI behavior by applying the relevant labels. By default, only basic unit tests are run.

- [ciflow:skip](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:skip) - Skip all CI tests for this PR
- [ciflow:notebooks](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:notebooks) - Run Jupyter notebooks execution tests
- [ciflow:slow](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:slow) - Run slow single GPU integration tests marked as @pytest.mark.slow
- [ciflow:all](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:all) - Run all tests (unit tests, slow tests, and notebooks). This label can be used to enforce running all framework tests.
- [ciflow:all-recipes](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:all-recipes) - Run tests for all recipes (under bionemo-recipes). This label can be used to enforce running tests for all recipes.

Unit tests marked as `@pytest.mark.multi_gpu` or `@pytest.mark.distributed` are not run in the PR pipeline.

For more details, see [CONTRIBUTING](CONTRIBUTING.md)

> [!NOTE]
> By default, only basic unit tests are run. Add appropriate labels to enable an additional test coverage.

#### Authorizing CI Runs

We use [copy-pr-bot](https://docs.gha-runners.nvidia.com/apps/copy-pr-bot/#automation) to manage authorization of CI
runs on NVIDIA's compute resources.

- If a pull request is opened by a trusted user and contains only trusted changes, the pull request's code will
  automatically be copied to a pull-request/ prefixed branch in the source repository (e.g. pull-request/123)
- If a pull request is opened by an untrusted user or contains untrusted changes, an NVIDIA org member must leave an
  `/ok to test` comment on the pull request to trigger CI. This will need to be done for each new commit.

#### Triggering Code Rabbit AI Review

To trigger a code review from code rabbit, comment on a pull request with one of these commands:

- @coderabbitai review - Triggers a standard review
- @coderabbitai full review - Triggers a comprehensive review

See https://docs.coderabbit.ai/reference/review-commands for a full list of commands.

### Pre-submit Checklist

<!--- Ensure all items are completed before submitting -->

- [x] I have tested these changes locally
- [x] I have updated the documentation accordingly
- [ ] I have added/updated tests as needed
- [ ] All existing tests pass successfully

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `194255417a55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
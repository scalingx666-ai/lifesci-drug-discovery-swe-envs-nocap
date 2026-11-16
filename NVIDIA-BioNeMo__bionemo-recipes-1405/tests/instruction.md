# Issue

**Title:** Turns off FP8 for ESM2 heads

## Description

### Description

When using FP8 configs, disables it for the HEAD of the network. This includes the final dense layer and the decoder layer. This is because these layers have a ton of underflow occuring within them. See plot here: 
<img width="6494" height="4495" alt="beautiful_heatmap" src="https://github.com/user-attachments/assets/4b199608-77f7-4777-9e9d-a33aba042dbc" />

When we explicitly turn off FP8 and use BF16 for these layers we have converging loss curves see:
<img width="1887" height="1069" alt="Screenshot 2026-01-08 at 1 16 59 PM" src="https://github.com/user-attachments/assets/886e631d-e63b-42db-a6ef-d3d50775f5df" />


#### Usage

The user doesn't have to do anything

```python
TODO: Add code snippet
```

### Type of changes

<!-- Mark the relevant option with an [x] -->

- [X] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Refactor
- [ ] Documentation update
- [ ] Other (please describe):

### CI Pipeline Configuration

Configure CI behavior by applying the relevant labels. By default, only basic unit tests are run.

- [ciflow:skip](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:skip) - Skip all CI tests for this PR
- [ciflow:notebooks](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:notebooks) - Run Jupyter notebooks execution tests for bionemo2
- [ciflow:slow](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:slow) - Run slow single GPU integration tests marked as @pytest.mark.slow for bionemo2
- [ciflow:all](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:all) - Run all tests (unit tests, slow tests, and notebooks) for bionemo2. This label can be used to enforce running tests for all bionemo2.
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

### Pre-submit Checklist

<!--- Ensure all items are completed before submitting -->

- [ ] I have tested these changes locally
- [ ] I have updated the documentation accordingly
- [ ] I have added/updated tests as needed
- [ ] All existing tests pass successfully

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aeed0ded628c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
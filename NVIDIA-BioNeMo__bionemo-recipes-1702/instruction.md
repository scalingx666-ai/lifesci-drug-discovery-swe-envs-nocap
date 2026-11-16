# Issue

**Title:** feat(evo2): add Vortex to MBridge checkpoint tools

## Description

### Description

Tools to back-convert Vortex to Mbridge. We had not done this before because you can't know the exact weights of the full mbridge model that would lead to a vortex model. This adds in a version that will make a guess at "reasonable" weights that could have lead to vortex. The forward pass results will be identical, but ability to fine-tune may be either better or worse than the original pre-vortex checkpoint. Splits these features out of 

#### Usage

Tool to get a sense for what a reasonable inverse prior would be when doing the back-conversion. This should help get you a reasonably well behaved checkpoint that is about as fine-tunable as the original.
```python
evo2_analyze_inverse_prior --help 
```

To actually run the back conversion, do the following. This script has hard-coded defaults learned from running `evo2_analyze_inverse_prior` on several evo2 checkpoints.

```
evo2_convert_vortex_to_mbridge --help
```

### Type of changes

<!-- Mark the relevant option with an [x] -->

- [ ] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [ ] Refactor
- [ ] Documentation update
- [ ] Other (please describe):

### CI Pipeline Configuration

Configure CI behavior by applying the relevant labels. By default, only basic unit tests are run.

- [ciflow:skip](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:skip) - Skip all CI tests for this PR
- [ciflow:notebooks](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:notebooks) - Run Jupyter notebooks execution tests
- [ciflow:slow](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:slow) - Run slow single GPU integration tests marked as @pytest.mark.slow
- [ciflow:all](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:all) - Run all tests, including unit tests, slow tests, notebooks, and every recipe/model directory.

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
- [x] I have added/updated tests as needed
- [ ] All existing tests pass successfully

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **New Features**
  * Added tools to convert Vortex checkpoints to MBridge format and analyze checkpoint filter priors.
  * Added support for local checkpoints or downloads, model configuration options, and optional Transformer Engine compatibility.
  * Improved checkpoint conversion to preserve rotary embedding settings when available.
* **Documentation**
  * Expanded checkpoint conversion guidance, supported workflows, validation details, and prior-analysis examples.
* **Bug Fixes**
  * Improved checkpoint packaging compatibility and handling of runtime state.
* **Tests**
  * Added coverage for conversion, round-trip accuracy, packaging, validation, and prior analysis.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34cb4966597f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
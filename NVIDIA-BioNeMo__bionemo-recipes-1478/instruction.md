# Issue

**Title:** Enable pipeline model parallelism for Evo2 inference

## Description

Remove the PP > 1 guard, argparse choices=[1] restriction, and hardcoded pre_process/post_process=True so the model provider auto-detects pipeline stage. Tested with PP=1, PP=2, and PP=5.

### Description

For the most part I just removed the guarding that forces PP=1.  There's only one functional line change.

  1. Line 257 — Removed the if pipeline_model_parallel_size != 1: raise ValueError(...) guard (3 lines deleted)
  2. Line 334 — Changed model_provider.provide(pre_process=True, post_process=True) to model_provider.provide() so each pipeline stage auto-detects whether it needs embedding/output layers
  3. Line 508 — Removed choices=[1] from the --pipeline-model-parallel-size argparse argument
  4. Lines 245, 553 — Updated docstrings removing "(must be 1)"

#### Usage

torchrun --nproc-per-node 2 /workspace/bionemo/src/bionemo/evo2/run/infer.py \
          --ckpt-dir /workspace/bionemo/evo2_1b_8k_bf16_mbridge \
          --prompt "ATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCG" \
          --max-new-tokens 10 \
          --top-k 1 \
          --temperature 1.0 \
          --pipeline-model-parallel-size 2

torchrun --nproc-per-node 5 /workspace/bionemo/src/bionemo/evo2/run/infer.py \
          --ckpt-dir /workspace/bionemo/evo2_1b_8k_bf16_mbridge \
          --prompt "ATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCG" \
          --max-new-tokens 10 \
          --top-k 1 \
          --temperature 1.0 \
          --pipeline-model-parallel-size 5

  │ PP=1 inference (1 GPU)                PASS   ATCGATCGAT   │
  │ PP=2 inference (2 GPUs)             PASS   ATCGATCGAT   │
  │ PP=5 inference (5 GPUs)             PASS   ATCGATCGAT   │

### Type of changes

<!-- Mark the relevant option with an [x] -->

- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Refactor
- [ ] Documentation update
- [ ] Other (please describe):

### CI Pipeline Configuration

Configure CI behavior by applying the relevant labels. By default, only basic unit tests are run.

- [ciflow:skip](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:skip) - Skip all CI tests for this PR

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
- [x] All existing tests pass successfully

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5a98d2ea33e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
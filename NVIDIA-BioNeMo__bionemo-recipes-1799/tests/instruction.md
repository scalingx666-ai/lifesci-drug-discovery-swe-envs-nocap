# Issue

**Title:** fix(esm2_peft_te): use spawn for DataLoader workers

## Description

### Description

Fixes the flaky `recipes/esm2_peft_te` `test_sanity_ddp_thd` failure in the [2026-11-12 nightly](https://github.com/NVIDIA-BioNeMo/bionemo-recipes/actions/runs/43189011080/job/131084313781). The same commit passed the night before, and the same tree failed once in #1798's PR CI before passing on rerun.

Failure from the log:
```
terminate called after throwing an instance of 'c10::AcceleratorError'
  what():  CUDA error: initialization error
frame #2: c10::cuda::ExchangeDevice(signed char)
frame #5: c10d::Reducer::~Reducer()
RuntimeError: DataLoader worker (pid(s) 1514) exited unexpectedly
```

The DataLoader workers are forked. A forked worker inherits whatever is still alive in the parent process, including a DDP model left over from an earlier test that hasn't been garbage-collected yet. When the worker's GC destroys it, `~Reducer` makes a CUDA call. CUDA can't be used in a forked child, so the worker aborts. Whether this happens depends on GC timing, which is why the failure is intermittent.

The fix follows `recipes/esm2_native_te/dataset.py`, which already does this (added in #1714):
- Both DataLoaders now pass `multiprocessing_context="spawn" if num_workers > 0 else None`.
- The nested `tokenize` closure is now a module-level `tokenize_function` bound with `functools.partial`, so the streaming `IterableDataset` can be pickled for spawned workers. Its logic is unchanged.

Adds `tests/test_dataset.py`. It checks that the train DataLoader uses `spawn`, and that a streaming dataset (both BSHD and THD) can be pickled and yields a batch from a spawned worker.

#### Usage

No API change. `create_dataloader(...)` returns DataLoaders whose workers are spawned instead of forked.

### Type of changes

- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
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

- [x] I have tested these changes locally: `tests/test_dataset.py` passed on CPU, with Transformer Engine stubbed out because this VM has no GPU. The GPU training tests weren't run locally; this PR's CI covers them.
- [ ] I have updated the documentation accordingly
- [x] I have added/updated tests as needed
- [ ] All existing tests pass successfully

Link to Devin session: https://nvidia-cloud.devinenterprise.com/sessions/581cb7b986394011bd77f4fd953906db
Open in Devin Desktop: https://nvidia-cloud.devinenterprise.com/desktop/session/581cb7b986394011bd77f4fd953906db?variant=devin

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4db3b55ce966`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
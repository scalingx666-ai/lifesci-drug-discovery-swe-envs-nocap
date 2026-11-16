# Issue

**Title:** Support subquadratic-ops kernels in evo2 autoregressive inference

## Description

### Description

Closes the gap noted in `hyena_mixer.py` (`# todo: support inference_context for b2b_kernel`) and the README caveat that `--use-subquadratic-ops` "does not apply to autoregressive inference (`infer_evo2`)". After this PR, the same fused kernels that accelerate training and batch prediction also accelerate the prefill phase of autoregressive inference. 

Summary of change:

1. **`engine.parallel_fir`** now accepts `use_subquadratic_ops` and routes to `fft_causal_conv1d` (filters ≥ 128) or `causal_conv1d` (short filters), wired through both call sites in `hyena_utils.py`.
2. **`HyenaMixer.forward`** detects prefill (no FIR cache yet) and runs `b2b_causal_conv1d` for the fused proj+mixer convolution. The kernel doesn't expose its intermediate, so we run a tiny windowed proj-conv on the last `K_proj + K_mixer − 2` input positions to materialize the `(x2*v)` tail and seed the mixer's FIR cache. Works for both `hyena_short_conv` and `hyena_medium_conv`.
3. Removed the `del self._parameters["short_conv_weight"]` micro-optimization in `ParallelCausalDepthwiseConv1dWithState._get_weight()` — `B2BCausalConv1dModule` reads that raw param on every prefill, so deleting it after first decode broke multi-prompt inference. Memory cost is ~4 MB for a 1B model.

`infer_evo2` gets a `--use-subquadratic-ops` flag.

## Testing

- New parametrization `test_forward_manual[1b-8k-bf16-subquadratic-ops-flash]` covers the `(flash_decode=True, subquadratic_ops=True)` combination that was previously skipped.
- New `test_subquadratic_ops_matches_baseline` runs greedy autoregressive generation with and without `--use-subquadratic-ops` and asserts identical output — this is the strict check that Phase 2 state population is correct (a wrong cache would diverge during decode).
- Existing kernel comparison tests (`test_hyena_mixer_kernel.py`) and inference-context unit tests pass unchanged.


## Performance

`infer_evo2`, evo2/1b-8k-bf16, single A6000, multiple identical prompts in one process to amortize the one-time JIT compile cost (~15 s the first time each subq-ops kernel sees a new shape). Steady-state numbers from batches 3+:

| Prompt | Generation | Baseline | Subq-ops | Speedup |
|---|---|---|---|---|
| 4 096 tokens | 5 tokens | 0.57 s | 0.51 s | ~10% |
| 8 000 tokens | 1 token | 1.02 s | 0.87 s | ~15% |

The speedup is concentrated in prefill. The relative improvement grows with prompt length and shrinks as more decode tokens are amortized in.


### Type of changes

<!-- Mark the relevant option with an [x] -->

- [ ] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
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

- [x] I have tested these changes locally
- [x] I have updated the documentation accordingly
- [x] I have added/updated tests as needed
- [x] All existing tests pass successfully

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **New Features**
  * Added `--use-subquadratic-ops` CLI option to optimize prompt/prefill processing during inference while leaving per-token decode unchanged.

* **Documentation**
  * Clarified subquadratic-ops kernel behavior and performance impact on prefill throughput.

* **Tests**
  * Added end-to-end test confirming subquadratic-ops generates identical inference results as baseline.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `85d0c16d2c06`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
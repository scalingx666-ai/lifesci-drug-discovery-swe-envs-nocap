# Issue

**Title:** Bug fixes for evo2 inference.  CP at least doesn't error.  TP working…

## Description

… on 1 node.

### Description

**EVO2 Dockerfile Change** - Added ENVs to force casual_conv1d to be built

**CP Partial Fixes**
Running Evo2 Megatron inference with --context-parallel-size 2 caused tensor shape mismatches because the inference path doesn't split sequences across CP ranks (each rank gets the full sequence), but the code was still applying CP-related AllToAll operations and CP-sharded parameter slicing.

Tested that it no longer errors and returns the generation, but enabling full useful CP is a much heavier lift.

**TP FIxes**
With TP > 1, sequence_parallel was automatically set to True. Megatron's inference engine doesn't support sequence parallelism for non-MoE models, raising NotImplementedError. Sequence parallelism is a training-only activation memory optimization and isn't needed for inference.

In ParallelHyenaOperator.forward_long(), the call to engine.parallel_iir() passed self.hidden_size (the full model hidden size, e.g., 4096). With TP=8, each rank only has width_per_tp_group = 4096 / 8 = 512 channels, so the concatenated tensor u has 3 * 512 = 1536 channels. The parallel_iir function tried to split it into three chunks of 4096, causing a RuntimeError.

**Infer.py Test Enabling**
I didn't know this, but apparently unix command lines have a character limit.  Even though I was generating the prompt it evaluated to something longer than 128K characters.  Added a --prompt-file switch that reads the prompt... from a file.

#### Usage

Tested TP=8 on one node.
16K prompt fits on one GPU. 32K OOMs

Confirmed that 128K prompt fits on 8 GPUs and 256K prompt OOMs.

Generate the prompt:
python3 -c "
import random
random.seed(42)
seq = ''.join(random.choices('ACGT', k=131072))
prompt = '|d_Bacteria;p_Pseudomonadota;c_Gammaproteobacteria;o_Enterobacterales|' + seq
with open('/tmp/prompt128k.txt', 'w') as f:
   f.write(prompt)
print(f'Wrote prompt of length {len(prompt)}')
"

Execute:
torchrun --nproc-per-node 8 ./src/bionemo/evo2/run/infer.py \
 --tensor-parallel-size 8 \
 --ckpt-dir $CKPT_OUT_DIR \
 --max-new-tokens 100 \
 --max-seq-length 131300 \
 --prompt-file /tmp/prompt128k.txt

### Type of changes

<!-- Mark the relevant option with an [x] -->

- [ x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Refactor
- [ ] Documentation update
- [ ] Other (please describe):

### CI Pipeline Configuration

Configure CI behavior by applying the relevant labels. By default, only basic unit tests are run.

It's my first real change.  Run everything?

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19fedc572d8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
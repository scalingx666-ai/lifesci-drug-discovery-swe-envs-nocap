# Issue

**Title:** Drop nv-grouped-gemm from Evo2/Eden recipes; bump eden_megatron to Megatron-Bridge v0.5.0

## Description

### Description

 (PyTorch 26.09 bump). This PR removes the `nv-grouped-gemm` dependency (fanshiqing/grouped_gemm `v1.1.4.post6`). It's one of the packages that hardcode `-std=c++17`, which the PyTorch 26.09 headers reject.

**Evo2 recipes (`evo2_megatron`, `evo2_phage_gen`)**
- Removes `nv-grouped-gemm` from three places in `pyproject.toml`:
  - the `dependencies` list
  - `[tool.uv.sources]`
  - `[tool.uv] no-build-isolation-package`
- Removes the package's name from the `cxx20_build_env.sh` comments.
- No uv.lock or constraints files referenced it.
- Why it's safe to remove:
  - No recipe code imports `grouped_gemm`. Evo2 is Hyena, not MoE.
  - These recipes pin Megatron-Bridge `v0.5.0`, which uses Megatron-LM `d0b3b77`. At that commit, `moe/grouped_gemm_util.py` is gone and nothing imports `grouped_gemm`. MoE grouped GEMM goes through TE `GroupedLinear`.
  - No dependency pulls it back in transitively. NeMo-RL lists it only in its unused `automodel` extra.

**eden_megatron: bump to Megatron-Bridge/mcore `v0.5.0`, matching Evo2** (requested in review)
- Why eden had it: the old pin was MB `549e3cb`, which depends on `megatron-core[dev]` at Megatron-LM `bbbedbb`. That extra pulled `nv-grouped-gemm~=1.1` from PyPI as a source build. At `v0.5.0` it no longer does.
- Dependency changes:
  - The pin now matches Evo2.
  - Drops the direct `nvidia-resiliency-ext` pin. It now comes in through Megatron-Bridge.
  - Adds `pydantic`/`logsage`/`drain3` overrides.
  - Adds the build requirements that `nvidia-resiliency-ext` needs under `--no-build-isolation`.
- API ports for v0.5.0, mostly mirroring what `evo2_megatron` already does:
  - `EdenModelProvider` subclasses `GPTModelProvider` with the Llama 3.1 defaults inlined, because `Llama31ModelProvider` was removed.
  - `InferenceWrapperConfig` is gone, and `AbstractModelInferenceWrapper` now takes `(model, inference_context)`.
  - The HF tokenizer falls back to mcore's `HuggingFaceTokenizer`. A `_adapt_tokenizer_for_generation` adapter aliases `tokenize`/`detokenize` for the static engine.
  - Registers the `bionemo.eden.` prefix with `register_allowed_target_prefix`. Without it, infer/predict can't `instantiate()` the provider from `run_config.yaml`.
  - Guards `compile_helpers()`, because the mcore wheel ships a prebuilt `helpers_cpp` and no Makefile.
- CI: `.ci_build.sh` now installs `.[test]`, and `pytest-timeout` is added to the test extra. Before this, the job had no pytest installed.
- Eden still uses `cxx20_build_env.sh` for the other extensions (e.g. causal-conv1d, mamba-ssm).

**Would a newer Megatron-Bridge change anything?** No. `v0.6.2` (latest) and `26.09-beta.rc1` also have no grouped-gemm dependency. Megatron-Bridge still lists `nv-grouped-gemm` in its own uv `no-build-isolation-package`, but that list only affects how a package is built if something installs it. It doesn't add a dependency.

#### Usage

No user-facing change. The containers no longer build `grouped_gemm`, and the eden train/infer/predict CLIs work as before.

### Type of changes

- [ ] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [x] Refactor
- [ ] Documentation update
- [x] Other (please describe): dependency cleanup / Megatron-Bridge bump for eden_megatron

### Pre-submit Checklist

- [ ] I have tested these changes locally (the dev VM has no GPU and no PyPI access. `python ci/scripts/check_copied_files.py` passes. GPU CI is the real test.)
- [ ] I have updated the documentation accordingly
- [ ] I have added/updated tests as needed
- [x] All existing tests pass successfully

Link to Devin session: https://nvidia-cloud.devinenterprise.com/sessions/8069a04ae96e4c5eaee3ce9b7493283a
Open in Devin Desktop: https://nvidia-cloud.devinenterprise.com/desktop/session/8069a04ae96e4c5eaee3ce9b7493283a?variant=devin
Requested by: @pstjohn

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fbae1941d8cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
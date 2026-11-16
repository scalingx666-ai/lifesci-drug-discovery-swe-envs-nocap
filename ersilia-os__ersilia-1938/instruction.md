# Issue

**Title:** Slim the pip model Dockerfile: no duplicate model layer, one apt laye…

## Description

**Description**

Model images built with `dockerfiles/dockerize-ersiliapack/model/Dockerfile.pip` ship data they
never use. A scan of 55 recent models found 9.9 GB (amd64) in duplicate model layers alone,
and 100–300 MB of test suites per image. This PR slims the template without changing how
models are packed or served: images get **8–27 % smaller** to download, with identical outputs.

**Changes to be made**

Only `dockerfiles/dockerize-ersiliapack/model/Dockerfile.pip` changes:

1. **No duplicate model layer.** `COPY ./$MODEL` is replaced by a BuildKit bind mount
   (`RUN --mount=type=bind,source=./$MODEL,...`). The old `rm -rf /root/$MODEL` only hid the
   copied folder; its bytes (checkpoints included) were still shipped in their own layer.
2. **One apt layer instead of six**, with the package lists deleted in the same step.
3. **Prune site-packages** in the install step: `tests/` folders, `include/` (C headers) and
   `*.a` static libraries. Models don't use these at runtime (the compiler is already removed
   in the same step). `numpy/_core/tests` is kept: in numpy 2.x, `numpy.testing` imports
   `numpy._core.tests._natype`, and scipy loads `numpy.testing`.

The CI build (`upload-ersilia-pack.yml`) already uses BuildKit (`setup-buildx-action`) and
`context: ../`, which is what the bind mount needs. No workflow change is required.

**Status**

Done and tested locally on linux/amd64 with 6 models: one per task type, two rounds, with
different stacks (plain rdkit, torch, lazyqsar, numpy 1 and 2, large checkpoints).

Sizes (compressed = download size), against the **current** Dockerfile built the same day, so
both images have exactly the same packages (`pip freeze` identical):

| Model   | Task type      | Stack                                     | Current | This PR | Saved  |
|---------|----------------|-------------------------------------------|--------:|--------:|-------:|
| eos4k4f | Representation | rdkit, datamol                            | 265 MiB | 234 MiB | −12 %  |
| eos5jv3 | Annotation     | torch CPU, torch-geometric, sklearn       | 512 MiB | 457 MiB | −11 %  |
| eos9p57 | Sampling       | rdkit, sklearn, crem + 688 MB checkpoint  | 391 MiB | 285 MiB | −27 %  |
| eos4r1g | Annotation     | lazyqsar, numpy 2 + scipy                 | 697 MiB | 643 MiB | −8 %   |
| eos5g6m | Representation | torch, chemprop, transformers, lightning  | 612 MiB | 535 MiB | −13 %  |
| eos92m1 | Sampling       | torch 1.13 CPU (generator)                | 424 MiB | 381 MiB | −10 %  |

Tests run, and why. Each published image (`ersiliaos/<model>:latest`) was run side by side with
the image built from this Dockerfile:

| Test | Why | Result |
|------|-----|--------|
| `run.sh` on the model's example input; outputs compared byte by byte | The prediction itself must not change | Identical for all deterministic models |
| Same input through the server (`POST /run`), plus `/healthz` and `/card` | This is how ersilia calls the model; checks that the server starts and answers | Identical outputs; 200 on all endpoints |
| Random models (eos9p57, eos92m1) re-run with all random generators seeded, 2× per image | Their outputs differ on every run by design, even in the published image; seeding makes an exact comparison possible | Byte-identical (4 of 4 runs per model) |
| Import every submodule of every installed package; compare failures with the current Dockerfile built the same day | Pruning must not delete a file some code needs. `import X` alone is not enough: that is how the numpy case was first missed | Same failure list in both (all pre-existing optional deps): nothing new broken |
| Compare `pip freeze` and bundle file checksums | Confirms the only difference is the removed files | Identical (except `information.json`, generated at build time) |
| Scan site-packages for normal code importing from a `tests/` folder | Find other packages that behave like numpy | Only numpy does so at import time; others only inside test-runner functions |

Small differences from the stored `run_output.csv` (≤ 8e-7 for eos5jv3, eos4r1g, eos5g6m) are
the same in the published images, so they existed before this change.

Side finding (unrelated to this PR): eos4r1g rebuilt today cannot import `chemprop`, with
either Dockerfile. lazyqsar doesn't pin chemprop's version, and chemprop 2.3.1 pulls
`cuik_molmaker`, built against another rdkit. The model still runs because it doesn't use
chemprop.

**To do**

- **arm64:** not tested. The change is not architecture specific, but it has only been run on amd64.


Related to #1917

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d3b9ab7d759`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
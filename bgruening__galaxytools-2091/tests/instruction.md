# Issue

**Title:** FLUX: FLUX.2 [klein] 4B and FLUX 3 Image Klein, editing and inpainting

## Description

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [ ] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

The wrapper and diffusers allow unrestricted use, and so does FLUX.2 [klein] 4B (Apache 2.0). FLUX 3 Image Klein's weights are non-commercial, as FLUX.1 [dev]'s were; the help says so.

Updates FLUX to the current Black Forest Labs models and loads them from the shared `huggingface` data table, the same way as WhisperX in #1792.

**Models and tasks**

| Task | FLUX.2 [klein] 4B (Apache 2.0) | FLUX 3 Image Klein (non-commercial) |
| --- | --- | --- |
| Generate an image from the prompt | yes | yes |
| Edit or combine up to 10 reference images | yes | yes |
| Inpainting (image and mask) | yes | |

FLUX.1 [dev] and [schnell] are replaced: FLUX.2 [klein] 4B is faster and smaller than [schnell] under the same license, and both new models also edit. Older FLUX.1 variants (Krea, Kontext, Fill, Canny, Depth, Redux) and the FLUX.2 9B and base models are left out, because these two models cover what they do. In a comparison, editing kept the structure of an image better than Canny and Depth, and FLUX.2 [klein] inpainted as well as FLUX.1 Fill. FLUX.2 [dev] does not fit on the GPUs of usegalaxy.eu.

The form, with the edit task and the model select open:

![FLUX form](https://github.com/user-attachments/assets/c30c1a8a-e37b-44be-964b-c4606b08aa77)

Outputs at 1024x1024 with the published container and no network for the jobs. The edit and inpainting change the image generated in the first column:

![FLUX examples](https://github.com/user-attachments/assets/8d2fdfa5-bfc9-4fda-b388-6cb1188da217)

**Data table**
- `value` is the Hugging Face model ID, `free_tag` is `flux` and `path` is the model root (the directory that contains `hub/`). `flux.py` loads the model by its ID with `HF_HUB_OFFLINE=1`. This replaces picking the model by "dev" or "schnell" in the path and the newest snapshot by modification time.
- `version` is the FLUX generation of the model: 2 for FLUX.2 [klein] 4B, 3 for FLUX 3 Image Klein. 2024+galaxy4 reads only version 1, its FLUX.1 rows, so it keeps working: tested with a table that has both, it still offers its own rows and rejects the new ones. The new version only offers the IDs it supports, so it never shows the FLUX.1 rows.
- The rows in `tool-data/huggingface.loc.sample` are commented out, so a Tool Shed install doesn't add rows with the placeholder path.

**Container.** `quay.io/galaxy/black_forest_labs_flux:2026-0`, built by the new [usegalaxy-eu/docker-flux](https://github.com/usegalaxy-eu/docker-flux) with pinned torch and diffusers versions. Its `2026-0` release builds the image; this PR's CI needs it on quay.io.

**Downloader.** `download_models.py` runs inside the tool's container and downloads only the diffusers files: about 16 GB for FLUX.2 [klein] 4B and 37 GB for FLUX 3 Image Klein with its prompt upsampler. FLUX 3 Image Klein is gated, so the token needs its license accepted.

**Tests.** CI has no models or GPU, so the tests (`ci_tests` in `macros_for_testing.xml`) check the command line built from the data table, and every job stops at the GPU check. A decoy test checks that the model select never offers the FLUX.1 rows of the older versions; it fails if a job is built. The real tests (`real_tests`) check the image size for each model and task. They passed on a machine with an L40S, with the network turned off for the jobs.

**Breaking:** the form now starts with a task, and the model values changed, so saved workflows need the model picked again.

**Follow-up (not in this PR):** usegalaxy.eu needs the models downloaded, the version 2 rows, and `mem` and GPU settings for the flux rule (usegalaxy-eu/infrastructure-playbook#2492).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `074136fa753e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
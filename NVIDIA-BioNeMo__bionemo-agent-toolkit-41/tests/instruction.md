# Issue

**Title:** Improve Evo2 generation execution and result validation

## Description

The Evo2 generation example required agents to reconstruct an API client, leaving request execution, validation, and saved outputs inconsistent. This adds a reusable client for hosted and local generation that validates returned DNA, probabilities, and timing; saves request/response JSON, the raw response body, FASTA, and metrics; and reports values from the actual response. The skill instructions now direct agents to execute the client when generation is requested.

The evaluation dataset matches the September 29 neutral run, including the hosted task and assertions. The model configuration and grading thresholds are unchanged. Source and distributed skill copies are synchronized.

## Client reliability

- Reserve a new output directory atomically before submitting a request. Existing directories, including empty ones, are rejected so concurrent runs cannot overwrite or mix artifacts.
- Save the exact response body as `response.raw` before checking HTTP status, parsing JSON, or serializing it. Malformed JSON and non-finite values retain diagnostics without producing success artifacts.
- Declare `requests>=2.28` directly in `pyproject.toml` and regenerate `uv.lock`; resolved package versions remain unchanged.

## Validation

- 16 local repository tests pass, including nine client tests covering concurrent output reservation, existing directories, malformed/non-finite responses, and an executed request through a loopback HTTP server. Responses in these local tests are synthetic.
- Plugin-sync passes for all 31 aggregate skills; `uv tree --no-dedupe --frozen` passes with `requests` declared as a direct dependency.
- GitHub SkillSpector passes at 37/100. Documented file-scoped suppressions cover the client's environment-URL and permission-mapping findings, plus the dotenv filename in deferred evaluation data. Ten active medium findings remain; the scanner score reflects these suppressions.
- **Completed NV-CARPS evaluation for `ef0e5bb`:** Tier 1 and Tier 2 passed with observations; **Tier 3 passed** with Claude Code and Codex on the hosted generation task. The signing service attached the benchmark, skill card, and signature in `b589a53`. The subsequent client reliability fixes in `93d4978` pass local checks and require a fresh NV-CARPS evaluation and signature.

## Last completed Tier 3 results (`ef0e5bb`)

The [Tier 3 job](https://gitlab-master.nvidia.com/nvcarps/ci-group/nvcarps-ci/-/jobs/461015779) reports **PASS, skill lift +0.24**, for source commit `ef0e5bb`.

The benchmark reports the following effectiveness scores (50% goal accuracy + 50% behavior check):

| Agent | Without skill | With skill | Effectiveness uplift |
|---|---:|---:|---:|
| Claude Code | 52.9% | 100.0% | +47.1 percentage points |
| Codex | 50.7% | 100.0% | +49.3 percentage points |

Both conditions retain 100% security and correctness scores. This run covers one hosted-generation task, with one executed attempt per agent and condition; it does not establish coverage of the deferred local-Docker and forward-pass cases.

Evidence: [completed evaluation for ef0e5bb](https://github.com/NVIDIA/nvskills-ci/actions/runs/36619286829), [validation of the signed evaluation commit](https://github.com/NVIDIA/nvskills-ci/actions/runs/36621200461), and [generated benchmark](https://github.com/NVIDIA-BioNeMo/bionemo-agent-toolkit/blob/b589a53acbf955728d9926537dc42cb5e39762c8/skills/bionemo-agent-toolkit/skills/evo2-nim/BENCHMARK.md).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf414dec16c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Use streaming and handle reasoning models in LLM Hub tool

## Description

## What & why

Long-running LLM Hub jobs (e.g. full-document translations) failed with `APITimeoutError: Request timed out` after 3 retries. Two compounding causes:

1. **Non-streaming request**: `client.chat.completions.create(...)` blocked until the *entire* completion was ready, so any generation longer than `LITELLM_REQUEST_TIMEOUT` (default 600s) timed out — and the retry loop then re-sent the whole large request from scratch, reproducing the same timeout.
2. **Reasoning models**: models that expose a `reasoning_content` field (OpenAI o-series, DeepSeek-R1, GLM thinking models, etc.) spend a large, unpredictable token budget on chain-of-thought *before* emitting any answer, making the wait even longer. The original code read only `message.content`, which stays empty during that phase.

## Changes

- **Streaming** (`stream=True`): token deltas keep the connection alive token-by-token, so `LITELLM_REQUEST_TIMEOUT` bounds *inter-chunk idle* rather than total generation walltime. Reasoning models stream their chain-of-thought continuously, so the connection never goes idle during the thinking phase.
- **Reasoning-model support**: accumulate only the answer (`content`) from the streaming delta; the non-standard `reasoning_content` (chain-of-thought) is accessed via `getattr` and discarded. Non-reasoning models that lack the field are unaffected (every access is guarded).
- **Explicit outcome handling** instead of silently producing a blank or truncated dataset:
  - An empty answer fails the job with an actionable message *before* writing `output.md` (no silent blank dataset).
  - `finish_reason` of `length`, `content_filter`, or `None` logs a warning when the written result may be partial.
- **No default `max_tokens`**: a fixed cap truncates reasoning models to empty `content` with `finish_reason='length'`. Rely on the model/proxy default.
- **Capped timeout retries**: new optional `MAX_TIMEOUT_RETRIES` config key (default 1), since re-sending a large request after a timeout reproduces the same timeout. Other transient errors keep the full `MAX_RETRIES` budget.
- Bump wrapper version to `2.41.1+galaxy2`.

## Testing

Verified end-to-end against **all 34 text/multimodal models** in the `genai_models.loc` of a live two-provider deployment (uni-freiburg + e-infra.cz), using a real subtitle-translation task — all return exit 0 with correct output, including slow reasoning models (e.g. `deepseek-v4-pro-thinking` ~108s, `deepseek-thinking` ~103s). Streaming kept the connection alive throughout; no `APITimeoutError`.

Failure paths also exercised:
- Empty answer on `finish_reason='length'` → exit 1, actionable message, no blank file written.
- Partial content + `length` → exit 0, partial file + stderr warning.
- Non-numeric `MAX_TIMEOUT_RETRIES` env → handled cleanly (no traceback).

## Notes

- This is a **behavior change**: an empty LLM response now fails the job (exit non-zero) instead of silently writing a blank dataset. An empty output is not usable by downstream tools, so failing loudly is the intended improvement. With `detect_errors='exit_code'` this surfaces clearly in Galaxy.
- Streaming cannot solve Galaxy's outer job walltime — a pathologically huge input can still exceed it. The truncation/empty messages now point users at splitting large inputs into chunks.
- No new dependencies; `openai` and `pyyaml` already required.

## Contributor checklist

* [x] I have read the CONTRIBUTING.md document and this tool is appropriate for the repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c850f5ed14b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
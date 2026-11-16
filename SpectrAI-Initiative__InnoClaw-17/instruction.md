# Issue

**Title:** Remove LLM_MODEL from .env.example; add vendor-level base URL fallback for per-model-URL providers

## Description

`LLM_MODEL` in `.env.example` is redundant (default is in code, overridable via Settings UI). Per-model-URL providers (Qwen, Moonshot, DeepSeek, etc.) only support per-model env vars like `MOONSHOT_KIMI_K2_5_BASE_URL` with no vendor-level fallback, which doesn't match common practice.

### Changes

- **`.env.example`**: Remove `LLM_MODEL` line. Add vendor-level base URL examples (`QWEN_BASE_URL`, `MOONSHOT_BASE_URL`, etc.) with per-model URLs documented as optional overrides.

- **`src/lib/ai/provider.ts`**: `getPerModelProvider()` now resolves base URL with fallback:
  1. Per-model env var (`MOONSHOT_KIMI_K2_5_BASE_URL`)
  2. Vendor-level env var (`MOONSHOT_BASE_URL`)
  3. Error naming both options

- **`docs/getting-started/environment-variables.md`**: Add missing provider API keys and vendor-level base URL variables to the reference table.

- **`src/lib/ai/provider.test.ts`**: 5 unit tests covering priority, fallback, error messages, and all 6 providers.

### Resolution logic

```typescript
const perModelEnvVar = prefix + "_" + modelId.toUpperCase().replace(/[^A-Z0-9]/g, "_") + "_BASE_URL";
const vendorEnvVar = prefix + "_BASE_URL";
const baseURL = process.env[perModelEnvVar] || process.env[vendorEnvVar];
```

Setting `MOONSHOT_BASE_URL` once now works for all Moonshot models. Per-model URLs still take priority for advanced routing.

<!-- START COPILOT ORIGINAL PROMPT -->

<details>

<summary>Original prompt</summary>

>
> ----
>
> *This section details on the original issue you should resolve*
>
> <issue_title>Environment variables: Remove useless LLM_MODEL from .env.example; add vendor-level base URL fallback for Qwen/Moonshot/etc.</issue_title>
> <issue_description>### Problem Statement
>
>
> ## 1. Remove `LLM_MODEL` from `.env.example`
>
> **Current state:** `.env.example` contains a commented line:
>
> ```env
> # LLM_MODEL=gpt-4o-mini
> ```
>
> **Problem:** This is redundant. The default model is already defined in code (`src/lib/ai/models.ts`: `DEFAULT_MODEL = process.env.LLM_MODEL || "gpt-4o-mini"`), and users can override the default in the Settings UI. Listing `LLM_MODEL` in the example file suggests it is a required or recommended example variable, but it is not needed for a minimal setup.
>
> **Proposal:** Remove the `LLM_MODEL` line from `.env.example`. Optionally keep it only in documentation (e.g. environment-variables.md) for advanced overrides. The in-repo example file should not advertise it as a standard env var to set.
>
> ---
>
> ## 2. Per-model base URL naming and fallback to vendor-level base URL
>
> **Current state:** For providers such as Qwen, Moonshot, DeepSeek, MiniMax, and Zhipu, the app only supports **per-model** base URL environment variables, whose names are derived from the **model id**:
>
> - Examples: `QWEN_QWEN3_235B_BASE_URL`, `QWEN_QWEN3_5_397B_BASE_URL`, `MOONSHOT_KIMI_K2_5_BASE_URL`, `DEEPSEEK_DEEPSEEK_V3_2_BASE_URL`, etc.
> - Logic in `src/lib/ai/provider.ts` (`getPerModelProvider`): `baseURL = process.env[prefix + "_" + modelId.toUpperCase().replace(/[^A-Z0-9]/g, "_") + "_BASE_URL"]`.
> - If that variable is unset, the app throws and requires the user to set a per-model URL.
>
> **Problems:**
>
> 1. **Binding the env var name to `model_id`** is unusual. Most ecosystems use a **single vendor-level base URL** (e.g. `OPENAI_BASE_URL`, `ANTHROPIC_BASE_URL`, `GEMINI_BASE_URL`). Users expect to set e.g. `MOONSHOT_BASE_URL` or `QWEN_BASE_URL` once and use any model from that provider.
> 2. **No fallback:** When a per-model URL is not set, the app does not try a vendor-level URL; it fails. So “per-model URL only” is the only supported pattern for these providers, which does not match common practice.
>
> **Proposal:**
>
> - **Keep** per-model base URLs for the “Per-model base URLs” use case (e.g. different endpoints per model).
> - **Add** vendor-level base URL environment variables for each of these providers, e.g.:
>   - `QWEN_BASE_URL`
>   - `MOONSHOT_BASE_URL`
>   - `DEEPSEEK_BASE_URL`
>   - `MINIMAX_BASE_URL`
>   - `ZHIPU_BASE_URL`
> - **Resolution order:** For a given provider and model:
>   1. If the **per-model** base URL env var is set (e.g. `MOONSHOT_KIMI_K2_5_BASE_URL`), use it.
>   2. Else if the **vendor** base URL env var is set (e.g. `MOONSHOT_BASE_URL`), use it.
>   3. Else, if the provider requires a base URL (e.g. no public default), fail with a clear error asking the user to set either the per-model or the vendor-level URL.
>
> This way, “Per-model base URLs” remain supported for advanced cases, and in the common case where all models of a provider use the same endpoint, a single `MOONSHOT_BASE_URL` / `QWEN_BASE_URL` etc. is enough and aligns with common practice.
>
> ---
>
> ## Summary
>
> - **.env.example:** Remove the commented `LLM_MODEL` line.
> - **Provider base URLs:** Introduce vendor-level `*_BASE_URL` env vars for Qwen, Moonshot, DeepSeek, MiniMax, Zhipu; use them when the corresponding per-model base URL is not set.
>
> ### Proposed Solution
>
> See Statement
>
>
> ### Alternatives Considered
>
> _No response_
>
> ### Feature Area
>
> AI / Chat / Agent
>
> ### Additional Context
>
> _No response_</issue_description>
>
> <agent_instructions>Please fix the bugs reported in this issue.</agent_instructions>
>
> ## Comments on the Issue (you are @copilot in this section)
>
> <comments>
> </comments>
>

</details>

<!-- START COPILOT CODING AGENT SUFFIX -->

- Fixes zjowowen/InnoClaw#15

<!-- START COPILOT CODING AGENT TIPS -->
---

📍 Connect Copilot coding agent with [Jira](https://gh.io/cca-jira-docs), [Azure Boards](https://gh.io/cca-azure-boards-docs) or [Linear](https://gh.io/cca-linear-docs) to delegate work to Copilot in one click without leaving your project management tool.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65e08f940ac9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
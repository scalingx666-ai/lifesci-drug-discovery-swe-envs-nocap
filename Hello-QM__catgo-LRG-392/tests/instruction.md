# Issue

**Title:** feat(chat): let client-direct providers (DeepSeek/Qwen/Kimi) build & edit workflows

## Description

**Problem:** CatBot on client-direct providers (DeepSeek/Qwen/Kimi) could only `run_workflow` — it refused to create or modify workflows (e.g. couldn't change a node's params). The build/edit tools (`create_workflow`, `add_node`, `remove_node`, `connect_nodes`, `set_node_params`, `validate_workflow`, …) were fully defined in `workflow-tools.ts` and implemented in `workflow-tool-executor.ts`, but **never registered into the client tool set** — only the SDK/MCP path (Claude Code/Codex/Gemini) had them via `catgo_workflow`.

**Fix:** register `WORKFLOW_TOOL_DEFINITIONS` through `execute_workflow_tool`, resolving the active WorkflowEditor's tab via a new `resolve_workflow_tab_id()` (slice key == the editor's handler key, verified). Skips `run_workflow` (already registered with a richer saved-config impl) and `plan_and_build_workflow` (no executor handler yet). Updates the client system prompt so the model knows it can build/modify, not just run.

Mutations dispatch to the open WorkflowEditor (needs backend + an open workflow); degrade gracefully ("open a workflow first") otherwise.

Verified: type-clean (no new svelte-check errors); tab routing confirmed against `WorkflowEditor.svelte` + `iter_workflow_slices`. Live-confirmed the SDK/MCP path already works (set_params ENCUT 520→600); this PR brings the same to client-direct providers.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42c624c01b4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
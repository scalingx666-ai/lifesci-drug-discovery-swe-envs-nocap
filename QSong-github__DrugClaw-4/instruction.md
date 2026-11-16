# Issue

**Title:** fix: restore original codegen-first flow and simple LLM planning

## Description

Revert Code Agent to codegen-first with template fallback (was reversed to template-first in e0ddac2), and restore Retriever Agent to simple keyword-suggestion LLM planning without constrained task classification.

This fixes key entity extraction (drugs/other) and the Code Agent generating code instead of attempting template path first.

Safety improvements (code validation, safe builtins, SIGALRM timeout) are preserved.

https://claude.ai/code/session_011DLLuavZ6UpM1NWBbdPV47

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15b6a0987b00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
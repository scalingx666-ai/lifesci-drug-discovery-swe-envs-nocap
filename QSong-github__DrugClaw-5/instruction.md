# Issue

**Title:** Enhance LLM response formatting with rich Markdown and folder-based q…

## Description

…uery logs

- Add response_formatter.py with formatting skills: answer cards, evidence tables, confidence badges, reasoning traces, source citations
- Refactor query_logger.py to folder-based storage: each query gets its own directory with answer.md, metadata.json, reasoning_trace.md, evidence.json, and full_result.pkl
- Enhance agent_responder.py prompts to instruct LLM to produce structured Markdown (tables, headers, code spans, blockquotes, TL;DR)
- Integrate wrap_answer_card() in main_system.py finalize flow so printed output and logged files are rich Markdown report cards

https://claude.ai/code/session_01KjsoCHE8nGJDCAp3BZd7Gh

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `efabaefdfd74`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
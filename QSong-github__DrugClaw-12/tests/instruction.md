# Issue

**Title:** Add fuzzy entity matching to improve retrieval robustness

## Description

Introduce EntityResolver that sits between entity extraction and skill querying to handle typos, case mismatches, and synonym variations:

- LOCAL_FILE skills: build an in-memory index of known entity names and use difflib.get_close_matches() for fuzzy matching (zero new deps)
- REST_API/CLI skills: ask the LLM to generate canonical names, common synonyms, and typo corrections for wider API query coverage
- Integrated into RetrieverAgent pipeline with 15 comprehensive tests

https://claude.ai/code/session_01VLmnWhA6xUqDq3J7K3gXJe

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `962cdfa9eec7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
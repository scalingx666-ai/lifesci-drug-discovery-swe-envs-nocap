# Issue

**Title:** Add maskself and bench logging to self-bench plugin

## Description

- Support optional maskself parameter for RAG-mode benchmarking: maskself=True excludes the dataset's own skill (test other resources), maskself=False includes all resources (test retrieval capability), omitted uses direct LLM classification (backward compatible).
- Add BenchLogger that saves per-sample LLM input/output as JSON files (analogous to QueryLogger) for post-hoc analysis.
- Add DATASET_SKILL_MAP for dataset-to-skill-name mapping.
- Refactor bench.py files to use shared run_classification_bench helper.
- Add --maskself and --log-dir CLI flags to run_all.py.
- Add self_bench_logs/ to .gitignore.

https://claude.ai/code/session_013aPLV15d1apnYyiv67PrpB

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c3ecaaa033a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
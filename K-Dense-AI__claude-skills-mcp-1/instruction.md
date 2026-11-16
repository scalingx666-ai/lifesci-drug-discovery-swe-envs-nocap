# Issue

**Title:** feat: implement background skill loading and improve search engine functionality

## Description

- Added a new LoadingState class to track the progress of background skill loading, ensuring thread-safe operations.
- Refactored the skill loading process to load skills in batches, allowing for incremental indexing and improved performance.
- Updated the SkillSearchEngine to support thread-safe access and dynamic skill addition.
- Enhanced the SkillsMCPServer to provide loading status during skill retrieval, improving user experience.
- Revised README.md to include setup instructions for using the new background loading feature.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a572be569168`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
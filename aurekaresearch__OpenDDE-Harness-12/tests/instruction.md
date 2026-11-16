# Issue

**Title:** fix(protein_design): bound post-filter selection

## Description

## Summary

Fix PostFilter failures caused by requiring verbose rankings for every eligible candidate, even when only a small Top-K was requested.

- Bound the candidate shortlist using multiple metrics and sequence diversity.
- Return only Top-K decisions with concise explanations.
- Synchronize antibody and minibinder prompts, skills, and output validation.
- Reject truncated responses, including at the output-token ceiling.
- Preserve all candidates and shortlist membership for auditing.
- Distinguish unselected, not-shortlisted, and hard-rejected candidates.
- Fix cancellation handling, fallback ranking, and failed-candidate visibility.

## Verification

- Python suite: 1892 passed, 21 deselected.
- Tracing dashboard: 62 passed.
- TUI build, Ruff, Prettier, and git diff checks passed.
- Additional TUI suite: 972 passed, 5 failed. The same five failures were reproduced on unchanged main and are unrelated to this PR.

Regression tests cover large candidate pools, invalid rankings, oversized evidence, truncated responses, fallback behavior, cancellation, and empty eligible pools.

## Risks and limitations

- Shortlisting is a context-budget heuristic, not a guarantee of globally optimal biological selection.
- Large explicit Top-K values still increase model costs.
- Unranked candidates now have null ranks; the bundled dashboard supports this.
- Live LLM selection and real GPU refolding were not tested.
- No production deployment is included.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8bb8684b2d31`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Pin pydantic-ai<2.0.0 to avoid breaking API change

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

Suggested fix, not sure if necessary, but seems to be an issue. 
pydantic-ai 2.0.0 was released on 2026-06-23  (today) and introduced breaking API changes: removed \`output_retries\` from \`Agent.__init__()\` and moved \`OpenAIModel\`. This breaks \`tests/bofire/strategies/test_llm.py\` and the \`types\` check on all branches including \`main\`. 
Suggest pin to \`<2.0.0\` until the LLM strategy code is properly migrated to the new pydantic-ai 2.x API.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

### Have you updated `CHANGELOG.md`?

yes

## Test Plan

No code changes. The fix constrains the \`pydantic-ai\` version to \`>=0.1,<2.0.0\` in \`pyproject.toml\`. CI will install a compatible version and \`test_llm.py\` should pass."

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bcea0d461e04`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
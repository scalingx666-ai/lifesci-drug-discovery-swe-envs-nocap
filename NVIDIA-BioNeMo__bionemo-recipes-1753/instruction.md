# Issue

**Title:** ci: limit Dependabot to security updates only

## Description

### Description

Dependabot currently opens weekly version-bump PRs for gitsubmodule, docker, uv and pip ecosystems, which is more churn than reviewers want. Setting `open-pull-requests-limit: 0` on every update entry disables scheduled version-update PRs while leaving **security** update PRs unaffected — [Dependabot security updates are not subject to `open-pull-requests-limit`](https://docs.github.com/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference#open-pull-requests-limit-).

The entries themselves are kept (rather than deleted) so the ecosystem/directory configuration continues to apply to security updates, and so bumping the limit back up re-enables version updates in one line.

```diff
   - package-ecosystem: "uv"
     ...
-    open-pull-requests-limit: 1
+    open-pull-requests-limit: 0
```

### Type of changes

- [x] Other (please describe): CI/dependency-bot configuration

### CI Pipeline Configuration

No test changes; config-only.

### Pre-submit Checklist

- [x] I have tested these changes locally (pre-commit `check-yaml`, `end-of-file-fixer`, `trailing-whitespace`, `check-copied-files` pass on the changed file)
- [ ] I have updated the documentation accordingly
- [ ] I have added/updated tests as needed
- [ ] All existing tests pass successfully

Link to Devin session: https://nvidia-cloud.devinenterprise.com/sessions/06fd08c615644d679ff5b6d4bd727d9b
Open in Devin Desktop: https://nvidia-cloud.devinenterprise.com/desktop/session/06fd08c615644d679ff5b6d4bd727d9b?variant=devin

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `361c506b7009`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
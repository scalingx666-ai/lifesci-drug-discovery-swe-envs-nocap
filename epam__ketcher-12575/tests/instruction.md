# Issue

**Title:** #12574 - Open separate Dependabot PRs for major GitHub Actions updates

## Description

Summary

Dependabot now puts only minor and patch updates of GitHub Actions in the grouped PR. Each major update comes in its own PR.

yaml
    groups:
      github-actions:
        patterns:
          - '*'
        update-types:   # new
          - minor
          - patch

Why: in #12550 the grouped PR also moved anthropics/claude-code-action from 0.0.63 to 1.0.264. Version 1 removed the direct_prompt and model inputs, which claude-implement-autotests.yml still uses. CI was green, because that workflow does not run on PRs, so the change was easy to miss. A separate PR makes a major update visible, and the reviewer reads its release notes before approving.

The file comment now says "once a quarter" instead of "per month", to match interval: quarterly.

Evidence
Before: #12550 grouped 5 updates, 3 of them major (actions/github-script 7 to 9, anthropics/claude-code-action 0.0.63 to 1.0.264, sonarsource/sonarqube-scan-action 7 to 8). After: the group takes only minor and patch. Updates that match no group, the majors, come as individual PRs ([GitHub Docs](https://docs.github.com/en/code-security/dependabot/dependabot-version-updates/optimizing-pr-creation-version-updates)). The YAML parses.
Dependabot validates the file after the merge; errors show under Insights → Dependency graph → Dependabot.

Verified in the app: n/a, Dependabot configuration only.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2202909801d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
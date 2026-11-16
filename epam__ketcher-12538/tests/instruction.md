# Issue

**Title:** #12537 - Run AI workflows in the protected ai-workflows environment

## Description

## Summary

The four AI workflow jobs now run in the `ai-workflows` environment. The environment holds the AI secrets and has required reviewers, so a job gets the secrets only after a maintainer approves the run. A new workflow adds the `workflows-changed` label to a PR that changes CI or agent configuration, so the approver knows to read those changes first.

```text
.github/
├── labeler.yml                           # new: paths for the workflows-changed label
└── workflows/
    ├── label-workflow-changes.yml        # new: actions/labeler on pull_request_target
    ├── claude-review.yml                 # + environment: ai-workflows
    ├── claude-implement-autotests.yml    # + environment: ai-workflows
    ├── claude-create-autotest-request.yml  # + environment: ai-workflows
    ├── openai-create-autotest-request.yml  # + environment: ai-workflows
    └── README.md                         # approval rule + new table row
```

The label covers `.github/`, `.claude/`, `.agents/`, `AGENTS.md`, `CLAUDE.md` and `.mcp.json`. `sync-labels: true` removes the label when those changes are reverted. The labeler runs on `pull_request_target`, so it uses this file and `.github/labeler.yml` from the base branch, and a PR cannot turn off its own check. It does not check out PR code and uses no secrets.

## Evidence

- **Before:** the four jobs read the AI secrets from the repository level and start without approval.
  **After:** each job has `environment: ai-workflows`. The YAML of all six workflow files parses. The `ai-workflows` environment exists with required reviewers (checked through the environments API).
- The labeler cannot run on this PR: `pull_request_target` uses the workflow from `master`, where it does not exist yet. It is tested on the first PR after the merge that changes `.github/`.

Verified in the app: n/a, CI configuration only.

## Merge Danger

**Door:** two-way

After the merge, every AI workflow run waits for approval from a required reviewer of `ai-workflows`. The secret names in the environment must match the names the workflows use (`CLAUDE_CODE_OAUTH_TOKEN`, `ANTHROPIC_API_KEY`, `OPENAI_API_KEY`); if one is missing, that run fails at its first API call.

**Blast Radius:** CI

Steps after the merge:

1. Create the `workflows-changed` label with a visible color, if it does not exist.
2. A required reviewer approves one AI run, for example a Claude review, and checks that it works.
3. After that run succeeds, delete the AI secrets at the repository level. Until then, a workflow added in a PR can still read them.

---



Memory bank: not needed (CI workflow change; documented in `.github/workflows/README.md`)

🤖 Generated with [[Claude Code](https://claude.com/claude-code)](https://claude.com/claude-code)

https://claude.ai/code/session_01XvZAmSJCtzryj23hrVKazK

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be4b299b1201`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** #12512 - Add Danger PR checks: title, branch, linked issue, size, PR-type contract

## Description

## Summary

Danger now checks every PR to `master` and `release/**`: the PR title, the branch name, the linked issue, the size, and the PR-type contract from `.memory-bank/review-workflow.md`. #12509 removed the "PR type" checkboxes from the template, so Danger finds the type from the linked issue's type and the labels instead.

```text
danger.yml  (pull_request_target, base branch checked out)
  danger ci --failOnErrors
    dangerfile.ts                  # reads the PR through the GitHub API
      pulls.listFiles              # changed files and line counts
      GraphQL closingIssuesReferences { number, issueType }
      checkPullRequest()           # scripts/pr-checks.mjs, pure rules
    → one Danger comment; the job fails on a fail
```

| Rule | Fails | Warns |
| --- | --- | --- |
| Title | `#<issue>` in a form other than `#<issue> - <title>`; no issue prefix while an issue is linked. `Backmerge: ` allowed | En dash instead of the hyphen; an issue in the title the PR does not link |
| Branch | Contains `#` | |
| Linked issue | | None |
| Size | | Over 400 changed lines (lockfiles and snapshots not counted); skipped on `large-scale-change` |
| Unit test | | `ketcher-core` `domain/` or `editor/operations/` changed, no unit test changed |
| Feature (issue type) | No file in `openspec/changes/`; backmerges skipped | |
| Bug (issue type) | | No unit or E2E test changed |
| `large-scale-change` label | A required section is missing or still holds the template text | |

Why `pull_request_target`: on `pull_request`, fork PRs get a read-only token, so Danger can't comment. `pull_request_target` runs in the context of the base branch. It is safe only because no step checks out or runs PR code. The workflow and `dangerfile.ts` both say so.

## Evidence

**Rule tests:** `npm run test:scripts`: 50 passed, 16 of them new in `scripts/pr-checks.test.mjs` (every rule, both the passing and the failing case, the backmerge and lockfile exceptions, and the unedited large-scale change template).

**The rules replayed over the last 150 merged PRs:**

| Finding | Count | Notes |
| --- | --- | --- |
| fail: feature | 10 | All are real Feature PRs with no OpenSpec change, most merged before the contract (2026-10-27) |
| fail: title | 5 | `#12266-Refactor`, `#12130 New …`, `6365 - …`, `#7681-monomer …` |
| fail: branch | 2 | Both backmerges, branch `#11981-…` |
| warn: title (en dash) | 27 | Would be a fail without the en dash exception |
| warn: linked issue / size / bug fix / unit test | 38 / 20 / 16 / 10 | |

The first draft failed 36 titles (24%). Allowing `Backmerge: ` and turning the en dash into a warning brought that down to the 5 real errors.

**Real `danger pr` runs** (text only, nothing posted):

```text
#12510  ✓ warnings only: No linked issue
#12184  ✗ #8853 is a Feature, and the PR has no OpenSpec change   (+ warn: en dash)
#12487  ✗ #10827 is a Feature, and the PR has no OpenSpec change
#12040  ✗ Branch `#11981---Copy-paste-…` contains `#`             (+ warn: Bug, no test)
```

**Not proven yet:**
- The workflow itself. `pull_request_target` uses the workflow file from the base branch, so Danger can't run on this PR. It first runs on PRs opened after this merges into `master`.
- A fork PR: none is open now to run against.
- The `large-scale-change` check: tests only. The label doesn't exist yet (plan task 2.2.8).

Verified in the app: n/a. CI only.

## Merge Danger

**Door:** two-way. Delete `danger.yml` or revert the commit.

**Blast Radius:** every PR

- The Feature rule fails Feature PRs without an OpenSpec change. In the replay that was 10 of 150 merged PRs. Until authors adapt, expect red Danger checks on Feature PRs. The fix is to add the change, or to link the right issue type.
- A fail blocks merge only if a ruleset makes the Danger check required. Today none does.
- `pull_request_target` gives the job a write token. A future edit that checks out the PR head (`ref: ${{ github.event.pull_request.head.sha }}`) or runs its scripts would hand that token to PR code. Don't.
- New root devDependency `danger@14.1.0`. `npm audit` counts are unchanged (0 critical, 19 high, as on the base).

Part of #12512

Memory bank: `.memory-bank/review-workflow.md` (PR-type table, Gates). Also `.github/workflows/README.md`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b3b39169515f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
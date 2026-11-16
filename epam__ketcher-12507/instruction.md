# Issue

**Title:** ci: align Claude PR Review skill set with master and move to Opus 5.5

## Description

## Summary

`claude-review.yml` silently produced no review on PRs whose branches predate the skills restructure:

```text
runner checkout (PR merge ref, old tree)
  .agents/skills/        -> old set (code-review, implement, implement-spec, tdd)
claude-code-action
  restores .claude from origin/master        -> new symlinks, incl. review-pr
  does NOT restore .agents
  => .claude/skills/review-pr symlink broken
  => /review-pr never loads, prompt is plain text
  => agent improvises, but every Bash(gh ...) call is denied
     (--allowedTools whitelists only the inline-comment MCP tool)
  => agent gives up, SDK run ends green, no comment posted
```

Changes:

```diff
 - name: Checkout repository
   uses: actions/checkout@v6
   with:
     fetch-depth: 1
+- name: Align agent skills with master
+  run: |
+    git fetch origin master --depth 1
+    rm -rf .agents
+    git checkout origin/master -- .agents
 - name: PR Review with Progress Tracking
   uses: anthropics/claude-code-action@v1
   ...
   claude_args: |
-    --allowedTools "mcp__github_inline_comment__create_inline_comment"
+    --allowedTools "mcp__github_inline_comment__create_inline_comment" "Bash(gh pr view:*)" "Bash(gh pr diff:*)" "Bash(gh issue view:*)" "Bash(gh pr comment:*)"
-    --model "claude-opus-4-7"
+    --model "claude-opus-5-5"
```

- The alignment step mirrors the action's own trust model: it copies `.agents` from `master` so the skill set matches what the restored `.claude` points at. Files only; nothing from the PR head is executed.
- The extra `--allowedTools` patterns are a safety net so an agent that falls back to improvising can still read the diff (they duplicate the `/review-pr` skill's `allowed-tools` frontmatter, which is what actually grants them once the skill loads).
- Model bump: `claude-opus-4-7` is legacy (two generations back); current recommended default is `claude-opus-5-5`.

## Evidence

- **Before (stale branch, PR #12245, run 40677147943):** `ls: cannot access '.agents/skills/review-pr/': No such file or directory`; then three `gh pr view` attempts answered `This command requires approval`; run ended `success` with no comment.
- **After (current branch, PR #12487, run 40674671525):** `review-pr` present in the SDK `slash_commands` list; diff fetched; 6 inline findings and the review brief posted —  That run already proves the skill path works when the tree is current; this PR makes it independent of branch age. The alignment step itself will be exercised by the next `Run Claude Review` run after merge.

## Merge Danger

**Door:** two-way (workflow file + docs row revert trivially)

**Blast Radius:** Claude PR Review workflow only. The step runs before the action and executes no PR-supplied code.

Memory bank: `.github/workflows/README.md` row for `claude-review.yml` updated (verified-in-CI status, root cause, model).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43f70e73fb6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
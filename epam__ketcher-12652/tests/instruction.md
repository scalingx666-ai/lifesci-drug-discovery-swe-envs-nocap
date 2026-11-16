# Issue

**Title:** Upgrade husky to 9 and run lint and related tests only on changed files

## Description

## Summary

The git hooks now check only what you change. Husky moves from 8 to 9. Before this PR, `pre-push` never ran: it was stored without the executable bit (`100644`). `pre-commit` ran Prettier over every workspace on each commit, and in a git worktree it failed on the missing `.husky/_/husky.sh`.

```
pre-commit  npx lint-staged                     (.lintstagedrc.json)
            staged *.{js,jsx,ts,tsx,mjs,cjs} -> prettier --write, eslint --quiet
            staged *.json                    -> prettier --write
            staged *.{css,less}              -> stylelint --fix
pre-push    npx lint-staged --diff="origin/master...HEAD"   (lint-staged.pre-push.mjs)
            changed packages/<pkg>/**        -> npm run test:unit -w packages/<pkg>
                                                -- --findRelatedTests <files>
```

- `package.json`: `"postinstall": "husky install"` becomes `"prepare": "husky"`, as husky 9 documents. The `precommit` and `prepush` scripts are removed.
- The hook files are plain commands. Husky 9 runs them through `.husky/_/h`, so they no longer source `husky.sh` or need the executable bit.
- `ketcher-autotests/package.json`: its lint-staged ran `eslint .`, which linted the whole folder on every commit. It now lints the staged files only.

## Evidence

- **pre-commit, red:** a staged `packages/ketcher-core/src/hookCheckTmp.ts` containing `export const hookCheckTmp: any = 1;` gives `@typescript-eslint/no-explicit-any` and `husky - pre-commit script failed (code 1)`. No commit is made.
  **pre-commit, green:** this PR's commits pass through the hook in 2 s.
- **pre-push, red:** a local commit that changes `toFixed(8)` to `toFixed(7)` in `utilities/toFixed.ts` runs `jest --findRelatedTests` on that file in `ketcher-core` and fails: `FAIL __tests__/utilities/toFixed.test.ts`, exit 1, 13 s.
  **pre-push, green:** a comment-only change to the same file passes in 12 s. On this branch, which touches only config files, the hook reports "No staged files match any configured task" and exits 0.
- `npm run check:agent-docs`: ok.

Verified in the app: n/a. Only dev tooling changes; nothing reaches the editor.

## Merge Danger

**Door:** two-way. Revert the PR and run `npm install`.

Everyone's `core.hooksPath` changes from `.husky` to `.husky/_` on their next `npm install`. A branch made before this PR still has the old hook files that source `husky.sh`. Husky 9 keeps a stub `husky.sh` that prints a deprecation notice, so those hooks still run. The pre-push hook needs an up-to-date `origin/master`; with a stale one it tests more files, not fewer. CI runs `npm ci`, which now runs `prepare` and sets the hooks path on the runner; CI never commits, so nothing else changes there.

Two things to coordinate with #12638 (ESLint to Oxlint): whichever PR merges second replaces `eslint --quiet --no-warn-ignored` in `.lintstagedrc.json` and in `ketcher-autotests/package.json` with the Oxlint command.

**Blast Radius:** dev-tooling

---

Memory bank: not needed. `DEVNOTES.md` (setup guide) gains a "Git hooks" section, and `.agents/skills/ketcher-flow/shared/LOCATIONS.md` adds `npx husky` for worktrees made by copying `node_modules`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b031cc21436`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
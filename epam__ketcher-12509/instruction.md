# Issue

**Title:** Add ketcher-pr skill and Summary, Evidence, Merge danger to the PR template

## Description

## Summary

Agents now write PR titles and bodies with a new `ketcher-pr` skill: the Ketcher adaptation of [`pr` from `mattpocock/skills`](https://github.com/mattpocock/skills/blob/main/skills/engineering/pr/SKILL.md). Both PR templates take that skill's sections, and drop the PR type and Check list tick boxes.

```diff
 .github/pull_request_template.md
-## How the feature works? / How did you fix the issue?
-## PR type          # tick boxes
-## Check list       # tick boxes
+## Summary          # <diagram, diff-sketch, or tree>
+## Evidence         # before / after
+## Merge Danger     # door and blast radius
+Closes #<issue>
+Memory bank: <file, or "not needed">
```

```diff
 .github/PULL_REQUEST_TEMPLATE/large-scale-change.md
+## Summary
 ## Split decision
 ## Codemod
 ## Evidence of equivalence      # takes the place of Evidence
 ## Review map
-## Revert plan
+## Merge Danger
+### Revert plan                 # describes the door
+Closes #<issue>
+Memory bank: <file, or "not needed">
```

Why the tick boxes go: 15 of the last 30 merged PRs tick none, and no workflow or review skill reads them. Each item is visible in the diff or the PR header, or belongs to an automated check.

The PR type itself stays: the PR-type contract in `.memory-bank/review-workflow.md` gains **Refactor** and **Small change**, so every `ketcher-flow` kind has a row. The AI review names the type in its brief, from the diff and the linked issue, instead of reading a tick box.

```text
.agents/skills/
├── ketcher-pr/SKILL.md        # upstream text word for word, plus "In Ketcher" paragraphs
├── ketcher-flow/              # SKILL.md, TRACKER.md point to ketcher-pr; flows stop asking to tick a PR type
└── prepare-release/SKILL.md   # no checklist to fill
.claude/skills/ketcher-pr      # symlink, as for the other shared skills
AGENTS.md                      # skill list gains "PR body"
```

## Evidence

- **Before:** agents copied the template sections by hand per `TRACKER.md`; humans and agents ticked boxes nobody read.
  **After:** this PR body is written with `ketcher-pr`. A script check confirms every line of upstream's _Sections_ is in `ketcher-pr` unchanged, except `GLOSSARY.md` → `.memory-bank/glossary.md`. `npx prettier --check` passes on the changed files (the warning on `ketcher-flow/SKILL.md` exists on `master` too).

### Verified in the app

n/a: no change to the editor.

## Merge Danger

**Door:** two-way

Reverting this PR restores the old templates and agent rules.

**Blast Radius:** process

Every new PR, human or agent, opens with the new sections and no tick boxes. Nothing in CI reads the old sections. Until Danger exists (planned, Phase 3), the PR type is recorded only in the AI review brief.

---

Memory bank: `.memory-bank/review-workflow.md` (PR-type contract, large-scale change body sections).

Part of #12512

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e4edebf97db`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
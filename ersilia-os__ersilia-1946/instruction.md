# Issue

**Title:** Keep the README's two date sentences apart

## Description

- [ ] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable? (no tests exist for this script)
- [x] Have you successfully ran tests with your changes locally? (no test suite covers this script; checked by rendering `write_information_1` by hand, see below)

**Description**

A packaged model's README read `This model was incorporated on 2026-10-19.Last packaged on 2026-10-20.`, with no space between the two sentences. This pull request fixes that.

**Changes to be made**

In `write_information_1` in `.github/scripts/readme_formatter.py`, drop the `text.rstrip("\n")` that ran before "Last packaged on", and the blank line before it. Both sentences stay in one paragraph, each on its own line. Markdown renders the single newline as a space.

The same `rstrip` also glued "Last packaged on" to the end of the description when a model had a packaging date but no incorporation date. That case is fixed too.

**Status**

Checked by rendering `write_information_1` before and after the change:

| Metadata | Before | After |
|---|---|---|
| Both dates | `...2026-10-19.Last packaged on 2026-10-20.` | two lines, one paragraph |
| Incorporation date only | one extra blank line | no extra blank line |
| Packaging date only | `Desc line.Last packaged on ...` | separate paragraph |

Rendering the metadata of [eos8nyg](https://github.com/ersilia-os/eos8nyg) with the change gives `...incorporated on 2026-10-19.\nLast packaged on 2026-10-20.\n\n`.

Model READMEs change only the next time their CI regenerates them. The `ersilia-model-workflows` workflows download this script from `master` at run time, so no change is needed there.

**To do**

Nothing further.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27a5eede727b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
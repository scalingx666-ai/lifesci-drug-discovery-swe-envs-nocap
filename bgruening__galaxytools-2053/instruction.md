# Issue

**Title:** tool bot: don't persist checkout credentials, no shell tools in review

## Description

Step 1 from  Workflow changes only.

- **Checkout no longer saves the token in `.git/config`** (`persist-credentials: false` on every bot checkout). The three steps that push now get the token from `GH_TOKEN` through `gh auth setup-git`.
- **Review has no shell tools.** The bot offers `planemo_test` and `run_in_conda` (`shell=True`) whenever planemo, micromamba or conda is on PATH. The review job no longer installs planemo or micromamba and removes the runner's `/usr/bin/conda` symlink. A guard step fails the job if any of them is still on PATH. PR CI already lints and tests.
- **Removes `gxy-on-fork-pr-notify.yml`.** From November 2, 2026 GitHub blocks `pull_request_target` on public repos unless an Actions policy allows it, so this workflow would fail at startup on every labeled PR (screenshot below). It only posted a notice; the bot's upcoming fork review replaces it.

Only using maintainer comments in feedback mode is done in d-callan/gxy-tool-bot#36 (merged) and comes with the next bot release.

zizmor: all 6 `artipacked` findings are gone, no new ones. actionlint is clean.

Tested the changed steps on a throwaway repo:

![test run](https://github.com/user-attachments/assets/2d32126a-67b4-422c-bc5b-1257eb328551)

What a blocked `pull_request_target` run looks like:

![blocked run](https://github.com/user-attachments/assets/43d46479-d378-4ce4-a85d-f018bd1ca884)

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [ ] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [ ] This PR updates an existing tool or tool collection
* [x] This PR does something else (explain below)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `392432b1d5f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
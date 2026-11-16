# Issue

**Title:** tool bot: sync workflows with gxy-tool-bot 0.2.3

## Description

Step 2 from  Syncs the bot workflows with the gxy-tool-bot 0.2.3 templates (galaxyproject/gxy-tool-bot#36 to #43) and pins `gxy-tool-bot==0.2.3`.

- **Feedback only follows maintainers.** The bot reads comments only from users with write access, and the plan comment must be the bot's own.
- **No job holds both the LLM key and a write token.** Review and feedback are split into separate jobs: the model runs with the key and read-only access, and a later job without the key posts comments and pushes.
- **The model's commands run as a separate user.** `planemo_test`, `run_in_conda` and the other commands in feedback, implement and autoupdate run as `gxyexec`: no sudo, no docker, can't read the key or the token, and can't write outside the tool directory. The bot keeps testing tools as before.
- **New `gxy-on-fork-pr-review.yml`.** A maintainer adds the `tool-bot:review` label to a fork PR to get a review (comments only, no pushes). Nothing runs on open or push. Feedback stays off for fork PRs.
- Local settings kept: autoupdate runs daily with `max-parallel: 2`.

Before merging:
- Allow `pull_request_target` for `gxy-on-fork-pr-review.yml` in the Actions settings. GitHub blocks it on public repos without this from December 2, 2026, so fork review won't start after that.
- Optional: required reviewers on the `fork-review` environment, so each fork review waits for an approval. The first run creates the environment without any.
- Optional: a separate, revocable LLM key for fork reviews, as a secret in that environment.

Tested with these exact workflows and gxy-tool-bot 0.2.3 from PyPI on a test repo (fake LLM): tool request runs once; review and feedback pass and remove their labels, and feedback keeps executable scripts and tracked links; implement and autoupdate open their PRs; fork review runs only on a maintainer's label for PRs against the default branch, reviews the fork's commit and posts. The exec user was tested in all three flows with a real model in galaxyproject/gxy-tool-bot#37. actionlint is clean.

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [ ] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [ ] This PR updates an existing tool or tool collection
* [x] This PR does something else (explain below)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `074136fa753e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
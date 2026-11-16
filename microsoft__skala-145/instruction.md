# Issue

**Title:** Automatic pixi lockfile updates

## Description

(in a way). Since dependabot doesn't support pixi, this uses the [recommended GH action structure](https://pixi.prefix.dev/latest/integration/ci/updates_github_actions/#how-to-use) from the pixi dev team

Some items to discuss before merging:
- The GITHUB_TOKEN is a placeholder. We could consider PATs for the action
- The update cadence is ~bi-weekly

Another option would be [renovate](https://docs.renovatebot.com/modules/manager/pixi/) but this current action structure requires less maintained upstream code

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e07a009af471`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
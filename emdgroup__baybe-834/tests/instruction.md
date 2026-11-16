# Issue

**Title:** Use `BetaPrior` in MultiTask Botorch Preset

## Description

This PR changes the `BOTORCH` preset to use the `BetaPrior(2.5, 1.5)` in the multi task case.

This change was introduced in Botorch v.0.18.0 (see https://github.com/meta-pytorch/botorch/releases/tag/v0.18.0). Consequently, our `BOTORCH` preset no longer reflected the actual botorch defaults and failed.

This PR thus updates the `BotorchKernelFactory` to not simply use `HVARFNER` but to use the new prior in the multi task case instead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b028ecfaeb1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
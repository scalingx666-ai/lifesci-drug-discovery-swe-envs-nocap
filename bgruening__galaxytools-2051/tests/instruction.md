# Issue

**Title:** ffmpeg: update tool wrapper to 9.0.2

## Description

Hello! This is an automated update of `tools/ffmpeg`. Its main dependency `ffmpeg` is out of date — a newer version (7.1.1 → 9.0.2) is available on the conda-forge conda channel.

An agent applied the version bump and checked upstream for breaking changes and new parameters — review the diff as you would any automated change.

**Project home page:** https://ffmpeg.org

If you want to skip this version, close this PR without deleting the branch — it will be reopened only if an even newer version appears.

Any commit from another author than 'gxy-tool-bot' on this branch will prevent further auto-updates. To allow them again, delete the branch.

---

## Working on this tool

To review or improve this tool locally:

**If you don't have the repo yet** (forks and clones in one step):

```bash
gh repo fork bgruening/galaxytools --clone
cd galaxytools
git checkout tool-bot/autoupdate-ffmpeg
```

**If you already have the repo:**

```bash
git fetch origin
git checkout tool-bot/autoupdate-ffmpeg
```

The tool files are in `tools/ffmpeg/`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `392432b1d5f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
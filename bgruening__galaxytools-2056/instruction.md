# Issue

**Title:** grapetree: update tool wrapper to 3.0.0

## Description

Hello! This is an automated update of `tools/grapetree`. Its main dependency `grapetree` is out of date — a newer version (2.1 → 3.0.0) is available on the bioconda conda channel.

An agent applied the version bump and checked upstream for breaking changes and new parameters — review the diff as you would any automated change.

**Project home page:** https://github.com/achtman-lab/GrapeTree/releases

If you want to skip this version, close this PR without deleting the branch — it will be reopened only if an even newer version appears.

Any commit from another author than 'gxy-tool-bot' on this branch will prevent further auto-updates. To allow them again, delete the branch.

---

## Working on this tool

To review or improve this tool locally:

**If you don't have the repo yet** (forks and clones in one step):

```bash
gh repo fork bgruening/galaxytools --clone
cd galaxytools
git checkout tool-bot/autoupdate-grapetree
```

**If you already have the repo:**

```bash
git fetch origin
git checkout tool-bot/autoupdate-grapetree
```

The tool files are in `tools/grapetree/`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d39f8d5ef240`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
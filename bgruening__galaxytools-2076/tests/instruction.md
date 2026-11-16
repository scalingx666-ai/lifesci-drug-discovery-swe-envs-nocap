# Issue

**Title:** fadu: auto-generated tool wrapper (issue #2074)

## Description

This PR adds a Galaxy tool wrapper for **fadu**, a tool that performs fluorometric analysis of DNA unwinding (FADU) to quantify DNA damage and repair. The generated wrapper includes the tool XML, macros, and associated test data, addressing the request in issue #2074.

⚠️ The generating agent did not terminate naturally after 30 iterations, so the output may be incomplete. Please review the command line construction, parameter definitions, and test configuration carefully before merging.

.

---

## Working on this tool

To review or improve this tool locally:

**If you don't have the repo yet** (forks and clones in one step):

```bash
gh repo fork bgruening/galaxytools --clone
cd galaxytools
git checkout tool-bot/issue-2074
```

**If you already have the repo:**

```bash
git fetch origin
git checkout tool-bot/issue-2074
```

The tool files are in `tools/fadu/`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `311f505042c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
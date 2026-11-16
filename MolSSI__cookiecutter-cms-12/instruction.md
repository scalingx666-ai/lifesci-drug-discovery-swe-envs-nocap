# Issue

**Title:** Add auto-versioneer creation

## Description

This PR adds Versionneer to the cookiecutter's output. When the skeleton is made, the output directory is automatically executes the following commands:
```bash
git init
git add *
git commit -m "Initial commit after Comp. Chem. Cookiecutter creation"
git tag 0.0.0
```

This also means that `git` is required for this cookiecutter to work, but that is a reasonable cost I think.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8fdf2281a31a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
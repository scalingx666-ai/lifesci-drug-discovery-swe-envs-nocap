# Issue

**Title:** ci: stop tracking npm dependencies with Dependabot

## Description

### Description

Removes the `npm` ecosystem entry from `.github/dependabot.yml`. There are no JavaScript packages to track under `models/`, `recipes/`, or `interpretability/`, and the corresponding Dependabot update job fails on every run with:

```
dependency_file_not_found: "/interpretability/**, /models/**, /recipes/** not found"
```

(e.g. https://github.com/NVIDIA-BioNeMo/bionemo-recipes/actions/runs/34854284478), which surfaces as a failing check run on `main`.

The `gitsubmodule`, `docker`, `uv`, and `pip` entries are unchanged.

### Type of changes

- [x] Other (please describe): CI configuration cleanup

### Pre-submit Checklist

- [x] I have tested these changes locally (YAML validated; no tests apply)
- [ ] I have updated the documentation accordingly
- [ ] I have added/updated tests as needed
- [ ] All existing tests pass successfully

> [!NOTE]
> Committed via the GitHub API because `pre-commit` hook environments cannot be installed in this sandbox (fetches of non-NVIDIA GitHub repos are blocked by network policy, so `pre-commit install-hooks` fails with HTTP 403). The equivalent checks for this file were run manually: YAML parses, file ends with a newline, no trailing whitespace, and the file is not in `SOURCE_TO_DESTINATION_MAP`.

Link to Devin session: https://nvidia-cloud.devinenterprise.com/sessions/a150661b00314a47ba4a91ed66499856
Open in Devin Desktop: https://nvidia-cloud.devinenterprise.com/desktop/session/a150661b00314a47ba4a91ed66499856?variant=devin

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed8a1816d639`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
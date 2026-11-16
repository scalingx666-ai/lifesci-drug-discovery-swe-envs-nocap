# Issue

**Title:** chore: declare OSS dependencies for scanning + add repo-level skill card

## Description

Two changes supporting open-source dependency scanning and release documentation for this repo.

## 1. Declare the OSS dependency tree

**Problem:** the repo ships 40 Python files and had *zero* package-manager manifests, so open-source dependency scanners have no dependency tree to resolve and report nothing.

Black Duck's UV detector requires **`uv.lock` AND a `pyproject.toml` carrying `[tool.uv] managed = true`**, and extracts the tree with `uv tree --no-dedupe --frozen`. Both files are now at the repo root, and that exact command succeeds:

```
$ uv tree --no-dedupe --frozen
bionemo-agent-toolkit v0.1.0
├── gemmi v0.7.5
├── numpy v2.5.1
└── pyyaml v6.0.3
```

Those three are the complete third-party import surface across all 40 scripts — everything else imported is stdlib. They come from:

- `gemmi` → `complexa-binder-design/scripts/{pdb_interface,pipeline,preflight_design,pdb_to_boltz_template_cif}.py`
- `numpy` → `complexa-binder-design/scripts/validate_binders.py`, `protein-binder-design/scripts/metrics.py`
- `pyyaml` → `complexa-binder-design/scripts/pipeline.py`

All of these live in **native** skills under `workflows/`, so this manifest is genuinely this repo's to own — no sourced skill contributes a third-party import today. `.venv/` and `__pycache__/` are gitignored; `uv.lock` is intentionally committed.

> **Open question for review:** uv vs poetry. I used uv because the repo already drives its scripts with `uv run` and PEP-723 headers, and uv is a supported detector. Easy to swap if there's a standard we should follow instead.

## 2. Repo-level skill card

`docs/skill-card.md`, filling the NVIDIA skill card template for all 31 skills at `v0.1.0` — description, owner, license, use case, requirements, limitations, risks and mitigations, outputs, evaluation, ethical considerations.

Grounded in the repo rather than generic. The evaluation sections are a genuine strength: **103 functional eval cases + 220 trigger-eval queries, 31/31 skills covered.**

Known gaps are stated plainly rather than omitted:

- no `skill.oms.sig` signatures (`SRC-11`)
- no published `BENCHMARK.md` (`SRC-10`); eval *results* are gitignored
- SkillSpector runs advisory (`continue-on-error`), not merge-blocking

## Validation

There is no `.pre-commit-config.yaml` in this repo, and neither `plugin-sync.yml` nor `skill-security.yml` has a path filter matching these files, so **no CI will run on this PR.** Verified by hand:

- `uv tree --no-dedupe --frozen` → exit 0 (the exact command the scanner runs)
- `uv run --frozen python -c "import gemmi, numpy, yaml"` → imports OK
- `python3 scripts/plugin_sync.py --check` → OK, 31 skills, payload matches source

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4aa17931886`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
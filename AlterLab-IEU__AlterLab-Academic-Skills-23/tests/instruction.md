# Issue

**Title:** fix(site)+ci(pages): mobile layout, deploy hardening with live verify, daily freshness check, catalog upgrades (v2.7 phase 0)

## Description

## Why

The live catalog (https://alterlab-ieu.github.io/AlterLab-Academic-Skills/) has served **232** skills since 2026-07-02 while `main` has **239**. Deploy runs #8 and #9 sat in `deployment_queued` for `actions/deploy-pages@v4`'s default 10-minute timeout and were aborted, so `alterlab-skill-finder` and six social-science-workflow skills never went live. The page also broke on phones (556 px document at 390 px; the sticky filter bar covered 447 px of an 844 px viewport) and its meta still said 13 domains.

## What

- **Site fix (0.1)** — fluid grid (`minmax(min(330px,100%),1fr)`), `min-width:0` cards, `overflow-wrap:anywhere` descriptions, one swipeable chip row under 560 px, meta says 17 domains. Headless-verified: `scrollWidth == clientWidth` at 390 and 1440, 1/3 columns, sticky bar 147 px on phones, 239 cards, search + chip filter + copy all work, zero console messages.
- **Deploy hardening (0.2)** — `deploy-pages` timeout 20 min (`error_count: 10`, `reporting_interval: 10 s`); `push: tags: v*` and `release: published` triggers so every release republishes; a `verify` job that polls the live `skills.json` (cache-busted, `Cache-Control: no-cache`) every 30 s for up to 10 min until `summary.total` matches the repo and no repo skill is missing, otherwise fails the run with a clear message. A `v*` tag deployment policy was added to the `github-pages` environment (it only allowed `main`).
- **Freshness check (0.3)** — `catalog-freshness.yml`: daily cron + manual; compares the live total, skill list and `Last-Modified` against `main`; if stale, re-dispatches `gh-pages.yml` and opens/refreshes exactly one issue "Live catalog is stale"; closes it when fresh. Dry-run against the current live site correctly reports stale (232 vs 239, 7 missing, first `alterlab-meta-analysis`).
- **Catalog upgrades (0.4)** — `gen_catalog.py` emits `summary.version` (from `pyproject.toml`) and `summary.generated_at` (ISO date; `--check` carries the committed date over so the stamp can never fail the gate). The page renders "v2.6.1 · generated 2026-09-04", per-card **Source** (GitHub folder) and **Install** (`/releases/download/v<version>/skill-<name>-<version>.zip`) links, an install block above the grid (`/plugin marketplace add …` + domain-specific `/plugin install alterlab-<domain>@alterlab-academic-skills` with a copy button), the `alterlab-skill-finder` / `alterflow` front door in the lede, OG/Twitter meta, canonical, theme-color, and an inline SVG favicon (no 404 fetch). No build step, no external scripts or fonts, no hard-coded domain count.

## Gates

`audit_skills.py`, `gen_catalog.py --check`, `gen_marketplace.py --check`, `gen_portability.py --check`, `gen_agents_catalog.py --check --strict`, `gen_security_scan.py --check --strict`, `check_claudeai_compat.py --strict`, `ruff` — all green locally. `pytest`: 3598 passed; the single local failure (`test_mcp_manifest.py`, backslash paths) is a pre-existing Windows-only path-separator issue unrelated to this branch and green on Linux CI. `check_spec.py` needs the Node `skills-ref` binary, which is absent locally; CI runs it.

After merge: `gh workflow run gh-pages.yml` → `verify` must go green → live page shows 239 and renders `alterlab-skill-finder`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0064fd54180`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
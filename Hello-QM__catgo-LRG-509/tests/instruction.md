# Issue

**Title:** feat(release): mirror release assets to Cloudflare R2 for mainland-China downloads

## Description

## Why

Users in mainland China report GitHub is unreachable — they can neither download CatGo installers nor receive in-app updates (the Tauri updater endpoint also points at github.com).

## What

- **New workflow `r2-release-mirror.yml`** — on `release: published` (or manual dispatch with a tag):
  - waits for the async build workflows to finish attaching assets (asset-count stabilization poll; skipped on manual dispatch)
  - `gh release download` → `aws s3 sync` to the R2 bucket under `<tag>/`
  - rewrites `latest.json` asset URLs from github.com to the mirror and uploads it to the bucket root
  - generates a minimal bilingual `index.html` download page
  - **keeps only the latest release** — older `<tag>/` prefixes are pruned (2.8 GB/release fits the 10 GB R2 free tier; R2 egress is free). Prune is skipped when the synced tag isn't the repo's latest, so backfilling an old tag can't delete the current one
  - no-ops gracefully (with a step-summary notice) until the R2 secrets are configured
- **`tauri.conf.json`** — adds `https://dl.catgo-ucsd.org/latest.json` as a fallback updater endpoint (GitHub stays first; Tauri falls through on failure), so installed apps behind the GFW can self-update
- **`readme.md` / `readme.zh.md`** — China-mirror note in the Download section (R2 mirror + Tsinghua PyPI mirror route)

## One-time setup (Cloudflare dashboard, ~5 min)

1. R2 → create bucket `catgo-releases`
2. Bucket → Settings → Custom Domains → `dl.catgo-ucsd.org` (zone already on this account)
3. R2 → Manage API Tokens → Object Read & Write on the bucket → add repo secrets `R2_ACCESS_KEY_ID` / `R2_SECRET_ACCESS_KEY` (`CLOUDFLARE_ACCOUNT_ID` already exists)
4. Optional repo vars `R2_BUCKET` / `R2_PUBLIC_BASE_URL` override the defaults

## Gotchas encoded in the workflow

- Releases published via `GITHUB_TOKEN` don't fire the `release` event (same as pypi-publish) — manual `workflow_dispatch` is the documented fallback and the sync is idempotent
- aws-cli ≥ 2.23 CRC checksums break R2's S3 API → `AWS_REQUEST_CHECKSUM_CALCULATION: when_required`
- Manually-uploaded assets (iOS .ipa) landing after publication → re-dispatch to pick them up

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a910abd9e6a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
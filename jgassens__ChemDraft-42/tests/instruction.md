# Issue

**Title:** GitHub Pages download site

## Description

Adds a download page for the notarized macOS app, styled like jeremiahsrandom.website.

- `site/` — static page (HTML/CSS/one small script). The download button asks the GitHub API for the latest release and links straight to its `.dmg`; with JavaScript off it links to `/releases/latest`.
- `.github/workflows/pages.yml` — deploys `site/` with the official Pages actions on pushes to `main` that touch `site/**`, or by hand.

After merge, Pages must be set to **GitHub Actions** as its source (Settings → Pages). Site URL: https://jgassens.github.io/ChemDraft/

Checked locally: button resolves to `ChemDraft_0.3.3_aarch64.dmg`; no horizontal scroll at 375px.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a16d82fe1d19`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
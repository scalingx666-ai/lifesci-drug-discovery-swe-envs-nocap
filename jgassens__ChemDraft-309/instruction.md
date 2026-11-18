# Issue

**Title:** [1.2] Draft the code signing policy and privacy pages

## Description

Prepares the website pages that Windows code signing through SignPath Foundation needs (#166). The pages go live first so SignPath can review them during the application. The owner's answers are filled in; the master deploys the site after merge.

## What's here
- `site/code-signing.html`: a draft code signing policy. It names the build, review and signing-approval steps. ChemDraft is a one-person project: Jeremiah Gassensmith (https://github.com/jgassens) is committer, reviewer and signing approver, and every release is built by GitHub Actions from this public repository. SignPath signing is described as applied for and pending approval, and the page says plainly that current Windows downloads are not yet Authenticode-signed.
- `site/privacy.html`: a privacy page describing every network connection the app makes and when it makes it, an "In short" summary at the top (files stay on the computer except through the optional AI assistant, what the app connects to, plugin permissions), plus the website's services (Cloudflare hosting, Cloudflare Web Analytics, Adobe Fonts) and the contact address.
- `docs/releasing/code-signing-network-audit.md`: the source-code audit behind the privacy page, one row per outbound connection with the file that makes it.
- `docs/releasing/windows-signing.md`: a pointer to the audit.

The signing workflow itself is already on main behind its flag, so this PR changes no workflow or app code.

## After merging
- The master deploys the site, so SignPath can review the live pages. The policy page keeps saying signing is pending until SignPath accepts.

## Tests
Docs and website only, so there are no new tests. The privacy claims were checked against the code in review.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78f82a1e7157`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Help search engines find chemdraft.ai

## Description

## Summary
- Descriptive page title, matching `og:title`, and Twitter card tags on `site/index.html`
- `site/robots.txt` that allows everything and points at the sitemap (today Cloudflare serves only its comment-only default)
- Sitemap `lastmod` set to 2026-10-28
- README links https://chemdraft.ai near the top
- Second `google-site-verification` tag for the owner's Search Console account (the existing tag belongs to another account), plus an IndexNow key file so changes can be pushed to Bing and other IndexNow engines

The repo's GitHub homepage link was also changed to https://chemdraft.ai (a repo setting, not part of this diff).

## Tests
- `git diff --check`
- Reviewer parsed the HTML and XML, checked robots.txt and the IndexNow key format, and confirmed all files are tracked and inside the `site/` assets directory in `cloudflare/wrangler.jsonc`

## Platforms
Website only; no app code, so macOS and Windows builds are unaffected.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `385079d622ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
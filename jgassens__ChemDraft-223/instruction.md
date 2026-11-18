# Issue

**Title:** Move the website to chemdraft.ai and redirect the GitHub Pages copy

## Description

## Summary
- The product site (`site/`) is now served from **https://chemdraft.ai/** on Cloudflare. Its canonical URL, `og:url`, structured-data `url` and sitemap now name that address.
- GitHub Pages stays up but publishes a new `site-redirect/` folder instead of `site/`. Its `index.html` and an identical `404.html` send every old URL to the same path on chemdraft.ai, keeping the query string and `#` fragment. GitHub serves `404.html` for any path it doesn't know, which is how deep links get redirected. Without JavaScript, visitors fall back to a meta refresh to the homepage.
- The Google site-verification tag is kept on the redirect page so the existing Search Console property stays verified.

No app code changed, so no build stamp bump is needed.

## Review
Kimi (run-20261027-131353-a20fdd) returned no findings after checking the path mapping, open-redirect and injection risk, the HTML, the workflow trigger and artifact paths, and the scope.

## After merge
Cloudflare does not deploy automatically yet. Re-run the Worker deploy so chemdraft.ai picks up the new canonical tags.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfa9f04c4e9b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
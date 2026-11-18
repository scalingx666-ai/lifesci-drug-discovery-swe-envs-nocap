# Issue

**Title:** Give chemdraft.ai a not-found page and commit its deploy config

## Description

## What this changes
- `site/404.html`: a "page not found" page with the site header and a link back home. Its links start at the site root, so it looks right at any depth (`/a/b/c`). It is marked noindex.
- `cloudflare/wrangler.jsonc`: the Cloudflare Worker settings that deploy `site/` to chemdraft.ai and www.chemdraft.ai. `not_found_handling: "404-page"` serves the page above with HTTP status 404. The file holds no token, key or account ID.
- `.gitignore`: ignores the `.wrangler/` folder a deploy leaves behind.

## After merge
Redeploy with `npx wrangler@4 deploy --config cloudflare/wrangler.jsonc`, then check that a missing path returns this page with status 404.

## Platforms
Website only; no app code, so macOS and Windows builds are unaffected.

Reviewed by kimi-k3 (run-20261027-190337-75d36a) and claude-opus (run-20261027-190515-174e3c, run-20261027-190639-b48f80).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4aca7a24bab3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
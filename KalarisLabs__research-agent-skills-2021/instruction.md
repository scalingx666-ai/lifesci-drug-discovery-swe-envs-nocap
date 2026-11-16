# Issue

**Title:** Ci/remove deploy catalog

## Description

## **User description**
## What does this change?

<!-- One or two sentences. Link related issues. -->

## Checklist

- [ ] `uv run tools/validate.py` passes for affected skills
- [ ] `uv run tools/lint_injection.py` reports no new findings
- [ ] `uv run tools/build_catalog.py` run and generated files committed
- [ ] New code has tests, and a bug fix has a regression test (see "Tests" in CONTRIBUTING.md)
- [ ] Facts that change over time (venue limits, APIs) point to official sources
- [ ] No fabricated citations, data or tool capabilities
- [ ] Scripts: stdlib-first, `--help`, exit codes 0/1/2, timeouts, new domains added to `security/allowed-domains.txt`
- [ ] Written by me (not copied from other skill collections); I agree to license it under MIT

<!-- codesmith:footer -->
---
<a href="https://backend.blacksmith.sh/track/enable-autofix?expires=1797183874&installation_model_id=444357&pr_number=2021&ref=codesmith_pr_footer&repository=KalarisLabs%2Fresearch-agent-skills&return_to=https%3A%2F%2Fgithub.com%2FKalarisLabs%2Fresearch-agent-skills%2Fpull%2F2021&signature=78a96edb67489540b34b72cfeda4c55f6af416d7a74651cd50164952f298e87a"><picture><source media="(prefers-color-scheme: dark)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-light.svg"><img alt="Autofix with [code]smith" src="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-dark-3x.png" width="190" height="28"></picture></a>
<sup><a href="https://app.blacksmith.sh/KalarisLabs/codesmith/research-agent-skills/pr/2021?autoLogin=true&ref=codesmith_pr_footer">Open in [code]smith</a> · Need help on this PR? Tag <code>@codesmith-bot</code> with what you need.</sup>

<!-- codesmith:autofix:disabled -->
<!-- /codesmith:footer -->

___

## **CodeAnt-AI Description**
Improve catalog discovery and remove automatic deployments

### What Changed
- Adds search and social-sharing details and structured catalog information to help search engines index the site and show richer previews
- Adds crawl guidance, a sitemap, and an AI-readable listing of 281 skills; visitors without JavaScript see a directory summary and links to the documentation and source
- Catalog changes in this repository no longer automatically deploy to the website

### Impact
`✅ Clearer search and social previews`
`✅ AI-readable directory of 281 skills`
`✅ Catalog changes no longer auto-deploy`
<details><summary><strong>💡 Usage Guide</strong></summary>

### Checking Your Pull Request
Every time you make a pull request, our system automatically looks through it. We check for security issues, mistakes in how you're setting up your infrastructure, and common code problems. We do this to make sure your changes are solid and won't cause any trouble later.

### Talking to CodeAnt AI
Got a question or need a hand with something in your pull request? You can easily get in touch with CodeAnt AI right here. Just type the following in a comment on your pull request, and replace "Your question here" with whatever you want to ask:
<pre>
<code>@codeant-ai ask: Your question here</code>
</pre>
This lets you have a chat with CodeAnt AI about your pull request, making it easier to understand and improve your code.

#### Example
<pre>
<code>@codeant-ai ask: Can you suggest a safer alternative to storing this secret?</code>
</pre>

### Preserve Org Learnings with CodeAnt
You can record team preferences so CodeAnt AI applies them in future reviews. Reply directly to the specific CodeAnt AI suggestion (in the same thread) and replace "Your feedback here" with your input:
<pre>
<code>@codeant-ai: Your feedback here</code>
</pre>
This helps CodeAnt AI learn and adapt to your team's coding style and standards.

#### Example
<pre>
<code>@codeant-ai: Do not flag unused imports.</code>
</pre>

### Retrigger review
Ask CodeAnt AI to review the PR again, by typing:
<pre>
<code>@codeant-ai: review</code>
</pre>

### Check Your Repository Health
To analyze the health of your code repository, visit our dashboard at [https://app.codeant.ai](https://app.codeant.ai). This tool helps you identify potential issues and areas for improvement in your codebase, ensuring your repository maintains high standards of code health.

</details>

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=106149420&amp;sig=5936a4aed3658661e712afc60fa60fdfc5b6ca275c1d44c0f8ade5b5a3f5b1b5"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a><a href="https://app.greptile.com/-/switch-tenant?tenant=kalarislabs&amp;next=%2FKalarisLabs%2Fresearch-agent-skills%2Fpull%2F2021&amp;utm_source=greptile_review&amp;utm_medium=github&amp;utm_campaign=view_in_greptile"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptileDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptile.svg?v=2"><img alt="View in Greptile" src="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptile.svg?v=2" align="right"></picture></a>Confidence Score: 5/5</h2>

<!-- greptile-impact-verdict --> The PR appears safe to merge, with the earlier non-blocking concern about keeping the website directory current.

<h2><a href="https://app.greptile.com/api/ide/codex?prompt=IMPORTANT%3A%20Work%20in%20the%20repository%20%22kalarislabs%2Fresearch-agent-skills%22%20on%20the%20existing%20branch%20%22ci%2Fremove-deploy-catalog%22.%20Checkout%20that%20branch%20%E2%80%94%20do%20NOT%20create%20a%20new%20branch%20or%20open%20a%20new%20PR.%20Push%20your%20changes%20to%20%22ci%2Fremove-deploy-catalog%22.%0A%0A%23%23%23%20Issue%201%0Aweb%2Fllms.txt%3A1-3%0A%60web%2Fllms.txt%60%20adds%20another%20copy%20of%20the%20generated%20skill%20directory%2C%20but%20%60tools%2Fbuild_catalog.py%60%20only%20updates%20the%20root%20and%20documentation%20copies.%20Adding%2C%20removing%2C%20or%20renaming%20skills%20will%20leave%20this%20copy%20unchanged%2C%20and%20%60--check%60%20will%20not%20flag%20it.%20Add%20%60web%2Fllms.txt%60%20to%20the%20builder's%20outputs%20so%20maintainers%20do%20not%20have%20to%20update%20it%20separately.%0A%0A---%0A%0AFor%20each%20issue%20above%2C%20determine%20whether%20it%20is%20valid%20and%20should%20be%20fixed.%20If%20so%2C%20fix%20it%20directly.&expires=1795324945&sig=ee872936b501cf3c65f62e242f664fe0afea89db7e8d55fae4457f40ed810e18&repo=kalarislabs%2Fresearch-agent-skills&pr=2021&platform=github"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/FixAllInCodexDark.svg?v=7"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/FixAllInCodex.svg?v=7"><img alt="Fix All in Codex" src="https://greptile-static-assets.s3.amazonaws.com/badges/FixAllInCodex.svg?v=7" align="right"></picture></a>Findings</h2>

1. <img alt="P2" src="https://greptile-static-assets.s3.amazonaws.com/badges/p2.svg?v=9" align="top">&nbsp;**Website directory falls behind** <a href="">▶</a>

<details><summary>Fix with agent prompt</summary>

`````markdown
### Issue 1
web/llms.txt:1-3
`web/llms.txt` adds another copy of the generated skill directory, but `tools/build_catalog.py` only updates the root and documentation copies. Adding, removing, or renaming skills will leave this copy unchanged, and `--check` will not flag it. Add `web/llms.txt` to the builder's outputs so maintainers do not have to update it separately.

---

For each issue above, determine whether it is valid and should be fixed. If so, fix it directly.
`````

</details>

<h3>Summary</h3>

Adds search and sharing details to the catalog and stops automatic website deployments.
- The catalog page explains itself to search tools and visitors without JavaScript.
- Crawler files point search engines to the catalog homepage.
- AI readers can browse a text index of 281 skills.
- Catalog changes no longer trigger the automatic website deployment.
- The README footer now credits the catalog's creator and maintainer.

<!-- greptile_confidence_score:5 -->

<sub>Reviews (2) · Last reviewed commit:  · [Reviewed by Greptile](https://www.greptile.com/?utm_source=greptile_review&utm_medium=github&utm_campaign=review_public&utm_content=kalarislabs/research-agent-skills)</sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `802bbea44e55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** ci: remove deploy-catalog workflow

## Description

## **User description**
Removes the failing Deploy Skills Catalog workflow and its entry in the PostHog telemetry watch list. The already-deployed site is unaffected but will no longer update.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- codesmith:footer -->
---
<sup><a href="https://app.blacksmith.sh/KalarisLabs/codesmith/research-agent-skills/pr/2017?autoLogin=true&ref=codesmith_pr_footer">Open in [code]smith</a> · Need help on this PR? Tag <code>@codesmith-bot</code> with what you need. Autofix is enabled.</sup>

<!-- codesmith:autofix:enabled -->
<!-- /codesmith:footer -->

___

## **CodeAnt-AI Description**
Stop automatically deploying the skills catalog site

### What Changed
- The skills catalog site remains available at its current deployed version, but catalog and web changes are no longer published automatically.

### Impact
`✅ Current catalog site remains available`
`✅ Catalog changes no longer trigger site updates`
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

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
  * Automated publishing of the skills catalog to GitHub Pages has been removed. Changes to the catalog and related files will no longer trigger deployment through this workflow, and manual deployment from the workflow is no longer available.
  * Catalog deployment completions will no longer trigger the associated telemetry workflow.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=98568251&amp;sig=1969c8a131c0ebbbf68fd96d1b89815a529408e2c8f479ad950192c529e5c832"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a><a href="https://app.greptile.com/-/switch-tenant?tenant=kalarislabs&amp;next=%2FKalarisLabs%2Fresearch-agent-skills%2Fpull%2F2017&amp;utm_source=greptile_review&amp;utm_medium=github&amp;utm_campaign=view_in_greptile"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptileDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptile.svg?v=2"><img alt="View in Greptile" src="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptile.svg?v=2" align="right"></picture></a>Confidence Score: 5/5</h2>

<!-- greptile-impact-verdict --> The PR appears safe to merge with the intended end of catalog updates.

<h3>Summary</h3>

Removes the catalog deployment workflow and its PostHog watch-list entry.
- The skills catalog site no longer gets updates from this repository.

<!-- greptile_confidence_score:5 -->

<sub>Reviews (1) · Last reviewed commit:  · [Reviewed by Greptile](https://www.greptile.com/?utm_source=greptile_review&utm_medium=github&utm_campaign=review_public&utm_content=kalarislabs/research-agent-skills)</sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38caba332f07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
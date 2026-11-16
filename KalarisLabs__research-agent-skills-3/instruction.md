# Issue

**Title:** Link the live research documentation across discovery surfaces

## Description

## **User description**
## Summary
- Point README and generated AI discovery indexes to the live Mintlify Research Agent Skills project.
- Keep the maintainer launch checklist aligned with the live domain.

## Verification
- The project page returns HTTP 200 with a research-specific title.
- The Mintlify sitemap contains 281 research skill pages.
- `uv run tools/build_catalog.py --check`
- `uv run python -m pytest -q tests/test_catalog.py`
- `uv run ruff check tools tests benchmarks`

___

## **CodeAnt-AI Description**
Link all research documentation references to the live Mintlify site

### What Changed
- README, generated AI discovery indexes, and maintainer guidance now link directly to the live research documentation at `docs.kalarislabs.com/research-agent-skills`
- The maintainer launch checklist now treats the Mintlify site and HTTPS domain as active rather than pending setup
- Generated documentation indexes use the live site as their documentation destination

### Impact
`✅ Direct access to live research guides`
`✅ Consistent documentation links across discovery surfaces`
`✅ Clearer maintainer launch instructions`
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

<h2><a href="https://app.greptile.com/api/retrigger?id=72951026"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a>Confidence Score: 5/5</h2>

<!-- greptile-risk -->

No blocking findings are identified in the available review information.

<h3>Summary</h3>

The PR points repository discovery links to the live research documentation. It also redacts identifier values from a validation error and adds a regression test and upstream-import patch.

<!-- greptile_confidence_score:5 -->

<sub>Reviews (2) · Last reviewed commit: </sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07f589d39a46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
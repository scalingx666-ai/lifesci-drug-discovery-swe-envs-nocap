# Issue

**Title:** Skill scanner: filter reviewed baseline findings out of the code-scanning SARIF

## Description

## **User description**
The non-required `skill-scanner` code-scanning check was red on every PR. The job uploaded the scanner's raw SARIF, which ignores `security/skill-scanner-baseline.json`, so all 95 error-level findings that were already reviewed and accepted (see `security/skill-scanner-review-2026-10-01.md`) appeared as new alerts. Examples: `model.eval()` read as Python `eval`, provider API keys read from env vars and sent to that provider, and guardrail skills documenting jailbreak patterns.

`tools/skill_scanner_gate.py` now removes baselined results from `reports/skill-scanner.sarif` in place, before the existing upload step. Findings outside the baseline stay in the SARIF and still fail the required gate. No workflow file changes.

Tests cover key derivation (including the `research-agent-skills` skill name) and filtering that keeps unreviewed findings.

___

## **CodeAnt-AI Description**
**Hide reviewed skill-scanner findings from code scanning**

### What Changed
- Reviewed findings are removed from the scanner report shown in GitHub code scanning.
- Findings that are not in the reviewed baseline remain visible and continue to fail the gate.

### Impact
`✅ Fewer repeated code-scanning alerts`
`✅ Unreviewed findings remain visible`
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

## Summary by CodeRabbit

* **New Features**
  * Skill scanner reports now automatically exclude findings that match accepted baseline entries, while retaining findings that still need review.
  * The adjacent SARIF report is updated with the filtered results, and the gate displays how many findings were kept and removed.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=83962083"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a><a href="https://app.greptile.com/kalarislabs/github/KalarisLabs/research-agent-skills/-/pull/1949"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptileDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptile.svg?v=2"><img alt="View in Greptile" src="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptile.svg?v=2" align="right"></picture></a>Confidence Score: 4/5</h2>

<!-- greptile-risk -->

The PR appears safe to merge, with a non-blocking request to test real scanner output.

<h2><a href="https://app.greptile.com/api/ide/codex?prompt=IMPORTANT%3A%20Work%20in%20the%20repository%20%22kalarislabs%2Fresearch-agent-skills%22%20on%20the%20existing%20branch%20%22ci%2Fscanner-sarif-baseline%22.%20Checkout%20that%20branch%20%E2%80%94%20do%20NOT%20create%20a%20new%20branch%20or%20open%20a%20new%20PR.%20Push%20your%20changes%20to%20%22ci%2Fscanner-sarif-baseline%22.%0A%0A%23%23%23%20Issue%201%0Atests%2Ftest_skill_scanner_gate.py%3A16-17%0AEvery%20SARIF%20result%20is%20built%20with%20%60_result%60%2C%20so%20the%20tests%20assume%20the%20paths%20and%20rule%20names%20that%20%60sarif_key%60%20expects.%20They%20do%20not%20check%20output%20from%20the%20pinned%20scanner.%20If%20that%20format%20differs%2C%20reviewed%20findings%20will%20remain%20in%20code%20scanning%20while%20these%20tests%20pass.%0A%0AAdd%20a%20small%20JSON%2FSARIF%20fixture%20pair%20from%20the%20configured%20scanner.%20Check%20that%20reviewed%20findings%20are%20removed%20and%20unreviewed%20findings%20remain.%0A%0ANote%3A%20If%20this%20suggestion%20doesn't%20match%20your%20team's%20coding%20style%2C%20reply%20to%20this%20and%20let%20me%20know.%20I'll%20remember%20it%20for%20next%20time!%0A%0A---%0A%0AFor%20each%20issue%20above%2C%20determine%20whether%20it%20is%20valid%20and%20should%20be%20fixed.%20If%20so%2C%20fix%20it%20directly.&repo=kalarislabs%2Fresearch-agent-skills&pr=1949&platform=github"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/FixAllInCodexDark.svg?v=7"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/FixAllInCodex.svg?v=7"><img alt="Fix All in Codex" src="https://greptile-static-assets.s3.amazonaws.com/badges/FixAllInCodex.svg?v=7" align="right"></picture></a>Findings</h2>

1. <img alt="P2" src="https://greptile-static-assets.s3.amazonaws.com/badges/p2.svg?v=9" align="top">&nbsp;**Tests assume the scanner format** <a href="">▶</a>

<details><summary>Fix with agent prompt</summary>

`````markdown
### Issue 1
tests/test_skill_scanner_gate.py:16-17
Every SARIF result is built with `_result`, so the tests assume the paths and rule names that `sarif_key` expects. They do not check output from the pinned scanner. If that format differs, reviewed findings will remain in code scanning while these tests pass.

Add a small JSON/SARIF fixture pair from the configured scanner. Check that reviewed findings are removed and unreviewed findings remain.

Note: If this suggestion doesn't match your team's coding style, reply to this and let me know. I'll remember it for next time!

---

For each issue above, determine whether it is valid and should be fixed. If so, fix it directly.
`````

</details>

<h3>Summary</h3>

This PR removes reviewed baseline findings from the sibling SARIF report before GitHub uploads it.
- The skill scanner removes reviewed findings before code scanning uploads them.

<!-- greptile_confidence_score:4 -->

<sub>Reviews (1) · Last reviewed commit:  · [Reviewed by Greptile](https://www.greptile.com/?utm_source=greptile_review&utm_medium=github&utm_campaign=review_public&utm_content=kalarislabs/research-agent-skills)</sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f5a08d6a110`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
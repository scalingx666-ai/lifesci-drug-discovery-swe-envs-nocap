# Issue

**Title:** Redact patient IDs from pacsomatic validation errors

## Description

## **User description**
## Summary
- Stop echoing invalid patient identifiers in pacsomatic validation errors.
- Preserve the imported-skill change in a post-import patch.
- Add a regression test that checks the identifier never reaches stderr.

## Security impact
Addresses the high-severity CodeQL clear-text logging alert for `run_pacsomatic.py` (alert #8).

## Verification
- `uv run python -m pytest -q tests/test_pacsomatic_privacy.py`
- `uv run tools/validate.py --quiet`
- `uv run tools/lint_injection.py`
- `uv run tools/brand_guard.py`
- `uv run tools/build_catalog.py --check`
- `uv run ruff check tools tests benchmarks`
- `git apply --reverse --check third_party/patches/post-0009-redact-patient-id-errors.patch`

___

## **CodeAnt-AI Description**
Prevent patient identifiers from appearing in pacsomatic validation errors

### What Changed
- Validation errors for values containing whitespace now report only the field name and the whitespace requirement
- Added a regression test confirming invalid patient identifiers are excluded from stderr

### Impact
`✅ Patient IDs stay out of validation logs`
`✅ Safer error output for invalid inputs`
`✅ Clearer whitespace validation messages`
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

* **Bug Fixes**
  * Input validation now rejects all whitespace characters, not just spaces.
  * Error messages no longer expose the rejected patient ID.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=72946743"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a>Confidence Score: 5/5</h2>

<!-- greptile-risk -->

Safe to merge based on the changed behavior and completed checks.

What we checked:
- Ran real CLI subprocesses against the previous and changed versions using synthetic invalid patient and sample identifiers; the tests showed every invalid invocation exited with code 1, stdout was empty, and neither output stream contained a synthetic identifier. <a href="https://www.greptile.com/trex"><img alt="T-Rex" src="https://greptile-static-assets.s3.amazonaws.com/trex/trex_green.svg" height="16" align="absmiddle"></a>
- Copied the pre-change script into a temporary workspace, applied the patch, and ran the CLI with a synthetic invalid patient ID to validate the patch effect; the pre-change error contained the ID, while the patched error omitted it. <a href="https://www.greptile.com/trex"><img alt="T-Rex" src="https://greptile-static-assets.s3.amazonaws.com/trex/trex_green.svg" height="16" align="absmiddle"></a>
- Verified the patch sequencing and replay results; the patch check and application succeeded, replay commands exited 0, and the patched CLI run did not expose the ID. <a href="https://www.greptile.com/trex"><img alt="T-Rex" src="https://greptile-static-assets.s3.amazonaws.com/trex/trex_green.svg" height="16" align="absmiddle"></a>

<h3>Summary</h3>

This PR removes identifier values from pacsomatic whitespace-validation errors, adds a regression test, and adds a post-import patch to retain the fix. A user entering an identifier with whitespace now receives an error without that identifier appearing in the error output. No actionable issues were found.

<!-- greptile_confidence_score:5 -->

<sub>Reviews (1) · Last reviewed commit: </sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18c02fe0f186`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
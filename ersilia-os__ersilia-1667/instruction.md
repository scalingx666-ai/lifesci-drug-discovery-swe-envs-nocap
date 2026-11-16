# Issue

**Title:** build(deps): bump GrantBirki/json-yaml-validate from 3.3.0 to 3.3.2

## Description

Bumps [GrantBirki/json-yaml-validate](https://github.com/grantbirki/json-yaml-validate) from 3.3.0 to 3.3.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/grantbirki/json-yaml-validate/releases">GrantBirki/json-yaml-validate's releases</a>.</em></p>
<blockquote>
<h2>v3.3.2</h2>
<h2>What's Changed</h2>
<ul>
<li>TLC and General Improvements by <a href="https://github.com/GrantBirki"><code>@​GrantBirki</code></a> in <a href="">GrantBirki/json-yaml-validate#88</a></li>
<li>More Robust Tests 🧪 - Comprehensive test coverage improvements by <a href="https://github.com/copilot-swe-agent"><code>@​copilot-swe-agent</code></a> in <a href="">GrantBirki/json-yaml-validate#90</a></li>
<li>Fix file duplication issue - YAML validator now skips JSON files when not in yamlAsJson mode by <a href="https://github.com/copilot-swe-agent"><code>@​copilot-swe-agent</code></a> in <a href="">GrantBirki/json-yaml-validate#91</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/copilot-swe-agent"><code>@​copilot-swe-agent</code></a> made their first contribution in <a href="">GrantBirki/json-yaml-validate#90</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/GrantBirki/json-yaml-validate/compare/v3.3.1...v3.3.2">https://github.com/GrantBirki/json-yaml-validate/compare/v3.3.1...v3.3.2</a></p>
<h2>v3.3.1</h2>
<h2>What's Changed</h2>
<ul>
<li>bug: <code>allow_multiple_documents</code> crashes the action in certain JSON parsing cases by <a href="https://github.com/GrantBirki"><code>@​GrantBirki</code></a> in <a href="">GrantBirki/json-yaml-validate#87</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/GrantBirki/json-yaml-validate/compare/v3.3.0...v3.3.1">https://github.com/GrantBirki/json-yaml-validate/compare/v3.3.0...v3.3.1</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>250fa0d</code></a> Merge pull request <a href="">#91</a> from GrantBirki/copilot/fix-70</li>
<li><a href=""><code>2e8494a</code></a> Bundle changes and apply code formatting</li>
<li><a href=""><code>b22ed78</code></a> Fix file duplication issue by adding JSON file skipping logic to YAML validator</li>
<li><a href=""><code>b805108</code></a> Add test case to reproduce issue <a href="">#70</a> - file duplication and extension misrepo...</li>
<li><a href=""><code>b2c4039</code></a> Initial plan for issue</li>
<li><a href=""><code>9413783</code></a> Merge pull request <a href="">#90</a> from GrantBirki/copilot/fix-89</li>
<li><a href=""><code>6d47d5e</code></a> fmt</li>
<li><a href=""><code>3f81094</code></a> Format test files and bundle final changes</li>
<li><a href=""><code>27c6361</code></a> Add comprehensive test coverage improvements - branch coverage increased from...</li>
<li><a href=""><code>db6e397</code></a> Initial plan for issue</li>
<li>Additional commits viewable in <a href="https://github.com/grantbirki/json-yaml-validate/compare/947ae8ac60c83cf78e4e00b3170ff8bee61f5248...250fa0dc7d7f4a888b24dc2a6b2ff589753fba70">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=GrantBirki/json-yaml-validate&package-manager=github_actions&previous-version=3.3.0&new-version=3.3.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

You can trigger a rebase of this PR by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot squash and merge` will squash and merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge and block automerging
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot close` will close this PR and stop Dependabot recreating it. You can achieve the same result by closing it manually
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

> **Note**
> Automatic rebases have been disabled on this pull request as it has been open for over 30 days.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3f2f00063ae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
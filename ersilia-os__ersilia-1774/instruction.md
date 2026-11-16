# Issue

**Title:** Bump GrantBirki/json-yaml-validate from 3.3.2 to 4.0.0

## Description

Bumps [GrantBirki/json-yaml-validate](https://github.com/grantbirki/json-yaml-validate) from 3.3.2 to 4.0.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/grantbirki/json-yaml-validate/releases">GrantBirki/json-yaml-validate's releases</a>.</em></p>
<blockquote>
<h2>v4.0.0</h2>
<h2>What's Changed</h2>
<p>🚨 <strong>Breaking change notice</strong>: The vast majority of users should be able to seamlessly upgrade to <code>v4</code> without needing to make any changes at all. This is mainly just a <em>major</em> version release due to the fact that this Action is moving to a default runtime of <code>node24</code> which requires up-to-date Actions runner versions.</p>
<ul>
<li>Bump brace-expansion from 1.1.11 to 1.1.12 in the npm_and_yarn group across 1 directory by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">GrantBirki/json-yaml-validate#92</a></li>
<li>update all internal node deps by <a href="https://github.com/GrantBirki"><code>@​GrantBirki</code></a> in <a href="">GrantBirki/json-yaml-validate#93</a></li>
<li>upgrade to <code>node24</code> by <a href="https://github.com/GrantBirki"><code>@​GrantBirki</code></a> in <a href="">GrantBirki/json-yaml-validate#94</a></li>
<li>Repo/actions dependency updates by <a href="https://github.com/GrantBirki"><code>@​GrantBirki</code></a> in <a href="">GrantBirki/json-yaml-validate#95</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/GrantBirki/json-yaml-validate/compare/v3.3.2...v4.0.0">https://github.com/GrantBirki/json-yaml-validate/compare/v3.3.2...v4.0.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9bbaa84</code></a> Merge pull request <a href="">#95</a> from GrantBirki/repo-updates</li>
<li><a href=""><code>95b5e1c</code></a> upgrade actions/setup-node from v4 to v6 in workflow files and bump upload ar...</li>
<li><a href=""><code>6023349</code></a> upgrade actions/checkout from v4 to v5 across workflow files and README</li>
<li><a href=""><code>3de07f3</code></a> add a dependabot config</li>
<li><a href=""><code>38f2011</code></a> Merge pull request <a href="">#94</a> from GrantBirki/node24</li>
<li><a href=""><code>d6d7a6e</code></a> upgrade to <code>node24</code></li>
<li><a href=""><code>e1bd53e</code></a> Merge pull request <a href="">#93</a> from GrantBirki/npm-updates</li>
<li><a href=""><code>bd408c3</code></a> use <code>picomatch</code> with <code>withGlobFunction()</code></li>
<li><a href=""><code>aff2b85</code></a> update all internal node deps and bundle</li>
<li><a href=""><code>35c97c6</code></a> Merge pull request <a href="">#92</a> from GrantBirki/dependabot/npm_and_yarn/npm_and_yarn-6...</li>
<li>Additional commits viewable in <a href="https://github.com/grantbirki/json-yaml-validate/compare/250fa0dc7d7f4a888b24dc2a6b2ff589753fba70...9bbaa8474e3af4e91f25eda8ac194fdc30564d96">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=GrantBirki/json-yaml-validate&package-manager=github_actions&previous-version=3.3.2&new-version=4.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

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

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d59a02a84708`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
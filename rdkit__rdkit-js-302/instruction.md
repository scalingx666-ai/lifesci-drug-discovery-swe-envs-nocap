# Issue

**Title:** Bump web-vitals from 3.1.0 to 3.1.1

## Description

Bumps [web-vitals](https://github.com/GoogleChrome/web-vitals) from 3.1.0 to 3.1.1.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/GoogleChrome/web-vitals/blob/main/CHANGELOG.md">web-vitals's changelog</a>.</em></p>
<blockquote>
<h3>v3.1.1 (2023-01-10)</h3>
<ul>
<li>Defer CLS logic until after <code>onFCP()</code> callback (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/297">#297</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9c095c5</code></a> Release v3.1.1</li>
<li><a href=""><code>a8c4371</code></a> Update CHANGELOG</li>
<li><a href=""><code>e5e4a6d</code></a> Defer CLS logic until after onFCP callback (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/issues/297">#297</a>)</li>
<li><a href=""><code>cd560dc</code></a> Add prettier (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/issues/288">#288</a>)</li>
<li>See full diff in <a href="https://github.com/GoogleChrome/web-vitals/compare/v3.1.0...v3.1.1">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~tunetheweb">tunetheweb</a>, a new releaser for web-vitals since your current version.</p>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=web-vitals&package-manager=npm_and_yarn&previous-version=3.1.0&new-version=3.1.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbe2c04b17dc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
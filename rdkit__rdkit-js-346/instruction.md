# Issue

**Title:** Bump vite from 3.2.4 to 3.2.7

## Description

Bumps [vite](https://github.com/vitejs/vite/tree/HEAD/packages/vite) from 3.2.4 to 3.2.7.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/blob/v3.2.7/packages/vite/CHANGELOG.md">vite's changelog</a>.</em></p>
<blockquote>
<h2><!-- raw HTML omitted -->3.2.7 (2023-05-26)<!-- raw HTML omitted --></h2>
<ul>
<li>fix: port <a href="">#13348</a> to v3, fs.deny with leading double slash (<a href="">#13349</a>) (<a href="">0574f80</a>), closes <a href="">#13348</a> <a href="">#13349</a></li>
</ul>
<h2><!-- raw HTML omitted -->3.2.6 (2023-04-18)<!-- raw HTML omitted --></h2>
<ul>
<li>fix: escape msg in render restricted error html, backport (<a href="">#12889</a>) (<a href="">#12892</a>) (<a href="">b48ac2a</a>), closes <a href="">#12889</a> <a href="">#12892</a></li>
</ul>
<h2><!-- raw HTML omitted -->3.2.5 (2022-12-05)<!-- raw HTML omitted --></h2>
<ul>
<li>chore: cherry pick more v4 bug fixes to v3 (<a href="">#11189</a>) (<a href="">eba9b42</a>), closes <a href="">#11189</a> <a href="">#10949</a> <a href="">#11056</a> <a href="">#8663</a> <a href="">#10958</a> <a href="">#11120</a> <a href="">#11122</a> <a href="">#11123</a> <a href="">#11132</a></li>
<li>chore: cherry pick v4 bug fix to v3 (<a href="">#11110</a>) (<a href="">c93a526</a>), closes <a href="">#11110</a> <a href="">#10941</a> <a href="">#10987</a> <a href="">#10985</a> <a href="">#11067</a></li>
<li>fix: relocated logger to respect config. (<a href="">#10787</a>) (<a href="">#10967</a>) (<a href="">bc3b5a9</a>), closes <a href="">#10787</a> <a href="">#10967</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>494f36b</code></a> release: v3.2.7</li>
<li><a href=""><code>0574f80</code></a> fix: port <a href="">#13348</a> to v3, fs.deny with leading double slash (<a href="">#13349</a>)</li>
<li><a href=""><code>f494760</code></a> release: v3.2.6</li>
<li><a href=""><code>b48ac2a</code></a> fix: escape msg in render restricted error html, backport (<a href="">#12889</a>) (<a href="">#12892</a>)</li>
<li><a href=""><code>77ee19b</code></a> release: v3.2.5</li>
<li><a href=""><code>eba9b42</code></a> chore: cherry pick more v4 bug fixes to v3 (<a href="">#11189</a>)</li>
<li><a href=""><code>c93a526</code></a> chore: cherry pick v4 bug fix to v3 (<a href="">#11110</a>)</li>
<li><a href=""><code>bc3b5a9</code></a> fix: relocated logger to respect config. (<a href="">#10787</a>) (<a href="">#10967</a>)</li>
<li>See full diff in <a href="https://github.com/vitejs/vite/commits/v3.2.7/packages/vite">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vite&package-manager=npm_and_yarn&previous-version=3.2.4&new-version=3.2.7)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/rdkit/rdkit-js/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7c609a932b35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
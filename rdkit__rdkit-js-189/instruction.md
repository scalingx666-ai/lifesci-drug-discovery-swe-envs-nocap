# Issue

**Title:** Bump vue-tsc from 0.40.9 to 0.40.10

## Description

Bumps [vue-tsc](https://github.com/johnsoncodehk/volar/tree/HEAD/packages/vue-tsc) from 0.40.9 to 0.40.10.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/johnsoncodehk/volar/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>0.40.10 (2022/9/7)</h2>
<ul>
<li>feat: improve &quot;Format Selection&quot; for html content</li>
<li>feat: uniquely scope attribute shorthands (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1812">#1812</a>)</li>
<li>feat: add server name, version infos to LSP initialize response</li>
<li>fix: &quot;Format Selection&quot; should not format whole language block (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1833">#1833</a>)</li>
<li>fix: formatting break document content randomly (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1827">#1827</a>) (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1832">#1832</a>)</li>
<li>fix: pug syntax highlighting confuses element id with interpolation (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1826">#1826</a>)</li>
<li>fix: don't cache IDE settings if IDE do not support config change notification</li>
</ul>
<h3>Our Sponsors</h3>
<!-- raw HTML omitted -->
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c1f4d3a</code></a> v0.40.10</li>
<li>See full diff in <a href="https://github.com/johnsoncodehk/volar/commits/v0.40.10/packages/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=0.40.9&new-version=0.40.10)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `636907cba5c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
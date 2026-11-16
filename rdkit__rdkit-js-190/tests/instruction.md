# Issue

**Title:** Bump vue-tsc from 0.40.10 to 0.40.13

## Description

Bumps [vue-tsc](https://github.com/johnsoncodehk/volar/tree/HEAD/packages/vue-tsc) from 0.40.10 to 0.40.13.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/johnsoncodehk/volar/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>0.40.13 (2022/9/8)</h2>
<ul>
<li>fix: cycle reactive reference lead to memory leak</li>
</ul>
<h2>0.40.12 (2022/9/8)</h2>
<ul>
<li>perf: fix incremental template compile not working</li>
<li>perf: cache path resolve result on <code>getScriptVersion</code></li>
<li>perf: faster code mapping range transform</li>
</ul>
<h3>Our Sponsors</h3>
<!-- raw HTML omitted -->
<h2>0.40.11 (2022/9/8)</h2>
<ul>
<li>feat: support for typescript class/object literal method completions (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1835">#1835</a>)</li>
<li>fix: langauge server crash if client did not support <code>onDidChangeWorkspaceFolders</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1834">#1834</a>)</li>
<li>fix: &quot;Format Selection&quot; embedded range incorrect with initialIndentBracket</li>
<li>fix: formatting break document with <code>editor.formatOnPaste</code> enabled (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1840">#1840</a>) (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1841">#1841</a>) (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1842">#1842</a>) (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1843">#1843</a>) (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1835">#1835</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>baeeddd</code></a> v0.40.13</li>
<li><a href=""><code>66a0ada</code></a> v0.40.12</li>
<li><a href=""><code>42c62e2</code></a> v0.40.11</li>
<li>See full diff in <a href="https://github.com/johnsoncodehk/volar/commits/v0.40.13/packages/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=0.40.10&new-version=0.40.13)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68b68c50b00e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Bump vue-tsc from 0.40.7 to 0.40.9

## Description

Bumps [vue-tsc](https://github.com/johnsoncodehk/volar/tree/HEAD/packages/vue-tsc) from 0.40.7 to 0.40.9.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/johnsoncodehk/volar/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>0.40.9 (2022/9/6)</h2>
<ul>
<li>feat: improve vue document formatting</li>
<li>fix: script format loss indent (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1823">#1823</a>)</li>
</ul>
<h2>0.40.8 (2022/9/6)</h2>
<ul>
<li>feat: add <code>volar.format.initialIndent</code> option for format <code>&lt;style&gt;</code>, <code>&lt;script&gt;</code> with initial indent (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1806">#1806</a>)</li>
<li>perf: cache <code>ts.ScriptSnapshot.fromString</code> result on formatting</li>
<li>fix: volar.config.js not working since v0.40.7 (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1819">#1819</a>)</li>
<li>fix: should not incremental update if SFC parse failed (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1807#issuecomment-1236857296">johnsoncodehk/volar#1807</a>)</li>
</ul>
<h3>Our Sponsors</h3>
<!-- raw HTML omitted -->
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9374238</code></a> v0.40.9</li>
<li><a href=""><code>27a16ee</code></a> v0.40.8</li>
<li>See full diff in <a href="https://github.com/johnsoncodehk/volar/commits/v0.40.9/packages/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=0.40.7&new-version=0.40.9)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13d46a918dbe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
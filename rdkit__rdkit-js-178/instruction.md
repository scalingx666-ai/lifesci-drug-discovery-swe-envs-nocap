# Issue

**Title:** Bump vue-tsc from 0.40.4 to 0.40.5

## Description

Bumps [vue-tsc](https://github.com/johnsoncodehk/volar/tree/HEAD/packages/vue-tsc) from 0.40.4 to 0.40.5.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/johnsoncodehk/volar/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>0.40.5 (2022/8/31)</h2>
<ul>
<li>feat: suppor add or switch workspaces without restart server (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1574">#1574</a>)</li>
<li>fix: sfc offset incremental update broken when input at block start</li>
<li>fix: document incremental update break document content on Sublime LSP (<a href="https://github-redirect.dependabot.com/sublimelsp/LSP-volar/issues/120">sublimelsp/LSP-volar#120</a>)</li>
<li>fix: unexpected prop types behavior with <code>compilerOptions.exactOptionalPropertyTypes</code> (<a href="https://github-redirect.dependabot.com/vuejs/core/issues/6532">vuejs/core#6532</a>)</li>
<li>fix: false positive error on <code>&lt;input typeof=&quot;radio&quot; value=&quot;...&quot;&gt;</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1775">#1775</a>)</li>
<li>fix: false positive style attribute inconsistent string type error (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1781">#1781</a>)</li>
<li>fix: langauge server broken with <code>outDir</code> + <code>rootDir</code> + <code>composite/incremental</code> tsconfig options (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1782">#1782</a>)</li>
<li>fix: json format should not trim first / end new line</li>
<li>fix: interpolation format adding redundant spaces (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1784">#1784</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>fb30bfc</code></a> v0.40.5</li>
<li>See full diff in <a href="https://github.com/johnsoncodehk/volar/commits/v0.40.5/packages/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=0.40.4&new-version=0.40.5)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d97869a3c375`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
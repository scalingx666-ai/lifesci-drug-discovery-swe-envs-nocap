# Issue

**Title:** Bump tslib from 2.4.1 to 2.5.0

## Description

Bumps [tslib](https://github.com/Microsoft/tslib) from 2.4.1 to 2.5.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/Microsoft/tslib/releases">tslib's releases</a>.</em></p>
<blockquote>
<h2>tslib 2.5.0</h2>
<h2>What's New</h2>
<ul>
<li>Fix asyncDelegator reporting done too early by <a href="https://github.com/apendua"><code>@​apendua</code></a> in <a href="https://github-redirect.dependabot.com/microsoft/tslib/pull/187">microsoft/tslib#187</a></li>
<li>Add support for TypeScript 5.0's <code>__esDecorate</code> and related helpers by <a href="https://github.com/rbuckton"><code>@​rbuckton</code></a> in <a href="https://github-redirect.dependabot.com/microsoft/tslib/pull/193">microsoft/tslib#193</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/microsoft/tslib/compare/2.4.1...2.5.0">https://github.com/microsoft/tslib/compare/2.4.1...2.5.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e388a23</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/Microsoft/tslib/issues/194">#194</a> from microsoft/bump-version-2.5</li>
<li><a href=""><code>b68d573</code></a> Bump package version to 2.5.0</li>
<li><a href=""><code>62c5322</code></a> Add support for __esDecorate and related helpers (<a href="https://github-redirect.dependabot.com/Microsoft/tslib/issues/193">#193</a>)</li>
<li><a href=""><code>3bdc002</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/Microsoft/tslib/issues/188">#188</a> from microsoft/add-codeql</li>
<li><a href=""><code>697f430</code></a> try paths: .</li>
<li><a href=""><code>63319af</code></a> add codeql</li>
<li><a href=""><code>a549d39</code></a> Fix asyncDelegator reporting done too early (<a href="https://github-redirect.dependabot.com/Microsoft/tslib/issues/187">#187</a>)</li>
<li>See full diff in <a href="https://github.com/Microsoft/tslib/compare/2.4.1...2.5.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=tslib&package-manager=npm_and_yarn&previous-version=2.4.1&new-version=2.5.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `693961fbd6f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
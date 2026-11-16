# Issue

**Title:** Bump typedoc from 0.23.14 to 0.23.15

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.23.14 to 0.23.15.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.23.15</h2>
<h3>Features</h3>
<ul>
<li>TypeDoc will now treat <code>@typedef {import(&quot;foo&quot;).Bar&lt;Z&gt;} Baz</code> type declarations which forward type parameters to the imported
symbol as re-exports of that symbol, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2044">#2044</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>TypeDoc will now prefer comments on variable declarations over signature comments, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2042">#2042</a>.</li>
<li>Fixed double rendering of &quot;Type Parameters&quot; header, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2054">#2054</a>.</li>
<li>Fixed double rendering of &quot;Hierarchy&quot; header, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2053">#2053</a>.</li>
<li>Removed unused <code>widgets.png</code> and <code>widgets@2x.png</code> files from generated assets folder.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.23.15 (2022-09-18)</h2>
<h3>Features</h3>
<ul>
<li>TypeDoc will now treat <code>@typedef {import(&quot;foo&quot;).Bar&lt;Z&gt;} Baz</code> type declarations which forward type parameters to the imported
symbol as re-exports of that symbol, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2044">#2044</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>TypeDoc will now prefer comments on variable declarations over signature comments, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2042">#2042</a>.</li>
<li>Fixed double rendering of &quot;Type Parameters&quot; header, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2054">#2054</a>.</li>
<li>Fixed double rendering of &quot;Hierarchy&quot; header, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2053">#2053</a>.</li>
<li>Removed unused <code>widgets.png</code> and <code>widgets@2x.png</code> files from generated assets folder.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>97de3e3</code></a> Update changelog for release</li>
<li><a href=""><code>e6d6bcf</code></a> Release 0.23.15</li>
<li><a href=""><code>5478293</code></a> Fix double render of Hierarchy header</li>
<li><a href=""><code>42fba94</code></a> Fix double Type Parameters heading render</li>
<li><a href=""><code>1adaf60</code></a> Remove unused files</li>
<li><a href=""><code>b8de8bf</code></a> Prefer variable comments</li>
<li><a href=""><code>041c35b</code></a> Remove circular dependency</li>
<li><a href=""><code>0c1b9c8</code></a> Detect <code>@typedef</code> re-exports</li>
<li>See full diff in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.23.14...v0.23.15">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.23.14&new-version=0.23.15)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84d60ef4d5c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
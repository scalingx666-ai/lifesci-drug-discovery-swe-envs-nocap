# Issue

**Title:** Bump typedoc from 0.24.6 to 0.24.7

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.24.6 to 0.24.7.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.24.7</h2>
<h3>Features</h3>
<ul>
<li>TypeDoc will now allow conversion without any entry points to support &quot;readme only&quot; packages, <a href="">#2264</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Category children are now sorted according to the <code>sort</code> option, <a href="">#2272</a>.</li>
<li>Inline tags no longer require a space after the tag name to be parsed as a tag, <a href="">#2273</a>.</li>
<li>Fixed module/namespace links in navigation when viewed in Safari, <a href="">#2275</a>.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.24.7 (2023-05-08)</h2>
<h3>Features</h3>
<ul>
<li>TypeDoc will now allow conversion without any entry points to support &quot;readme only&quot; packages, <a href="">#2264</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Category children are now sorted according to the <code>sort</code> option, <a href="">#2272</a>.</li>
<li>Inline tags no longer require a space after the tag name to be parsed as a tag, <a href="">#2273</a>.</li>
<li>Fixed module/namespace links in navigation when viewed in Safari, <a href="">#2275</a>.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c5d1ec5</code></a> Update changelog for release</li>
<li><a href=""><code>0756981</code></a> Bump version to 0.24.7</li>
<li><a href=""><code>a4028d7</code></a> Update changelog</li>
<li><a href=""><code>56abed5</code></a> Fix navigation on Safari, hopefully fixes <a href="">#2275</a></li>
<li><a href=""><code>515e8b7</code></a> Fix inline tag parsing</li>
<li><a href=""><code>26df2ac</code></a> Support readme only packages</li>
<li><a href=""><code>eb18150</code></a> Fix <a href="">#2272</a> category sort order</li>
<li><a href=""><code>5d38df1</code></a> Add a test for <a href="">#2270</a></li>
<li>See full diff in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.24.6...v0.24.7">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.24.6&new-version=0.24.7)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c89c0b46fe8c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
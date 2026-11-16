# Issue

**Title:** Bump typedoc from 0.23.17 to 0.23.18

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.23.17 to 0.23.18.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.23.18</h2>
<h3>Features</h3>
<ul>
<li>Improved error reporting when failing to find entry points, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2080">#2080</a>, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2082">#2082</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Constructor parameter-properties will now use the <code>@param</code> comment for the parameter if available, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/1261">#1261</a>.</li>
<li>Fixed display of object types containing methods, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/1788">#1788</a>.</li>
<li>Fixed conversion of intrinsic string mapping types when converting without a type node, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2079">#2079</a>.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.23.18 (2022-10-23)</h2>
<h3>Features</h3>
<ul>
<li>Improved error reporting when failing to find entry points, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2080">#2080</a>, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2082">#2082</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Constructor parameter-properties will now use the <code>@param</code> comment for the parameter if available, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/1261">#1261</a>.</li>
<li>Fixed display of object types containing methods, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/1788">#1788</a>.</li>
<li>Fixed conversion of intrinsic string mapping types when converting without a type node, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2079">#2079</a>.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e3d2801</code></a> Update changelog for release</li>
<li><a href=""><code>f3dda4b</code></a> Bump version to 0.23.18</li>
<li><a href=""><code>cbe6e16</code></a> Add warning for missing tsconfig</li>
<li><a href=""><code>d1f8927</code></a> Improve error message when failing to find entry point</li>
<li><a href=""><code>9671e18</code></a> Fix comments for constructor properties</li>
<li><a href=""><code>1ebddd6</code></a> Fix object types with methods</li>
<li><a href=""><code>7072f73</code></a> Adjust unsupported warning</li>
<li><a href=""><code>c7c48f2</code></a> Fix <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2079">#2079</a></li>
<li>See full diff in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.23.17...v0.23.18">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.23.17&new-version=0.23.18)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `471ffaf9aa97`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
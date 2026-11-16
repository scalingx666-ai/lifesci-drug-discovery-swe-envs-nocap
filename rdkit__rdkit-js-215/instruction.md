# Issue

**Title:** Bump typedoc from 0.23.16 to 0.23.17

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.23.16 to 0.23.17.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.23.17</h2>
<h3>Features</h3>
<ul>
<li>Added <code>titleLink</code>, <code>navigationLinks</code> and <code>sidebarLinks</code> options to add additional links to the rendered output, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/1830">#1830</a>.</li>
<li>Added <code>sourceLinkTemplate</code> option to allow more flexible specification of remote urls.
Deprecated now redundant <code>gitRevision</code> detection starting with <code>https?://</code> introduced in v0.23.16, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2068">#2068</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/futurGH"><code>@​futurGH</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.23.17 (2022-10-18)</h2>
<h3>Features</h3>
<ul>
<li>Added <code>titleLink</code>, <code>navigationLinks</code> and <code>sidebarLinks</code> options to add additional links to the rendered output, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/1830">#1830</a>.</li>
<li>Added <code>sourceLinkTemplate</code> option to allow more flexible specification of remote urls.
Deprecated now redundant <code>gitRevision</code> detection starting with <code>https?://</code> introduced in v0.23.16, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2068">#2068</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/futurGH"><code>@​futurGH</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c59b8bf</code></a> Update changelog for release</li>
<li><a href=""><code>e2814dc</code></a> Bump version</li>
<li><a href=""><code>4c81b3d</code></a> Add sourceLinkTemplate option</li>
<li><a href=""><code>2eaa476</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2078">#2078</a> from futurGH/configurable-links</li>
<li><a href=""><code>c0b4420</code></a> lint</li>
<li><a href=""><code>3badd68</code></a> Tests</li>
<li><a href=""><code>767b9b1</code></a> Add navigationLinks and sidebarLinks to the example</li>
<li><a href=""><code>1d5da81</code></a> Add support for <code>titleLink</code>, <code>navigationLinks</code>, and <code>sidebarLinks</code> options</li>
<li>See full diff in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.23.16...v0.23.17">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.23.16&new-version=0.23.17)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `724c922caf16`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
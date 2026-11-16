# Issue

**Title:** Bump pat-s/always-upload-cache from 2 to 3

## Description

Bumps [pat-s/always-upload-cache](https://github.com/pat-s/always-upload-cache) from 2 to 3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pat-s/always-upload-cache/releases">pat-s/always-upload-cache's releases</a>.</em></p>
<blockquote>
<h2>v2.1.5</h2>
<p>Merge upstream changes from actions/cache.</p>
<h2>v2.1.3</h2>
<p>Merge upstream changes from actions/cache.</p>
<h2>v2.1.0</h2>
<p>Merge upstream changes from actions/cache.</p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pat-s/always-upload-cache/blob/main/RELEASES.md">pat-s/always-upload-cache's changelog</a>.</em></p>
<blockquote>
<h1>Releases</h1>
<h3>3.0.0</h3>
<ul>
<li>Updated minimum runner version support from node 12 -&gt; node 16</li>
</ul>
<h3>3.0.1</h3>
<ul>
<li>Added support for caching from GHES 3.5.</li>
<li>Fixed download issue for files &gt; 2GB during restore.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>af4dd99</code></a> Merge branch 'main' of github.com:actions/cache</li>
<li><a href=""><code>f63a711</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pat-s/always-upload-cache/issues/781">#781</a> from actions/t-dedah/cacheSize</li>
<li><a href=""><code>770a27c</code></a> Update licenses</li>
<li><a href=""><code>c2131ab</code></a> New build</li>
<li><a href=""><code>5751604</code></a> Updated <code>@​actions/cache</code> to 2.0.1</li>
<li><a href=""><code>136d96b</code></a> Enabling actions/cache for GHES based on presence of AC service (<a href="https://github-redirect.dependabot.com/pat-s/always-upload-cache/issues/774">#774</a>)</li>
<li><a href=""><code>7d4f40b</code></a> Bumping up the version to fix download issue for files &gt; 2 GB. (<a href="https://github-redirect.dependabot.com/pat-s/always-upload-cache/issues/775">#775</a>)</li>
<li><a href=""><code>2d8d0d1</code></a> Updated what's new. (<a href="https://github-redirect.dependabot.com/pat-s/always-upload-cache/issues/771">#771</a>)</li>
<li><a href=""><code>7799d86</code></a> Updated the usage and docs to the major version release. (<a href="https://github-redirect.dependabot.com/pat-s/always-upload-cache/issues/770">#770</a>)</li>
<li><a href=""><code>4b0cf6c</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/pat-s/always-upload-cache/issues/769">#769</a> from actions/users/ashwinsangem/bump_major_version</li>
<li>Additional commits viewable in <a href="https://github.com/pat-s/always-upload-cache/compare/v2...v3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pat-s/always-upload-cache&package-manager=github_actions&previous-version=2&new-version=3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99db0af2a2ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
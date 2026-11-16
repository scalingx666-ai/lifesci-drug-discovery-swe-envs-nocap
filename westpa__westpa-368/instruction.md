# Issue

**Title:** Bump actions/download-artifact from 3 to 4

## Description

Bumps [actions/download-artifact](https://github.com/actions/download-artifact) from 3 to 4.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/download-artifact/releases">actions/download-artifact's releases</a>.</em></p>
<blockquote>
<h2>v4.0.0</h2>
<h2>What's Changed</h2>
<p>The release of upload-artifact@v4 and download-artifact@v4 are major changes to the backend architecture of Artifacts. They have numerous performance and behavioral improvements.</p>
<p>For more information, see the <a href="https://github.com/actions/toolkit/tree/main/packages/artifact"><code>@​actions/artifact</code></a> documentation.</p>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/bflad"><code>@​bflad</code></a> made their first contribution in <a href="">actions/download-artifact#194</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/download-artifact/compare/v3...v4.0.0">https://github.com/actions/download-artifact/compare/v3...v4.0.0</a></p>
<h2>v3.0.2</h2>
<ul>
<li>Bump <code>@actions/artifact</code> to v1.1.1 - <a href="">actions/download-artifact#195</a></li>
<li>Fixed a bug in Node16 where if an HTTP download finished too quickly (&lt;1ms, e.g. when it's mocked) we attempt to delete a temp file that has not been created yet <a href="h">actions/toolkit#1278</a></li>
</ul>
<h2>v3.0.1</h2>
<ul>
<li><a href="">Bump <code>@​actions/core</code> to 1.10.0</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f44cd7b</code></a> Merge pull request <a href="">#259</a> from actions/robherley/glob-downloads</li>
<li><a href=""><code>3181fe8</code></a> add some migration docs</li>
<li><a href=""><code>aaaac7b</code></a> licensed cache</li>
<li><a href=""><code>7c9182f</code></a> update readme</li>
<li><a href=""><code>b94e701</code></a> licensed cache</li>
<li><a href=""><code>0b55470</code></a> add test case for globbed downloads to same directory</li>
<li><a href=""><code>0b51c2e</code></a> update prettier/eslint versions</li>
<li><a href=""><code>c4c6db7</code></a> support globbing artifact list &amp; merging download directory</li>
<li><a href=""><code>1bd0606</code></a> Merge pull request <a href="">#252</a> from stchr/patch-1</li>
<li><a href=""><code>eff4d42</code></a> fix default for run-id</li>
<li>Additional commits viewable in <a href="https://github.com/actions/download-artifact/compare/v3...v4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=actions/download-artifact&package-manager=github_actions&previous-version=3&new-version=4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37a4ceff3827`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
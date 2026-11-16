# Issue

**Title:** ci(deps): bump softprops/action-gh-release from 1 to 2

## Description

Bumps [softprops/action-gh-release](https://github.com/softprops/action-gh-release) from 1 to 2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/softprops/action-gh-release/releases">softprops/action-gh-release's releases</a>.</em></p>
<blockquote>
<h2>v2.0.0</h2>
<ul>
<li>update actions.yml declaration to node20 to address warnings</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/softprops/action-gh-release/blob/master/CHANGELOG.md">softprops/action-gh-release's changelog</a>.</em></p>
<blockquote>
<h2>0.1.12</h2>
<ul>
<li>fix bug leading to empty strings subsituted for inputs users don't provide breaking api calls <a href="">#144</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>72f2c25</code></a> release 2.3.2</li>
<li><a href=""><code>552dc55</code></a> fix: revert <code>fs:readableWebStream</code> change (<a href="">#632</a>)</li>
<li><a href=""><code>f3cad8b</code></a> release 2.3.1</li>
<li><a href=""><code>07a2257</code></a> fix: fix file closing issue (<a href="">#629</a>)</li>
<li><a href=""><code>d5382d3</code></a> release 2.3.0</li>
<li><a href=""><code>a0e2122</code></a> feat: migrate from jest to vitest (<a href="">#626</a>)</li>
<li><a href=""><code>8836085</code></a> chore: replace <code>mime</code> with <code>mime-types</code> (<a href="">#624</a>)</li>
<li><a href=""><code>8646335</code></a> chore: bump node to 20.19.2</li>
<li><a href=""><code>46b2847</code></a> chore(deps): bump the npm group across 1 directory with 5 updates (<a href="">#623</a>)</li>
<li><a href=""><code>37fd9d0</code></a> chore(deps): bump undici from 5.28.5 to 5.29.0 (<a href="">#621</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/softprops/action-gh-release/compare/v1...v2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=softprops/action-gh-release&package-manager=github_actions&previous-version=1&new-version=2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c993282793e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
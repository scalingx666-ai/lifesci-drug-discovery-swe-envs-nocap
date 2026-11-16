# Issue

**Title:** Bump vite from 3.2.3 to 3.2.4

## Description

Bumps [vite](https://github.com/vitejs/vite/tree/HEAD/packages/vite) from 3.2.3 to 3.2.4.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/blob/v3.2.4/packages/vite/CHANGELOG.md">vite's changelog</a>.</em></p>
<blockquote>
<h2><!-- raw HTML omitted -->3.2.4 (2022-11-15)<!-- raw HTML omitted --></h2>
<ul>
<li>fix: prevent cache on optional package resolve (v3) (<a href="">#10812</a>) (<a href="">#10845</a>) (<a href="">3ba45b9</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10812">#10812</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10845">#10845</a></li>
<li>fix(ssr): skip optional peer dep resolve (v3) (<a href="">#10593</a>) (<a href="">#10931</a>) (<a href="">7f59dcf</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10593">#10593</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10931">#10931</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10593">#10593</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>970538c</code></a> release: v3.2.4</li>
<li><a href=""><code>7f59dcf</code></a> fix(ssr): skip optional peer dep resolve (v3) (<a href="">#10593</a>) (<a href="">#10931</a>)</li>
<li><a href=""><code>3ba45b9</code></a> fix: prevent cache on optional package resolve (v3) (<a href="">#10812</a>) (<a href="">#10845</a>)</li>
<li>See full diff in <a href="https://github.com/vitejs/vite/commits/v3.2.4/packages/vite">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vite&package-manager=npm_and_yarn&previous-version=3.2.3&new-version=3.2.4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9cf03c14b28e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
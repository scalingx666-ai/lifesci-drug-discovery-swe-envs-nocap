# Issue

**Title:** Bump vite from 3.1.2 to 3.1.3

## Description

Bumps [vite](https://github.com/vitejs/vite/tree/HEAD/packages/vite) from 3.1.2 to 3.1.3.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/blob/main/packages/vite/CHANGELOG.md">vite's changelog</a>.</em></p>
<blockquote>
<h2><!-- raw HTML omitted -->3.1.3 (2022-09-19)<!-- raw HTML omitted --></h2>
<ul>
<li>fix: esbuildOutputFromId for symlinked root (<a href="">#10154</a>) (<a href="">fc5310f</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10154">#10154</a></li>
<li>fix(hmr): dedupe virtual modules in module graph (<a href="">#10144</a>) (<a href="">71f08e7</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10144">#10144</a></li>
<li>fix(lib): respect <code>rollupOptions.input</code> in lib mode (<a href="">#10116</a>) (<a href="">c948e7d</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10116">#10116</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>dfa22ca</code></a> release: v3.1.3</li>
<li><a href=""><code>71f08e7</code></a> fix(hmr): dedupe virtual modules in module graph (<a href="">#10144</a>)</li>
<li><a href=""><code>c948e7d</code></a> fix(lib): respect <code>rollupOptions.input</code> in lib mode (<a href="">#10116</a>)</li>
<li><a href=""><code>fc5310f</code></a> fix: esbuildOutputFromId for symlinked root (<a href="">#10154</a>)</li>
<li>See full diff in <a href="https://github.com/vitejs/vite/commits/v3.1.3/packages/vite">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vite&package-manager=npm_and_yarn&previous-version=3.1.2&new-version=3.1.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3936bba920ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
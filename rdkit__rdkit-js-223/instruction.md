# Issue

**Title:** Bump vite from 3.2.1 to 3.2.2

## Description

Bumps [vite](https://github.com/vitejs/vite/tree/HEAD/packages/vite) from 3.2.1 to 3.2.2.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/blob/main/packages/vite/CHANGELOG.md">vite's changelog</a>.</em></p>
<blockquote>
<h2><!-- raw HTML omitted -->3.2.2 (2022-10-31)<!-- raw HTML omitted --></h2>
<ul>
<li>chore: remove src/client from package (<a href="">#10703</a>) (<a href="">816842e</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10703">#10703</a></li>
<li>chore(deps): update all non-major dependencies (<a href="">#10725</a>) (<a href="">22cfad8</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10725">#10725</a></li>
<li>fix: remove loaded input sourcemap (fixes <a href="">#8411</a>) (<a href="">#10705</a>) (<a href="">eb50e3a</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/8411">#8411</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10705">#10705</a></li>
<li>fix: tsconfig <code>jsx</code> overrides esbuild options, reverts <a href="">#10374</a> (<a href="">#10714</a>) (<a href="">aacf6a4</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10374">#10374</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10714">#10714</a></li>
<li>docs(changelog): fix broken url (<a href="">#10692</a>) (<a href="">f937ccc</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10692">#10692</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>65d69b4</code></a> release: v3.2.2</li>
<li><a href=""><code>22cfad8</code></a> chore(deps): update all non-major dependencies (<a href="">#10725</a>)</li>
<li><a href=""><code>aacf6a4</code></a> fix: tsconfig <code>jsx</code> overrides esbuild options, reverts <a href="">#10374</a> (<a href="">#10714</a>)</li>
<li><a href=""><code>816842e</code></a> chore: remove src/client from package (<a href="">#10703</a>)</li>
<li><a href=""><code>eb50e3a</code></a> fix: remove loaded input sourcemap (fixes <a href="">#8411</a>) (<a href="">#10705</a>)</li>
<li><a href=""><code>f937ccc</code></a> docs(changelog): fix broken url (<a href="">#10692</a>)</li>
<li>See full diff in <a href="https://github.com/vitejs/vite/commits/v3.2.2/packages/vite">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vite&package-manager=npm_and_yarn&previous-version=3.2.1&new-version=3.2.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83f4c31a8682`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Bump vite from 3.1.4 to 3.1.5

## Description

Bumps [vite](https://github.com/vitejs/vite/tree/HEAD/packages/vite) from 3.1.4 to 3.1.5.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/blob/v3.1.5/packages/vite/CHANGELOG.md">vite's changelog</a>.</em></p>
<blockquote>
<h2><!-- raw HTML omitted -->3.1.5 (2022-10-06)<!-- raw HTML omitted --></h2>
<ul>
<li>fix(build): fix resolution algorithm when <code>build.ssr</code> is true (<a href="">#9989</a>) (<a href="">f20d285</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9989">#9989</a></li>
<li>fix(config): resolve implicit deps as absolute path (<a href="">#10254</a>) (<a href="">dc140af</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10254">#10254</a></li>
<li>fix(css):  missing css in lib mode (<a href="">#10185</a>) (<a href="">e2cdb28</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10185">#10185</a></li>
<li>fix(esbuild): transpile with esnext in dev (<a href="">#10207</a>) (<a href="">abf2cfd</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10207">#10207</a></li>
<li>fix(hmr): handle virtual module update (<a href="">#10324</a>) (<a href="">14ebbc6</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10324">#10324</a></li>
<li>fix(ssr): correctly track scope (<a href="">#10300</a>) (<a href="">effb7c3</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10300">#10300</a></li>
<li>chore: fix build error (<a href="">01aa224</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>31f8ea6</code></a> release: v3.1.5</li>
<li><a href=""><code>f20d285</code></a> fix(build): fix resolution algorithm when <code>build.ssr</code> is true (<a href="">#9989</a>)</li>
<li><a href=""><code>01aa224</code></a> chore: fix build error</li>
<li><a href=""><code>14ebbc6</code></a> fix(hmr): handle virtual module update (<a href="">#10324</a>)</li>
<li><a href=""><code>e2cdb28</code></a> fix(css):  missing css in lib mode (<a href="">#10185</a>)</li>
<li><a href=""><code>effb7c3</code></a> fix(ssr): correctly track scope (<a href="">#10300</a>)</li>
<li><a href=""><code>dc140af</code></a> fix(config): resolve implicit deps as absolute path (<a href="">#10254</a>)</li>
<li><a href=""><code>abf2cfd</code></a> fix(esbuild): transpile with esnext in dev (<a href="">#10207</a>)</li>
<li>See full diff in <a href="https://github.com/vitejs/vite/commits/v3.1.5/packages/vite">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vite&package-manager=npm_and_yarn&previous-version=3.1.4&new-version=3.1.5)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `266dc520ccf3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
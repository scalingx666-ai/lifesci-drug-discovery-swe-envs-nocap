# Issue

**Title:** Bump vite from 3.2.0 to 3.2.1

## Description

Bumps [vite](https://github.com/vitejs/vite/tree/HEAD/packages/vite) from 3.2.0 to 3.2.1.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/blob/main/packages/vite/CHANGELOG.md">vite's changelog</a>.</em></p>
<blockquote>
<h2><!-- raw HTML omitted -->3.2.1 (2022-10-28)<!-- raw HTML omitted --></h2>
<ul>
<li>fix: prioritize existing env over .env (fixes <a href="">#10676</a>) (<a href="">#10684</a>) (<a href="">e2ea6af</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10676">#10676</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10684">#10684</a></li>
<li>fix: remove picomatch type import (fixes <a href="">#10656</a>) (<a href="">#10678</a>) (<a href="">1128b4d</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10656">#10656</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10678">#10678</a></li>
<li>fix(config): resolve externalized specifier with internal resolver (<a href="">#10683</a>) (<a href="">b15d21c</a>)</li>
<li>feat: Add support for imba in html scripts (<a href="">#10679</a>) (<a href="">b823fd6</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10679">#10679</a></li>
<li>chore: join URL segments more safely (<a href="">#10590</a>) (<a href="">675bf07</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10590">#10590</a></li>
<li>chore: update changelog for 3.2 (<a href="">#10646</a>) (<a href="">f787a60</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10646">#10646</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>47a78db</code></a> release: v3.2.1</li>
<li><a href=""><code>b15d21c</code></a> fix(config): resolve externalized specifier with internal resolver (<a href="">#10683</a>)</li>
<li><a href=""><code>e2ea6af</code></a> fix: prioritize existing env over .env (fixes <a href="">#10676</a>) (<a href="">#10684</a>)</li>
<li><a href=""><code>1128b4d</code></a> fix: remove picomatch type import (fixes <a href="">#10656</a>) (<a href="">#10678</a>)</li>
<li><a href=""><code>b823fd6</code></a> feat: Add support for imba in html scripts (<a href="">#10679</a>)</li>
<li><a href=""><code>675bf07</code></a> chore: join URL segments more safely (<a href="">#10590</a>)</li>
<li><a href=""><code>f787a60</code></a> chore: update changelog for 3.2 (<a href="">#10646</a>)</li>
<li>See full diff in <a href="https://github.com/vitejs/vite/commits/v3.2.1/packages/vite">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vite&package-manager=npm_and_yarn&previous-version=3.2.0&new-version=3.2.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `231e08c0388f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
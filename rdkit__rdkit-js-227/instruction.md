# Issue

**Title:** Bump vite from 3.2.2 to 3.2.3

## Description

Bumps [vite](https://github.com/vitejs/vite/tree/HEAD/packages/vite) from 3.2.2 to 3.2.3.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/blob/main/packages/vite/CHANGELOG.md">vite's changelog</a>.</em></p>
<blockquote>
<h2><!-- raw HTML omitted -->3.2.3 (2022-11-07)<!-- raw HTML omitted --></h2>
<ul>
<li>refactor: change style.innerHTML to style.textContent (<a href="">#10801</a>) (<a href="">8ea71b4</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10801">#10801</a></li>
<li>fix: add <code>@types/node</code> as an optional peer dependency (<a href="">#10757</a>) (<a href="">57916a4</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10757">#10757</a></li>
<li>fix: transform import.meta.glob when scan JS/TS <a href="">#10634</a> (<a href="">#10635</a>) (<a href="">c53ffec</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10634">#10634</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10635">#10635</a></li>
<li>fix(css): url() with variable in sass/less (fixes <a href="">#3644</a>, <a href="">#7651</a>) (<a href="">#10741</a>) (<a href="">fa2e47f</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/3644">#3644</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/7651">#7651</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10741">#10741</a></li>
<li>feat: add <code>vite:afterUpdate</code> event (<a href="">#9810</a>) (<a href="">1f57f84</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9810">#9810</a></li>
<li>perf: improve <code>multilineCommentsRE</code> regex (fix <a href="">#10689</a>) (<a href="">#10751</a>) (<a href="">51ed059</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10689">#10689</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10751">#10751</a></li>
<li>perf: Use only one ps exec to find a Chromium browser opened on Mac OS (<a href="">#10588</a>) (<a href="">f199e90</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10588">#10588</a></li>
<li>chore: fix dev build replacing undefined (<a href="">#10740</a>) (<a href="">1358a3c</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10740">#10740</a></li>
<li>chore: remove non used type definitions (<a href="">#10738</a>) (<a href="">ee8c7a6</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10738">#10738</a></li>
<li>chore(deps): update dependency <code>@​rollup/plugin-commonjs</code> to v23 (<a href="">#10611</a>) (<a href="">cc4be70</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10611">#10611</a></li>
<li>chore(deps): update dependency <code>@​rollup/plugin-dynamic-import-vars</code> to v2 (<a href="">#10726</a>) (<a href="">326f782</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10726">#10726</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ce4c8d4</code></a> release: v3.2.3</li>
<li><a href=""><code>8ea71b4</code></a> refactor: change style.innerHTML to style.textContent (<a href="">#10801</a>)</li>
<li><a href=""><code>57916a4</code></a> fix: add <code>@types/node</code> as an optional peer dependency (<a href="">#10757</a>)</li>
<li><a href=""><code>1f57f84</code></a> feat: add <code>vite:afterUpdate</code> event (<a href="">#9810</a>)</li>
<li><a href=""><code>51ed059</code></a> perf: improve <code>multilineCommentsRE</code> regex (fix <a href="">#10689</a>) (<a href="">#10751</a>)</li>
<li><a href=""><code>f199e90</code></a> perf: Use only one ps exec to find a Chromium browser opened on Mac OS (<a href="">#10588</a>)</li>
<li><a href=""><code>c53ffec</code></a> fix: transform import.meta.glob when scan JS/TS <a href="">#10634</a> (<a href="">#10635</a>)</li>
<li><a href=""><code>fa2e47f</code></a> fix(css): url() with variable in sass/less (fixes <a href="">#3644</a>, <a href="">#7651</a>) (<a href="">#10741</a>)</li>
<li><a href=""><code>1358a3c</code></a> chore: fix dev build replacing undefined (<a href="">#10740</a>)</li>
<li><a href=""><code>ee8c7a6</code></a> chore: remove non used type definitions (<a href="">#10738</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/vitejs/vite/commits/v3.2.3/packages/vite">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vite&package-manager=npm_and_yarn&previous-version=3.2.2&new-version=3.2.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d234c0418b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
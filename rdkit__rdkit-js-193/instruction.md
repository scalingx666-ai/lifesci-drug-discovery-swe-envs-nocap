# Issue

**Title:** Bump vite from 3.0.9 to 3.1.1

## Description

Bumps [vite](https://github.com/vitejs/vite/tree/HEAD/packages/vite) from 3.0.9 to 3.1.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/releases">vite's releases</a>.</em></p>
<blockquote>
<h2>create-vite@3.1.0</h2>
<p>Please refer to <a href="https://github.com/vitejs/vite/blob/create-vite@3.1.0/packages/create-vite/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vitejs/vite/blob/main/packages/vite/CHANGELOG.md">vite's changelog</a>.</em></p>
<blockquote>
<h2><!-- raw HTML omitted -->3.1.1 (2022-09-15)<!-- raw HTML omitted --></h2>
<ul>
<li>fix: ensure version query for relative node_modules imports (<a href="">#10016</a>) (<a href="">1b822d0</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10016">#10016</a></li>
<li>fix: no quote on attrs (<a href="">#10117</a>) (<a href="">f541239</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10117">#10117</a></li>
<li>fix: prevent error overlay style being overridden (fixes <a href="">#9969</a>) (<a href="">#9971</a>) (<a href="">a7706d0</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9969">#9969</a> <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9971">#9971</a></li>
<li>fix: proxy to secured websocket server (<a href="">#10045</a>) (<a href="">9de9bc4</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10045">#10045</a></li>
<li>fix: replace white with reset (<a href="">#10104</a>) (<a href="">5d56e42</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10104">#10104</a></li>
<li>fix(deps): update all non-major dependencies (<a href="">#10077</a>) (<a href="">caf00c8</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10077">#10077</a></li>
<li>fix(deps): update all non-major dependencies (<a href="">#9985</a>) (<a href="">855f2f0</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9985">#9985</a></li>
<li>fix(preview): send configured headers (<a href="">#9976</a>) (<a href="">0d20eae</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9976">#9976</a></li>
<li>chore: cleanup old changelogs (<a href="">#10056</a>) (<a href="">9e65a41</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10056">#10056</a></li>
<li>chore: update 3.1 changelog (<a href="">#9994</a>) (<a href="">44dbcbe</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9994">#9994</a></li>
<li>chore(deps): update <code>@​rollup/plugin-node-resolve</code> to v14 (<a href="">#10078</a>) (<a href="">3390c87</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/10078">#10078</a></li>
<li>refactor: config hook helper function (<a href="">#9982</a>) (<a href="">9c1be10</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9982">#9982</a></li>
<li>refactor: optimize <code>async</code> and <code>await</code> in code (<a href="">#9854</a>) (<a href="">31f5ff3</a>), closes <a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9854">#9854</a></li>
</ul>
<h2>3.1.0 (2022-09-05)</h2>
<h3>Main Changes</h3>
<ul>
<li>Vite now uses <a href="https://github.com/inikulin/parse5">parse5</a>, which parses HTML in the same way as the latest browser versions. This migration gives us a more robust HTML story moving forward (<a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9678">#9678</a>).</li>
<li>Vite now supports using objects as hooks to change execution order (<a href="https://github-redirect.dependabot.com/vitejs/vite/issues/9634">#9634</a>). Check out the <a href="https://github.com/vitejs/rfcs/discussions/12">RFC</a> and the implementation upstream at <a href="https://github-redirect.dependabot.com/rollup/rollup/pull/4600">rollup/rollup#4600</a> for details and rationale.
<pre lang="js"><code>  import { resolve } from 'node:path';
  import { readdir } from 'node:fs/promises';
<p>export default function getFilesOnDisk() {
return {
name: 'getFilesOnDisk',
writeBundle: {
// run this hook sequentially even if the hook is parallel
sequential: true,
// push this hook to the 'post' stage, after all normal hooks
order: 'post',
// hook implementation
async handler({ dir }) {
const topLevelFiles = await readdir(resolve(dir))
console.log(topLevelFiles)
}
}
}
}
</code></pre>
Read the updated <a href="https://rollupjs.org/guide/en/#build-hooks">Rollup Plugin docs</a> for more information.</li></p>
</ul>
<blockquote>
<p><strong>Note</strong>
After Vite 3.1, you are no longer going to see <code>[vite] hot updated</code> log messages in the browser console. These messages have been moved to the debug channel (<a href="https://github-redirect.dependabot.com/vitejs/vite/issues/8855">#8855</a>). Check your browser docs to <a href="https://developer.chrome.com/docs/devtools/console/log/#level">show debug logs</a>.</p>
</blockquote>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d324181</code></a> release: v3.1.1</li>
<li><a href=""><code>f541239</code></a> fix: no quote on attrs (<a href="">#10117</a>)</li>
<li><a href=""><code>5d56e42</code></a> fix: replace white with reset (<a href="">#10104</a>)</li>
<li><a href=""><code>caf00c8</code></a> fix(deps): update all non-major dependencies (<a href="">#10077</a>)</li>
<li><a href=""><code>3390c87</code></a> chore(deps): update <code>@​rollup/plugin-node-resolve</code> to v14 (<a href="">#10078</a>)</li>
<li><a href=""><code>9e65a41</code></a> chore: cleanup old changelogs (<a href="">#10056</a>)</li>
<li><a href=""><code>9de9bc4</code></a> fix: proxy to secured websocket server (<a href="">#10045</a>)</li>
<li><a href=""><code>1b822d0</code></a> fix: ensure version query for relative node_modules imports (<a href="">#10016</a>)</li>
<li><a href=""><code>a7706d0</code></a> fix: prevent error overlay style being overridden (fixes <a href="">#9969</a>) (<a href="">#9971</a>)</li>
<li><a href=""><code>31f5ff3</code></a> refactor: optimize <code>async</code> and <code>await</code> in code (<a href="">#9854</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/vitejs/vite/commits/v3.1.1/packages/vite">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vite&package-manager=npm_and_yarn&previous-version=3.0.9&new-version=3.1.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae43037edcdb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
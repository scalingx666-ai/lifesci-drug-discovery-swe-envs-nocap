# Issue

**Title:** Bump vue-tsc from 1.0.11 to 1.8.3

## Description

Bumps [vue-tsc](https://github.com/vuejs/language-tools/tree/HEAD/packages/vue-tsc) from 1.0.11 to 1.8.3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/vuejs/language-tools/releases">vue-tsc's releases</a>.</em></p>
<blockquote>
<h2>v1.8.0</h2>
<p>2.0 schedule has been postponed: <a href="">#3294</a></p>
<h2>Highlights</h2>
<ul>
<li>
<p>Support for <a href="https://blog.vuejs.org/posts/volar-a-new-beginning">Scripts API</a></p>
<p>If you want to use the formatting feature through the Scripts API, please refer to <a href="">#3133</a>.</p>
<p>If you want to use the diagnostic feature through the Scripts API, please refer to <a href="https://github.com/withastro/language-tools/blob/main/packages/language-server/src/check.ts">https://github.com/withastro/language-tools/blob/main/packages/language-server/src/check.ts</a>.</p>
</li>
<li>
<p>Support for <a href="https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volarjs-labs">Volar.js Labs</a> (<a href="https://twitter.com/johnsoncodehk/status/1656126976774791168">Ref</a>)</p>
</li>
<li>
<p>Improved Vue 3.3 syntax support</p>
</li>
<li>
<p>TS 5.1.3 compatible</p>
</li>
<li>
<p>Upgrade to Volar.js 1.7 to big improve support for Monaco and <a href="https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.vscode-typescript-web">TypeScript IntelliSense for Web</a></p>
</li>
<li>
<p>Support for new <code>@vue-ignore</code>, <code>@vue-skip</code>, <code>@vue-expect-error</code> directive comments syntax (<a href="">#3215</a>)</p>
</li>
</ul>
<h2>Breaking changes</h2>
<ul>
<li>
<p><code>volar.config.js</code> <code>plugins</code> option has been renamed to <code>services</code></p>
</li>
<li>
<p>Renaming packages from <code>@volar/vue-*</code> to <code>@vue/*</code> (<a href="">#3134</a>)</p>
</li>
</ul>
<hr />
<p>Please refer to <a href="https://github.com/vuejs/language-tools/blob/master/CHANGELOG.md">CHANGELOG.md</a> for details.</p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vuejs/language-tools/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>1.8.3 (2023/6/28)</h2>
<ul>
<li>fix(ts-plugin): tsserver crashes when import &gt; 4MB .vue file (<a href="">#3332</a>)</li>
<li>fix(language-server): in specific os <code>fileExists()</code> throws (<a href="">#3336</a>)</li>
</ul>
<hr />
<!-- raw HTML omitted -->
<!-- raw HTML omitted -->
<!-- raw HTML omitted -->
<!-- raw HTML omitted -->
<!-- raw HTML omitted -->
<!-- raw HTML omitted -->
<h2>1.8.2 (2023/6/27)</h2>
<ul>
<li>fix: should not auto closing <code>&lt;img&gt;</code> tag (<a href="">#3217</a>)</li>
<li>fix: allow passing undefined as events (<a href="">#3122</a>) (<a href="">#3217</a>) - thanks <a href="https://github.com/so1ve"><code>@​so1ve</code></a></li>
<li>fix: fixes object literal parsing for <!-- raw HTML omitted --> (<a href="">#3324</a>) (<a href="">#3171</a>) - thanks <a href="https://github.com/so1ve"><code>@​so1ve</code></a></li>
<li>fix: symbol types are lost (<a href="">#3300</a>) (<a href="">#3295</a>) - thanks <a href="https://github.com/so1ve"><code>@​so1ve</code></a></li>
<li>fix(ts-plugin): suppress errors when <code>composite</code> is enabled</li>
<li>fix(language-server): trigger characters missing on web IDE</li>
<li>perf(language-server): debounce for <code>isCancellationRequested()</code></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a02e928</code></a> v1.8.3</li>
<li><a href=""><code>de0fb3f</code></a> v1.8.2</li>
<li><a href=""><code>3e31c6e</code></a> v1.8.1</li>
<li><a href=""><code>289acee</code></a> feat: upgrade volar to improve ts plugin support</li>
<li><a href=""><code>6e2e04e</code></a> v1.8.0</li>
<li><a href=""><code>a8a05a2</code></a> v1.7.14</li>
<li><a href=""><code>d275a54</code></a> chore: use try catch instead of <code>existsSync</code></li>
<li><a href=""><code>32d5d5e</code></a> v1.7.13</li>
<li><a href=""><code>8a610ef</code></a> test: strict template unknown props (<a href="">#3284</a>)</li>
<li><a href=""><code>9e712c2</code></a> v1.7.12</li>
<li>Additional commits viewable in <a href="https://github.com/vuejs/language-tools/commits/v1.8.3/packages/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=1.0.11&new-version=1.8.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ecfa8dfd081`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
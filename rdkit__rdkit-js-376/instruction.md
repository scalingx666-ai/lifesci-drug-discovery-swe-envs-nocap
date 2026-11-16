# Issue

**Title:** Bump vue-tsc from 1.8.3 to 1.8.8

## Description

Bumps [vue-tsc](https://github.com/vuejs/language-tools/tree/HEAD/packages/vue-tsc) from 1.8.3 to 1.8.8.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/vuejs/language-tools/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>1.8.8 (2023/7/27)</h2>
<ul>
<li>fix: language server crashed due to importing unexist library (<a href="">#3453</a>) (<a href="">#3454</a>)</li>
</ul>
<h2>1.8.7 (2023/7/27)</h2>
<ul>
<li>feat: support auto-complete for directives (<a href="">#2559</a>)</li>
<li>feat: support extract component for options api</li>
<li>feat: re-support external component parsing (<a href="">#3328</a>)</li>
<li>feat: support function expression emit event (<a href="">#3445</a>) - thanks <a href="https://github.com/lvjiaxuan"><code>@​lvjiaxuan</code></a></li>
<li>perf: reuse VueFile instances between monorepo packages (<a href="">#3450</a>)</li>
<li>fix: handle node next module resolution (<a href="">#3159</a>) - thanks <a href="https://github.com/kalvenschraut"><code>@​kalvenschraut</code></a></li>
<li>fix: generate valid code when using <code>__VLS_PropsChildren</code> (<a href="">#3442</a>) - thanks <a href="https://github.com/so1ve"><code>@​so1ve</code></a></li>
<li>fix: component auto-import cannot insert import statement</li>
<li>fix: extract component cannot extract interpolations</li>
<li>fix: allow top-level await in script setup blocks with generics (<a href="">#3441</a>) - thanks <a href="https://github.com/so1ve"><code>@​so1ve</code></a></li>
</ul>
<h3>Full-time Support by</h3>
<!-- raw HTML omitted -->
<h3>Our Platinum Sponsors</h3>
<!-- raw HTML omitted -->
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>62a08c3</code></a> v1.8.8</li>
<li><a href=""><code>2b88890</code></a> v1.8.7</li>
<li><a href=""><code>9da8afe</code></a> v1.8.6</li>
<li><a href=""><code>b7fd537</code></a> Extract into simple component refactoring (<a href="">#2496</a>)</li>
<li><a href=""><code>971820b</code></a> v1.8.5</li>
<li><a href=""><code>5f9eee7</code></a> feat: sync volar 1.9.0</li>
<li><a href=""><code>b8f111b</code></a> perf: hoist regexp if possible (<a href="">#3378</a>)</li>
<li><a href=""><code>4809729</code></a> fix: camel case components is not recognized as used (<a href="">#3377</a>)</li>
<li><a href=""><code>a62aa88</code></a> v1.8.4</li>
<li><a href=""><code>f7dda2a</code></a> fix: sync volar usage (<a href="">#3357</a>)</li>
<li>See full diff in <a href="https://github.com/vuejs/language-tools/commits/v1.8.8/packages/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=1.8.3&new-version=1.8.8)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2777560afa5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
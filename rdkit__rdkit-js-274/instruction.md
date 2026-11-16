# Issue

**Title:** Bump vue-tsc from 1.0.9 to 1.0.10

## Description

Bumps [vue-tsc](https://github.com/johnsoncodehk/volar/tree/HEAD/vue-language-tools/vue-tsc) from 1.0.9 to 1.0.10.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/johnsoncodehk/volar/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>1.0.10 (2022/11/29)</h2>
<ul>
<li>feat: add <code>volar.vueserver.json.customBlockSchemaUrls</code> setting to support preset json schema urls for custom blocks (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2079">#2079</a>)</li>
<li>feat: add <code>volar.vueserver.reverseConfigFilePriority</code> setting to support customize tsconfig priority (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1815">#1815</a>)</li>
<li>feat: add <code>volar.vueserver.disableFileWatcher</code> setting for better performance (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2027">#2027</a>)</li>
<li>feat(vue-tsc): support for TypeScript 5.0 (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2095">#2095</a>)</li>
<li>feat: auto insert parentheses for <code>instanceof</code> expressions (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2099">#2099</a>)</li>
<li>feat: more accurate HTML attributes auto-complete</li>
<li>feat: add <code>nativeTags</code> instead of <code>experimentalRuntimeMode</code> to vueCompilerOptions for uni-app supports (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2065">#2065</a>)</li>
<li>feat: remove split editors icon and use command instead of</li>
<li>fix: goto definition not working with nvim-lspconfig (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/pull/1916#issuecomment-1293166322">johnsoncodehk/volar#1916</a>)</li>
<li>fix(preview): more accurate script judgment (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2135">#2135</a>)</li>
<li>fix: local components types should cover global components types (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1886">#1886</a>)</li>
<li>fix: auto insert parentheses for AsExpressions not working</li>
<li>fix: template code mapping confusion when undo with invalid template code (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2151">#2151</a>)</li>
<li>fix: output Server Stats through LSP API (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2050">#2050</a>)</li>
<li>fix: vite app preview not working if project path includes spaces (<a href="https://github-redirect.dependabot.com/johnsoncodehk/vite-plugin-vue-component-preview/issues/7">johnsoncodehk/vite-plugin-vue-component-preview#7</a>)</li>
<li>fix: avoid component preview create multiple terminals (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2128">#2128</a>)</li>
<li>fix: avoid folding when join split editors (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1887">#1887</a>)</li>
<li>fix: split editors command crash with empty document (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2072">#2072</a>)</li>
<li>fix: avoid escape <code>&amp;quot;</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2091">#2091</a>)</li>
<li>fix: script setup first variable jsdoc missing (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1327#issuecomment-1304784005">johnsoncodehk/volar#1327</a>)</li>
<li>fix: document symbols of SFC blocks range incorrect (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2118">#2118</a>)</li>
<li>fix: <code>strictTemplates</code> option works only bound props (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2136">#2136</a>)</li>
<li>fix: props required warning missing when <code>jsxTemplates</code> option enabled (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2139">#2139</a>)</li>
<li>fix: cannot infer events parameter type in recursive component (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2140">#2140</a>)</li>
<li>perf: faster semantic tokens parsing (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2053">#2053</a>) (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2056">#2056</a>)</li>
<li>perf: avoid create file watchers in syntactic server</li>
<li>perf: cache workspace configuration in language servers (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2062">#2062</a>)</li>
</ul>
<h3>Special Sponsor</h3>
<!-- raw HTML omitted -->
<h3>Out Gold Sponsors</h3>
<!-- raw HTML omitted -->
<h3>Out Silver Sponsors</h3>
<!-- raw HTML omitted -->
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>89b82f9</code></a> v1.0.10</li>
<li><a href=""><code>e1cc687</code></a> feat: support TS v5 for svelte-tsc</li>
<li><a href=""><code>8f5ba72</code></a> fix typo (<a href="">#2112</a>)</li>
<li><a href=""><code>a59ee4e</code></a> feat(vue-tsc): support for TS v5</li>
<li>See full diff in <a href="https://github.com/johnsoncodehk/volar/commits/v1.0.10/vue-language-tools/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=1.0.9&new-version=1.0.10)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f3666cbabe9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
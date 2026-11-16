# Issue

**Title:** Bump vue-tsc from 0.38.9 to 0.40.1

## Description

Bumps [vue-tsc](https://github.com/johnsoncodehk/volar/tree/HEAD/packages/vue-tsc) from 0.38.9 to 0.40.1.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/johnsoncodehk/volar/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>0.40.1 (2022/8/11)</h2>
<ul>
<li>fix: component context types missing in template if no script block (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1688">#1688</a>)</li>
<li>fix: organize imports added invalid code (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1692">#1692</a>)</li>
<li>fix: v-else template interpolation missing in virtual code (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1694">#1694</a>)</li>
<li>fix: template interpolation formatting broken (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1697">#1697</a>)</li>
<li>fix: inline css intellisense not working</li>
</ul>
<h3>Our Sponsors</h3>
<!-- raw HTML omitted -->
<h2>0.40.0 (2022/8/10)</h2>
<ul>
<li>feat: support document highlights cross <code>&lt;script&gt;</code>, <code>\&lt;template&gt;</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/462">#462</a>)</li>
<li>feat: support reference types from script setup in template (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/891">#891</a>)</li>
<li>feat: support auto import in template (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/823">#823</a>)</li>
<li>feat: support plugin api (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/185">#185</a>) (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1687">#1687</a>)</li>
<li>fix: template scope variables completion missing (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1284">#1284</a>)</li>
<li>fix: prefer <code>defineComponent</code> instead of <code>Vue.extend</code> to wrap component options by default (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1584">#1584</a>)</li>
<li>fix: bracket pair colorization in VSCode v1.70 (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1677">#1677</a>)</li>
</ul>
<h2>0.39.5 (2022/8/6)</h2>
<ul>
<li>feat(vue-component-meta): add option to expose raw type (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1674">#1674</a>)</li>
<li>fix(vue-component-meta): recursive schema parsing (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1660">#1660</a>)</li>
<li>fix(vue-component-meta): parse defineProps in script setup with option (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1665">#1665</a>)</li>
<li>fix: SFC syntax broken in vscode v1.70.0 (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1566">#1566</a>) (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1675">#1675</a>)</li>
<li>fix: vite app preview not working (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1668">#1668</a>)</li>
<li>fix: diagnosis is slow on windows after v0.39.2 (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1663">#1663</a>)</li>
<li>fix: <code>compilerOptions.types</code> not working since v0.39.2 (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1650">#1650</a>)</li>
<li>fix: avoid auto-import path append <code>.js</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1667">#1667</a>)</li>
<li>fix: avoid variables defined after export default report TS_2454</li>
<li>perf: cache semver result on auto-complete</li>
</ul>
<h2>0.39.4 (2022/7/31)</h2>
<ul>
<li>feat: support ESM project (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1543">#1543</a>)</li>
<li>fix: &quot;Volar: Reload Project&quot; command cannot detect node_modules change</li>
<li>fix: webview buttons show to unrelated extensions (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1611">#1611</a>)</li>
</ul>
<h2>0.39.3 (2022/7/31)</h2>
<ul>
<li>feat(vue-component-meta): component schema improves (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1656">#1656</a>)</li>
<li>feat(vue-component-meta): support options api props default (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1649">#1649</a>)</li>
<li>feat: add &quot;Volar: Reload Project&quot; command (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1605">#1605</a>)</li>
<li>fix: vue-tsc watch not working (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1647">#1647</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4f92ef8</code></a> v0.40.1</li>
<li><a href=""><code>9207e74</code></a> v0.40.0</li>
<li><a href=""><code>9237d8b</code></a> feat: generate single .tsx file for vue script (<a href="">#1686</a>)</li>
<li><a href=""><code>b2efb24</code></a> v0.39.5</li>
<li><a href=""><code>e3f6327</code></a> v0.39.4</li>
<li><a href=""><code>57a7b0f</code></a> v0.39.3</li>
<li><a href=""><code>eac2dca</code></a> v0.39.2</li>
<li><a href=""><code>844b470</code></a> feat: add vue-component-meta</li>
<li><a href=""><code>569487a</code></a> v0.39.0</li>
<li><a href=""><code>8a2785a</code></a> refactor: loadTypeScriptModule -&gt; getTypeScriptModule</li>
<li>Additional commits viewable in <a href="https://github.com/johnsoncodehk/volar/commits/v0.40.1/packages/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=0.38.9&new-version=0.40.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73122f60b0d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
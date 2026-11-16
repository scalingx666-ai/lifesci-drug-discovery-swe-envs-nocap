# Issue

**Title:** Bump vue-tsc from 0.40.13 to 1.0.7

## Description

Bumps [vue-tsc](https://github.com/johnsoncodehk/volar/tree/HEAD/vue-language-tools/vue-tsc) from 0.40.13 to 1.0.7.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/johnsoncodehk/volar/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>1.0.7 (2022/10/13)</h2>
<ul>
<li>feat(vue-language-core): support custom v-model prefix (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2004">#2004</a>)</li>
<li>feat: allow passing attributes array for <code>experimentalModelPropName</code> ignore setting (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1821">#1821</a>)</li>
<li>fix: <code>@volar/vue-language-plugin-pug</code> cause to doctor warns in Vue 2.7 project (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2002">#2002</a>)</li>
<li>fix: mitigate virtual file mapping highlights dislocation</li>
<li>fix: tag hover not working when enabled <code>jsxTemplates</code></li>
<li>fix: avoid convert invalid JSX type to any when enabled <code>jsxTemplates</code></li>
<li>fix: component JSX type invalid when enabled <code>jsxTemplates</code> but template has no any slots</li>
<li>perf: try skip convert attribute value to unicode</li>
</ul>
<h3>Our Sponsors</h3>
<!-- raw HTML omitted -->
<h2>1.0.6 (2022/10/12)</h2>
<ul>
<li>fix: component ast broken when use script setup with <code>export default</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1996">#1996</a>)</li>
<li>fix: <code>experimentalModelPropName</code> link invalid (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1999">#1999</a>)</li>
<li>fix: <code>@volar/pug-language-service</code> crash (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2000">#2000</a>)</li>
</ul>
<h2>1.0.5 (2022/10/12)</h2>
<ul>
<li>feat(doctor): report warning for <code>@types/node</code> version <code>&gt;= 18.8.1</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1985">#1985</a>)</li>
<li>fix: <code>@volar-examples/svelte-tsc</code>, <code>@volar-examples/svelte-typescript</code> released empty dist</li>
<li>fix: component syntax minor defect when enabled <code>experimentalRfc436</code></li>
<li>fix: force use VSCode display language in language server (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1959">#1959</a>)</li>
<li>fix: don't hoisting defineProps type arg when disabled <code>experimentalRfc436</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1994">#1994</a>)</li>
</ul>
<h2>1.0.4 (2022/10/12)</h2>
<ul>
<li>feat: Support generic typed template slots for RFC 436 (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1987">#1987</a>)</li>
<li>feat: add <code>resolveTemplateCompilerOptions</code> API for <code>VueLanguagePlugin</code></li>
<li>feat: support intellisense for <code>generic</code> attribute (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1967">#1967</a>)</li>
<li>feat: add <code>Show Component Meta</code> command for inspect <code>vue-component-meta</code> result</li>
<li>feat: add <code>vueCompilerOptions.experimentalModelPropName</code> for customize <code>v-model</code> binding prop for vue 2 component (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1969">#1969</a>)</li>
<li>fix: <code>TypeScript Vue Plugin (Volar)</code> stop working</li>
<li>fix: change <code>vueCompilerOptions.dataAttributes</code> default value from <code>[&quot;data-*&quot;]</code> to <code>[]</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1965">#1965</a>)</li>
<li>fix: component props order should be on the top (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1972">#1972</a>)</li>
<li>fix: <code>@volar/vue-language-plugin-pug</code> crash due to missing depend</li>
<li>fix: component tag highlight not working for pug template (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1977">#1977</a>)</li>
<li>fix: references codeLens number incorrect (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1989">#1989</a>)</li>
</ul>
<p><strong>Breaking changes</strong></p>
<ul>
<li>Removed <code>experimentalTemplateCompilerOptions</code>, <code>experimentalTemplateCompilerOptionsRequirePath</code> from <code>vueCompilerOptions</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1991">#1991</a>)</li>
</ul>
<h2>1.0.3 (2022/10/10)</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>96cc1ac</code></a> v1.0.7</li>
<li><a href=""><code>21df343</code></a> v1.0.6</li>
<li><a href=""><code>9735e41</code></a> v1.0.5</li>
<li><a href=""><code>1394533</code></a> v1.0.4</li>
<li><a href=""><code>2576804</code></a> v1.0.3</li>
<li><a href=""><code>4e750f8</code></a> v1.0.2</li>
<li><a href=""><code>62a5dce</code></a> v1.0.1</li>
<li><a href=""><code>5496c1e</code></a> v1.0.0</li>
<li><a href=""><code>2100689</code></a> v1.0.0-rc.5</li>
<li><a href=""><code>eadcf13</code></a> v1.0.0-rc.4</li>
<li>Additional commits viewable in <a href="https://github.com/johnsoncodehk/volar/commits/v1.0.7/vue-language-tools/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=0.40.13&new-version=1.0.7)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a1b8a8ecfed7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
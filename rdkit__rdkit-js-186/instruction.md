# Issue

**Title:** Bump vue-tsc from 0.40.5 to 0.40.7

## Description

Bumps [vue-tsc](https://github.com/johnsoncodehk/volar/tree/HEAD/packages/vue-tsc) from 0.40.5 to 0.40.7.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/johnsoncodehk/volar/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>0.40.7 (2022/9/5)</h2>
<ul>
<li>feat: support multiple workspaces for document features</li>
<li>feat: add <code>initializationOptions.completion.ignoreTriggerCharacters</code> for LSP-Volar (<a href="https://github-redirect.dependabot.com/sublimelsp/LSP-volar/issues/114">sublimelsp/LSP-volar#114</a>)</li>
<li>feat: add <code>vueCompilerOptions.experimentalComponentOptionsWrapper</code> option for custom component options warpper (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1517">#1517</a>)</li>
<li>fix: add missing surrounding pair &quot;`&quot; (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1659">#1659</a>)</li>
<li>fix: formatting edit range incorrect edge case (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1814">#1814</a>)</li>
<li>fix: typescript onType format do not respect <code>typescript.format.enable</code></li>
<li>fix: document features stop working for script block (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1813">#1813</a>)</li>
<li>fix: pug formatter extra spaces in <code>{{ }}</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1784">#1784</a>)</li>
<li>fix: template incremental parser broken when typing slot name</li>
</ul>
<p><strong>Breaking changes</strong></p>
<ul>
<li>vueCompilerOptions properties <code>experimentalImplicitWrapComponentOptionsWithDefineComponent</code>, <code>experimentalImplicitWrapComponentOptionsWithVue2Extend</code> replaced by <code>experimentalComponentOptionsWrapper</code>.</li>
</ul>
<h3>Our Sponsors</h3>
<!-- raw HTML omitted -->
<h2>0.40.6 (2022/9/4)</h2>
<ul>
<li>feat: support language features for Web IDE (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/612">#612</a>)</li>
<li>feat: update vite problemMatcher (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1801">#1801</a>)</li>
<li>feat: add <code>volar.vueserver.textDocumentSync</code> option to disable incremental update (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1807">#1807</a>)</li>
<li>fix: <code>v-for</code>, <code>v-if</code> textmate scopes incorrect (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1810">#1810</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>09b517f</code></a> v0.40.7</li>
<li><a href=""><code>f87049a</code></a> v0.40.6</li>
<li>See full diff in <a href="https://github.com/johnsoncodehk/volar/commits/v0.40.7/packages/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=0.40.5&new-version=0.40.7)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `927f95da4efd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
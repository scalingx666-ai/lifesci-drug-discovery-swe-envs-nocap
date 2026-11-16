# Issue

**Title:** Bump vue-tsc from 1.0.8 to 1.0.9

## Description

Bumps [vue-tsc](https://github.com/johnsoncodehk/volar/tree/HEAD/vue-language-tools/vue-tsc) from 1.0.8 to 1.0.9.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/johnsoncodehk/volar/blob/master/CHANGELOG.md">vue-tsc's changelog</a>.</em></p>
<blockquote>
<h2>1.0.9 (2022/10/23)</h2>
<ul>
<li>feat(vue-tsc): add error message for <code>noEmitOnError</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1669">#1669</a>)</li>
<li>feat: add support for custom file extensions (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1931">#1931</a>)</li>
<li>feat: add support for <code>typescript/javascript.suggest.completeFunctionCalls</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/956">#956</a>)</li>
<li>feat: add support for JSX auto closing tags and tags commenting (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1494">#1494</a>)</li>
<li>feat: add support for auto import component from .ts sources (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1643">#1643</a>)</li>
<li>feat: add <code>Server Stats</code> command for debugging loading files</li>
<li>feat: add <code>volar.completion.normalizeComponentAutoImportName</code> setting to support remove <code>Vue</code> ending for component auto import (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/82">#82</a>)</li>
<li>feat: add <code>volar.vueserver.diagnosticModel</code> setting to support pull model for diagnostic</li>
<li>feat: add <code>experimentalUseElementAccessInTemplate</code> setting in vueCompilerOptions for class component supports (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/997">#997</a>)</li>
<li>feat: migrated to standard token types for support semantic tokens IDE other than VSCode</li>
<li>feat: register file watchers in language server for support IDE other than VSCode (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2037">#2037</a>)</li>
<li>perf: load scripts on demand on inferred project</li>
<li>fix(doctor): update valid <code>@types/node</code> version and clarity words (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2043">#2043</a>)</li>
<li>fix: avoid language server crash by invalid tsconfig references path (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1957">#1957</a>)</li>
<li>fix: <code>LanguageServicePlugin</code> error don'ts reporting</li>
<li>fix: SCSS At-Rule autocomplete not working</li>
<li>fix: intellisense not working for files path start with <code>.</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1147">#1147</a>)</li>
<li>fix: avoid reporting partial diagnostic when failed to update cache range</li>
<li>fix: formatting not working for template interpolations (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2026">#2026</a>)</li>
<li>fix: file watchers not working (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2028">#2028</a>)</li>
<li>fix: document version of code action incorrect (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2025">#2025</a>)</li>
<li>fix: don't filter <code>onXxx</code> for props autocomplete (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2034">#2034</a>)</li>
<li>fix: import statements completion not working (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1983#issuecomment-1278778898">johnsoncodehk/volar#1983</a>)</li>
<li>fix: server throwing errors due to component auto import completion canceled (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1983">#1983</a>)</li>
<li>fix: expand selection does not work correctly in <code>\&lt;template&gt;</code> (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/1465">#1465</a>)</li>
<li>fix: component tags messes with duplicate name template properties (<a href="https://github-redirect.dependabot.com/johnsoncodehk/volar/issues/2030">#2030</a>)</li>
<li>fix: improve invalid content trimming in .md files for VitePress</li>
<li>fix: avoid language server throwing when changing built-in TS plugin activation</li>
</ul>
<h3>Special Sponsor</h3>
<!-- raw HTML omitted -->
<h3>Out Gold Sponsors</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6490d60</code></a> v1.0.9</li>
<li><a href=""><code>c21e10b</code></a> doc: update sponsors display</li>
<li><a href=""><code>b4ea520</code></a> feat(vue-tsc): throw error for <code>noEmitOnError</code></li>
<li>See full diff in <a href="https://github.com/johnsoncodehk/volar/commits/v1.0.9/vue-language-tools/vue-tsc">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=vue-tsc&package-manager=npm_and_yarn&previous-version=1.0.8&new-version=1.0.9)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `471ffaf9aa97`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
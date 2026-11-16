# Issue

**Title:** Bump @angular/compiler from 14.2.10 to 15.2.0

## Description

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

Bumps [@angular/compiler](https://github.com/angular/angular/tree/HEAD/packages/compiler) from 14.2.10 to 15.2.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/angular/angular/releases"><code>@​angular/compiler</code>'s releases</a>.</em></p>
<blockquote>
<h2>v15.2.0</h2>
<p><!-- raw HTML omitted --><!-- raw HTML omitted --></p>
<h1>15.2.0 (2023-02-22)</h1>
<h2>Deprecations</h2>
<h3></h3>
<ul>
<li>Class and <code>InjectionToken</code> guards and resolvers are
deprecated. Instead, write guards as plain JavaScript functions and
inject dependencies with <code>inject</code> from <code>@angular/core</code>.</li>
</ul>
<h3></h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/926c35f4ac-docs-yellow" alt="docs - 926c35f4ac" /></a></td>
<td>Deprecate class and InjectionToken and resolvers (<a href="">#47924</a>)</td>
</tr>
</tbody>
</table>
<h3>common</h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/54b24eb40f-feat-blue" alt="feat - 54b24eb40f" /></a></td>
<td>Add loaderParams attribute to NgOptimizedImage (<a href="">#48907</a>)</td>
</tr>
</tbody>
</table>
<h3>compiler-cli</h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/0cf11167f1-fix-green" alt="fix - 0cf11167f1" /></a></td>
<td>incorrectly detecting forward refs when symbol already exists in file (<a href="">#48988</a>)</td>
</tr>
</tbody>
</table>
<h3>core</h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/a154db8a81-feat-blue" alt="feat - a154db8a81" /></a></td>
<td>add ng generate schematic to convert declarations to standalone (<a href="">#48790</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/345e737daa-feat-blue" alt="feat - 345e737daa" /></a></td>
<td>add ng generate schematic to convert to standalone bootstrapping APIs (<a href="">#48848</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/e7318fc758-feat-blue" alt="feat - e7318fc758" /></a></td>
<td>add ng generate schematic to remove unnecessary modules (<a href="">#48832</a>)</td>
</tr>
</tbody>
</table>
<h3>language-service</h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/4ae384fd61-feat-blue" alt="feat - 4ae384fd61" /></a></td>
<td>Allow auto-imports of a pipe via quick fix when its selector is used, both directly and via reexports. (<a href="">#48354</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/141333411e-feat-blue" alt="feat - 141333411e" /></a></td>
<td>Introduce a new NgModuleIndex, and use it to suggest re-exports. (<a href="">#48354</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/d0145033bd-fix-green" alt="fix - d0145033bd" /></a></td>
<td>generate forwardRef for same file imports (<a href="">#48898</a>)</td>
</tr>
</tbody>
</table>
<h3>migrations</h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/2796230e95-fix-green" alt="fix - 2796230e95" /></a></td>
<td>add <code>enum</code> in <code>mode</code> option in <code>standalone</code> schema (<a href="">#48851</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/816e76a578-fix-green" alt="fix - 816e76a578" /></a></td>
<td>automatically prune root module after bootstrap step (<a href="">#49030</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/bdbf21d04b-fix-green" alt="fix - bdbf21d04b" /></a></td>
<td>avoid generating imports with forward slashes (<a href="">#48993</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/32cf4e5cb9-fix-green" alt="fix - 32cf4e5cb9" /></a></td>
<td>avoid internal modules when generating imports (<a href="">#48958</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/521ccfbe6c-fix-green" alt="fix - 521ccfbe6c" /></a></td>
<td>avoid interrupting the migration if language service lookup fails (<a href="">#49010</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/a40cd47aa7-fix-green" alt="fix - a40cd47aa7" /></a></td>
<td>avoid modifying testing modules without declarations (<a href="">#48921</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/1afa6ed322-fix-green" alt="fix - 1afa6ed322" /></a></td>
<td>don't add ModuleWithProviders to standalone test components (<a href="">#48987</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/c98c6a8452-fix-green" alt="fix - c98c6a8452" /></a></td>
<td>don't copy animations modules into the imports of test components (<a href="">#49147</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/8389557848-fix-green" alt="fix - 8389557848" /></a></td>
<td>don't copy unmigrated declarations into imports array (<a href="">#48882</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/f82bdc4b01-fix-green" alt="fix - f82bdc4b01" /></a></td>
<td>don't delete classes that may provide dependencies transitively (<a href="">#48866</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/759db12e0b-fix-green" alt="fix - 759db12e0b" /></a></td>
<td>duplicated comments on migrated classes (<a href="">#48966</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/ba38178d19-fix-green" alt="fix - ba38178d19" /></a></td>
<td>generate forwardRef for same file imports (<a href="">#48898</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/03fcb36cfd-fix-green" alt="fix - 03fcb36cfd" /></a></td>
<td>migrate HttpClientModule to provideHttpClient() (<a href="">#48949</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/2de6dae16d-fix-green" alt="fix - 2de6dae16d" /></a></td>
<td>migrate RouterModule.forRoot with a config object to use features (<a href="">#48935</a>)</td>
</tr>
<tr>
<td><a href=""><img src="https://img.shields.io/badge/770191cf1f-fix-green" alt="fix - 770191cf1f" /></a></td>
<td>migrate tests when switching to standalone bootstrap API (<a href="">#48987</a>)</td>
</tr>
</tbody>
</table>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/angular/angular/blob/main/CHANGELOG.md"><code>@​angular/compiler</code>'s changelog</a>.</em></p>
<blockquote>
<h1>15.2.0 (2023-02-22)</h1>
<h2>Deprecations</h2>
<h3></h3>
<ul>
<li>Class and <code>InjectionToken</code> guards and resolvers are
deprecated. Instead, write guards as plain JavaScript functions and
inject dependencies with <code>inject</code> from <code>@angular/core</code>.</li>
</ul>
<h3></h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="">926c35f4ac</a></td>
<td>docs</td>
<td>Deprecate class and InjectionToken and resolvers (<a href="https://github-redirect.dependabot.com/angular/angular/pull/47924">#47924</a>)</td>
</tr>
</tbody>
</table>
<h3>common</h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="">54b24eb40f</a></td>
<td>feat</td>
<td>Add loaderParams attribute to NgOptimizedImage (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48907">#48907</a>)</td>
</tr>
</tbody>
</table>
<h3>compiler-cli</h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="">0cf11167f1</a></td>
<td>fix</td>
<td>incorrectly detecting forward refs when symbol already exists in file (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48988">#48988</a>)</td>
</tr>
</tbody>
</table>
<h3>core</h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="">a154db8a81</a></td>
<td>feat</td>
<td>add ng generate schematic to convert declarations to standalone (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48790">#48790</a>)</td>
</tr>
<tr>
<td><a href="">345e737daa</a></td>
<td>feat</td>
<td>add ng generate schematic to convert to standalone bootstrapping APIs (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48848">#48848</a>)</td>
</tr>
<tr>
<td><a href="">e7318fc758</a></td>
<td>feat</td>
<td>add ng generate schematic to remove unnecessary modules (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48832">#48832</a>)</td>
</tr>
</tbody>
</table>
<h3>language-service</h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="">4ae384fd61</a></td>
<td>feat</td>
<td>Allow auto-imports of a pipe via quick fix when its selector is used, both directly and via reexports. (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48354">#48354</a>)</td>
</tr>
<tr>
<td><a href="">141333411e</a></td>
<td>feat</td>
<td>Introduce a new NgModuleIndex, and use it to suggest re-exports. (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48354">#48354</a>)</td>
</tr>
<tr>
<td><a href="">d0145033bd</a></td>
<td>fix</td>
<td>generate forwardRef for same file imports (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48898">#48898</a>)</td>
</tr>
</tbody>
</table>
<h3>migrations</h3>
<table>
<thead>
<tr>
<th>Commit</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="">2796230e95</a></td>
<td>fix</td>
<td>add <code>enum</code> in <code>mode</code> option in <code>standalone</code> schema (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48851">#48851</a>)</td>
</tr>
<tr>
<td><a href="">816e76a578</a></td>
<td>fix</td>
<td>automatically prune root module after bootstrap step (<a href="https://github-redirect.dependabot.com/angular/angular/pull/49030">#49030</a>)</td>
</tr>
<tr>
<td><a href="">bdbf21d04b</a></td>
<td>fix</td>
<td>avoid generating imports with forward slashes (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48993">#48993</a>)</td>
</tr>
<tr>
<td><a href="">32cf4e5cb9</a></td>
<td>fix</td>
<td>avoid internal modules when generating imports (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48958">#48958</a>)</td>
</tr>
<tr>
<td><a href="">521ccfbe6c</a></td>
<td>fix</td>
<td>avoid interrupting the migration if language service lookup fails (<a href="https://github-redirect.dependabot.com/angular/angular/pull/49010">#49010</a>)</td>
</tr>
<tr>
<td><a href="">a40cd47aa7</a></td>
<td>fix</td>
<td>avoid modifying testing modules without declarations (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48921">#48921</a>)</td>
</tr>
<tr>
<td><a href="">1afa6ed322</a></td>
<td>fix</td>
<td>don't add ModuleWithProviders to standalone test components (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48987">#48987</a>)</td>
</tr>
<tr>
<td><a href="">c98c6a8452</a></td>
<td>fix</td>
<td>don't copy animations modules into the imports of test components (<a href="https://github-redirect.dependabot.com/angular/angular/pull/49147">#49147</a>)</td>
</tr>
<tr>
<td><a href="">8389557848</a></td>
<td>fix</td>
<td>don't copy unmigrated declarations into imports array (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48882">#48882</a>)</td>
</tr>
<tr>
<td><a href="">f82bdc4b01</a></td>
<td>fix</td>
<td>don't delete classes that may provide dependencies transitively (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48866">#48866</a>)</td>
</tr>
<tr>
<td><a href="">759db12e0b</a></td>
<td>fix</td>
<td>duplicated comments on migrated classes (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48966">#48966</a>)</td>
</tr>
<tr>
<td><a href="">ba38178d19</a></td>
<td>fix</td>
<td>generate forwardRef for same file imports (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48898">#48898</a>)</td>
</tr>
<tr>
<td><a href="">03fcb36cfd</a></td>
<td>fix</td>
<td>migrate HttpClientModule to provideHttpClient() (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48949">#48949</a>)</td>
</tr>
<tr>
<td><a href="">2de6dae16d</a></td>
<td>fix</td>
<td>migrate RouterModule.forRoot with a config object to use features (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48935">#48935</a>)</td>
</tr>
<tr>
<td><a href="">770191cf1f</a></td>
<td>fix</td>
<td>migrate tests when switching to standalone bootstrap API (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48987">#48987</a>)</td>
</tr>
<tr>
<td><a href="">c7926b5773</a></td>
<td>fix</td>
<td>move standalone migrations into imports (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48987">#48987</a>)</td>
</tr>
<tr>
<td><a href="">65c74ed93e</a></td>
<td>fix</td>
<td>normalize paths to posix (<a href="https://github-redirect.dependabot.com/angular/angular/pull/48850">#48850</a>)</td>
</tr>
</tbody>
</table>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c2bcf0b</code></a> refactor(compiler): Remove strictStyling option for ShadowCss (<a href="">#48824</a>)</li>
<li><a href=""><code>06e161f</code></a> fix(compiler): incorrect code when non-null assertion is used after a safe ac...</li>
<li><a href=""><code>bc8cfa2</code></a> fix(compiler): handle css selectors with space after an escaped character. (#...</li>
<li><a href=""><code>6beff5e</code></a> refactor(compiler): rework and expose APIs to be used in schematics (<a href="">#48730</a>)</li>
<li><a href=""><code>61023b5</code></a> refactor(compiler): refactor the shadow css specs (<a href="">#48443</a>)</li>
<li><a href=""><code>fc1c03e</code></a> refactor(compiler): Remove unnecessary assignment (<a href="">#48478</a>)</li>
<li><a href=""><code>a532d71</code></a> feat(compiler): allow self-closing tags on custom elements (<a href="">#48535</a>)</li>
<li><a href=""><code>a2b9c5c</code></a> build: refactor <code>packages/compiler/test</code> to work with ESM (<a href="">#48521</a>)</li>
<li><a href=""><code>c9415e4</code></a> build: ensure bootstrap transitive runfiles are made available (<a href="">#48521</a>)</li>
<li><a href=""><code>2055150</code></a> build: replace <code>_es2015</code> shorthand with more flexible <code>_files</code> suffix (<a href="">#48521</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/angular/angular/commits/15.2.0/packages/compiler">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@angular/compiler&package-manager=npm_and_yarn&previous-version=14.2.10&new-version=15.2.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3cd282d865c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
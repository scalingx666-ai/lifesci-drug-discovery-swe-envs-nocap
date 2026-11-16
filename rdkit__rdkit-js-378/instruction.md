# Issue

**Title:** Bump typedoc from 0.24.7 to 0.25.0

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.24.7 to 0.25.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.25.0</h2>
<h3>Breaking Changes</h3>
<ul>
<li>Bump minimum Node version to 16.</li>
<li>Removed <code>legacy-packages</code> option for <code>--entryPointStrategy</code>.</li>
<li>Changed default value of <code>--categorizeByGroup</code> to <code>false</code>.</li>
<li>Specifying a link as the <code>gitRemote</code> is no longer supported.</li>
<li>An <code>Application</code> instance must now be retrieved via <code>Application.bootstrap</code> or <code>Application.bootstrapWithPlugins</code>, <a href="">#2268</a>.</li>
<li>Removed <code>ReflectionKind.ObjectLiteral</code> that was never used by TypeDoc.</li>
<li>Removed deprecated members <code>DefaultThemeRenderContext.comment</code> and <code>DefaultThemeRenderContext.attemptExternalResolution</code>.</li>
</ul>
<h3>Features</h3>
<ul>
<li>Added support for TypeScript 5.2</li>
<li>TypeDoc config files now support options default-exported from an ESM config file, <a href="">#2268</a>.</li>
<li>TypeDoc config files may now export a promise containing configuration, <a href="">#2268</a>.</li>
<li>Added <code>--preserveLinkText</code> option (defaults to true) which determines whether the reflection name or full link text is included
in the output when no override is specified, <a href="">#2355</a>.</li>
<li>Added a no-results placeholder when no search results are available, <a href="">#2347</a>.</li>
<li>Implemented several miscellaneous performance improvements to generate docs faster, this took the time to generate TypeDoc's
site from ~5.6 seconds to ~5.4 seconds.</li>
<li>Added <code>--disableGit</code> option to prevent TypeDoc from using Git to try to determine if sources can be linked, <a href="">#2326</a>.</li>
<li>Added support for tags <code>@showGroups</code>, <code>@hideGroups</code>, <code>@showCategories</code>, <code>@hideCategories</code> to configure the navigation pane on a
per-reflection basis, <a href="">#2329</a>.</li>
<li>With <code>--jsDocCompatibility.defaultTags</code> set, <code>@defaultValue</code> is now implicitly a code block if the text contains no code, <a href="">#2370</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Fixed link discovery if nested (<code>Foo#bar</code>) links were used and <code>--useTsLinkResolution</code> is enabled in some cases, <a href="">#2360</a>.</li>
<li>Links with invalid declaration references will no longer silently link to the wrong page in some cases, <a href="">#2360</a>.</li>
<li>Fixed duplicate definitions in type hierarchy when using packages mode, <a href="">#2327</a>.</li>
<li><code>@inheritDoc</code> was not properly resolved across packages in packages mode, <a href="">#2331</a>.</li>
<li>Added warning for attempted <code>@interface</code> use on union types, <a href="">#2352</a>.</li>
<li>Fixed misleading type annotation on <code>Theme.getUrls</code>, <a href="">#2318</a>.</li>
<li>Fixed duplicate namespace in documentation if <code>@namespace</code> is used on a variable with an associated namespace, <a href="">#2364</a>.</li>
<li>Fixed <code>@namespace</code> property discovery if merged with a type and the type was declared first <a href="">#2364</a>.</li>
<li>Tables in markdown are now styled, <a href="">#2366</a>.</li>
<li>Sidebar links no longer open in a new tab, <a href="">#2353</a>.</li>
<li>Headers now include some padding before rendering text, <a href="">#2316</a>.</li>
<li>Symbol locations for signatures on <code>reflection.sources</code> now considers the node's name like non-signature location discovery does.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/camc314"><code>@​camc314</code></a></li>
<li><a href="https://github.com/cprussin"><code>@​cprussin</code></a></li>
<li><a href="https://github.com/roggervalf"><code>@​roggervalf</code></a></li>
<li><a href="https://github.com/Th3S4mur41"><code>@​Th3S4mur41</code></a></li>
</ul>
<h2>v0.24.8</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h1>v0.25.0 (2023-08-25)</h1>
<h3>Breaking Changes</h3>
<ul>
<li>Bump minimum Node version to 16.</li>
<li>Removed <code>legacy-packages</code> option for <code>--entryPointStrategy</code>.</li>
<li>Changed default value of <code>--categorizeByGroup</code> to <code>false</code>.</li>
<li>Specifying a link as the <code>gitRemote</code> is no longer supported.</li>
<li>An <code>Application</code> instance must now be retrieved via <code>Application.bootstrap</code> or <code>Application.bootstrapWithPlugins</code>, <a href="">#2268</a>.</li>
<li>Removed <code>ReflectionKind.ObjectLiteral</code> that was never used by TypeDoc.</li>
<li>Removed deprecated members <code>DefaultThemeRenderContext.comment</code> and <code>DefaultThemeRenderContext.attemptExternalResolution</code>.</li>
</ul>
<h3>Features</h3>
<ul>
<li>Added support for TypeScript 5.2, <a href="">#2373</a>.</li>
<li>TypeDoc config files now support options default-exported from an ESM config file, <a href="">#2268</a>.</li>
<li>TypeDoc config files may now export a promise containing configuration, <a href="">#2268</a>.</li>
<li>Added <code>--preserveLinkText</code> option (defaults to true) which determines whether the reflection name or full link text is included
in the output when no override is specified, <a href="">#2355</a>.</li>
<li>Added a no-results placeholder when no search results are available, <a href="">#2347</a>.</li>
<li>Implemented several miscellaneous performance improvements to generate docs faster, this took the time to generate TypeDoc's
site from ~5.6 seconds to ~5.4 seconds.</li>
<li>Added <code>--disableGit</code> option to prevent TypeDoc from using Git to try to determine if sources can be linked, <a href="">#2326</a>.</li>
<li>Added support for tags <code>@showGroups</code>, <code>@hideGroups</code>, <code>@showCategories</code>, <code>@hideCategories</code> to configure the navigation pane on a
per-reflection basis, <a href="">#2329</a>.</li>
<li>With <code>--jsDocCompatibility.defaultTags</code> set, <code>@defaultValue</code> is now implicitly a code block if the text contains no code, <a href="">#2370</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Fixed link discovery if nested (<code>Foo#bar</code>) links were used and <code>--useTsLinkResolution</code> is enabled in some cases, <a href="">#2360</a>.</li>
<li>Links with invalid declaration references will no longer silently link to the wrong page in some cases, <a href="">#2360</a>.</li>
<li>Fixed duplicate definitions in type hierarchy when using packages mode, <a href="">#2327</a>.</li>
<li><code>@inheritDoc</code> was not properly resolved across packages in packages mode, <a href="">#2331</a>.</li>
<li>Added warning for attempted <code>@interface</code> use on union types, <a href="">#2352</a>.</li>
<li>Fixed misleading type annotation on <code>Theme.getUrls</code>, <a href="">#2318</a>.</li>
<li>Fixed duplicate namespace in documentation if <code>@namespace</code> is used on a variable with an associated namespace, <a href="">#2364</a>.</li>
<li>Fixed <code>@namespace</code> property discovery if merged with a type and the type was declared first <a href="">#2364</a>.</li>
<li>Tables in markdown are now styled, <a href="">#2366</a>.</li>
<li>Sidebar links no longer open in a new tab, <a href="">#2353</a>.</li>
<li>Headers now include some padding before rendering text, <a href="">#2316</a>.</li>
<li>Symbol locations for signatures on <code>reflection.sources</code> now considers the node's name like non-signature location discovery does.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/camc314"><code>@​camc314</code></a></li>
<li><a href="https://github.com/cprussin"><code>@​cprussin</code></a></li>
<li><a href="https://github.com/roggervalf"><code>@​roggervalf</code></a></li>
<li><a href="https://github.com/Th3S4mur41"><code>@​Th3S4mur41</code></a></li>
</ul>
<h2>v0.24.8 (2023-06-04)</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>8d822e9</code></a> Update changelog for release</li>
<li><a href=""><code>fc6f648</code></a> Bump version to 0.25.0</li>
<li><a href=""><code>d4db571</code></a> Add preserveLinkText option</li>
<li><a href=""><code>3d8ff29</code></a> defaultValue is implicitly code only with JSDoc compat</li>
<li><a href=""><code>028a141</code></a> feat(default-value): treat as code block for better styling (<a href="">#2370</a>)</li>
<li><a href=""><code>c83f2c3</code></a> Add support for TS 5.2</li>
<li><a href=""><code>5c977ae</code></a> Support ESM config files</li>
<li><a href=""><code>76c918c</code></a> Headers now include some padding before rendering text</li>
<li><a href=""><code>0cc6e58</code></a> Sidebar links no longer open in a new tab, closes <a href="">#2353</a>.</li>
<li><a href=""><code>3207ae5</code></a> Lint</li>
<li>Additional commits viewable in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.24.7...v0.25.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.24.7&new-version=0.25.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
# Issue

**Title:** Bump typedoc from 0.23.26 to 0.24.6

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.23.26 to 0.24.6.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.24.6</h2>
<h3>Features</h3>
<ul>
<li>Improved error messaging if a provided entry point could not be converted into a documented module reflection, <a href="">#2242</a>.</li>
<li>API: Added support for <code>g</code>, <code>circle</code>, <code>ellipse</code>, <code>polygon</code>, and <code>polyline</code> svg elements, <a href="">#2259</a>.</li>
<li>Extended <code>jsDocCompatibility</code> option with <code>inheritDocTag</code> to ignore fully lowercase <code>inheritDoc</code> tags and
<code>ignoreUnescapedBraces</code> to disable warnings about unescaped <code>{</code> and <code>}</code> characters in comments.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li><code>--useTsLinkResolution</code> is no longer ignored within block tags, <a href="">#2260</a>.</li>
<li>The current namespace will also be expanded in the navigation on page load, <a href="">#2260</a>.</li>
<li>Fixed flicker of navigation pane when reloading a page caused by updating expansion state after the page was loaded.</li>
<li>Fixed an infinite loop if more than one entry point was provided, and all entry points were the same.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/FlippieCoetser"><code>@​FlippieCoetser</code></a></li>
</ul>
<h2>v0.24.5</h2>
<h3>Features</h3>
<ul>
<li>Categories and groups can now be shown in the navigation, added <code>--navigation.includeCategories</code>
and <code>--navigation.includeGroups</code> to control this behavior. The <code>--categorizeByGroup</code> option also
effects this behavior. If <code>categorizeByGroup</code> is set (the default) and <code>navigation.includeGroups</code> is
<em>not</em> set, the value of <code>navigation.includeCategories</code> will be effectively ignored since categories
will be created only within groups, <a href="">#1532</a>.</li>
<li>Added support for discovering a &quot;module&quot; comment on global files, <a href="">#2165</a>.</li>
<li>Added copy code to clipboard button, <a href="">#2153</a>.</li>
<li>Function <code>@returns</code> blocks will now be rendered with the return type, <a href="">#2180</a>.</li>
<li>Added <code>--groupOrder</code> option to specify the sort order of groups, <a href="">#2251</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Type parameter constraints now respect the <code>--hideParameterTypesInTitle</code> option, <a href="">#2226</a>.</li>
<li>Even more contrast fixes, <a href="">#2248</a>.</li>
<li>Fix semantic highlighting for predicate type's parameter references, <a href="">#2249</a>.</li>
<li>Fixed broken links to heading titles.</li>
<li>Fixed inconsistent styling between type parameter lists and parameter lists.</li>
<li>TypeDoc will now warn if more than one <code>@returns</code> block is is present in a function, and ignore the duplicate blocks as specified by TSDoc.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/FlippieCoetser"><code>@​FlippieCoetser</code></a></li>
</ul>
<h2>v0.24.4</h2>
<h3>Bug Fixes</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.24.6 (2023-04-24)</h2>
<h3>Features</h3>
<ul>
<li>Improved error messaging if a provided entry point could not be converted into a documented module reflection, <a href="">#2242</a>.</li>
<li>API: Added support for <code>g</code>, <code>circle</code>, <code>ellipse</code>, <code>polygon</code>, and <code>polyline</code> svg elements, <a href="">#2259</a>.</li>
<li>Extended <code>jsDocCompatibility</code> option with <code>inheritDocTag</code> to ignore fully lowercase <code>inheritDoc</code> tags and
<code>ignoreUnescapedBraces</code> to disable warnings about unescaped <code>{</code> and <code>}</code> characters in comments.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li><code>--useTsLinkResolution</code> is no longer ignored within block tags, <a href="">#2260</a>.</li>
<li>The current namespace will also be expanded in the navigation on page load, <a href="">#2260</a>.</li>
<li>Fixed flicker of navigation pane when reloading a page caused by updating expansion state after the page was loaded.</li>
<li>Fixed an infinite loop if more than one entry point was provided, and all entry points were the same.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/FlippieCoetser"><code>@​FlippieCoetser</code></a></li>
</ul>
<h2>v0.24.5 (2023-04-22)</h2>
<h3>Features</h3>
<ul>
<li>Categories and groups can now be shown in the navigation, added <code>--navigation.includeCategories</code>
and <code>--navigation.includeGroups</code> to control this behavior. The <code>--categorizeByGroup</code> option also
effects this behavior. If <code>categorizeByGroup</code> is set (the default) and <code>navigation.includeGroups</code> is
<em>not</em> set, the value of <code>navigation.includeCategories</code> will be effectively ignored since categories
will be created only within groups, <a href="">#1532</a>.</li>
<li>Added support for discovering a &quot;module&quot; comment on global files, <a href="">#2165</a>.</li>
<li>Added copy code to clipboard button, <a href="">#2153</a>.</li>
<li>Function <code>@returns</code> blocks will now be rendered with the return type, <a href="">#2180</a>.</li>
<li>Added <code>--groupOrder</code> option to specify the sort order of groups, <a href="">#2251</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Type parameter constraints now respect the <code>--hideParameterTypesInTitle</code> option, <a href="">#2226</a>.</li>
<li>Even more contrast fixes, <a href="">#2248</a>.</li>
<li>Fix semantic highlighting for predicate type's parameter references, <a href="">#2249</a>.</li>
<li>Fixed broken links to heading titles.</li>
<li>Fixed inconsistent styling between type parameter lists and parameter lists.</li>
<li>TypeDoc will now warn if more than one <code>@returns</code> block is is present in a function, and ignore the duplicate blocks as specified by TSDoc.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/FlippieCoetser"><code>@​FlippieCoetser</code></a></li>
</ul>
<h2>v0.24.4 (2023-04-16)</h2>
<h3>Bug Fixes</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>af63d9e</code></a> Update changelog for release</li>
<li><a href=""><code>50f8968</code></a> Bump version to 0.24.6</li>
<li><a href=""><code>776f7a7</code></a> Fix useTsLinkResolution in block tags</li>
<li><a href=""><code>08b8348</code></a> Didn't mean to commit that</li>
<li><a href=""><code>e5a6477</code></a> Fix tests</li>
<li><a href=""><code>afb61fa</code></a> Extend jsDocCompatibility with inheritDoc + brace opts</li>
<li><a href=""><code>1e96a2d</code></a> Improve error messaging for missing entry points</li>
<li><a href=""><code>4970a4b</code></a> Suport g, circle, ellipse, polygon, polyline svg elements (<a href="">#2259</a>)</li>
<li><a href=""><code>b49506c</code></a> Fix broken links in changelog</li>
<li><a href=""><code>eeaaf0a</code></a> Update changelog for release</li>
<li>Additional commits viewable in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.23.26...v0.24.6">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.23.26&new-version=0.24.6)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b824d173756`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
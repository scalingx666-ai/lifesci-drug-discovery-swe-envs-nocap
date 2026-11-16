# Issue

**Title:** Bump typedoc from 0.23.10 to 0.23.11

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.23.10 to 0.23.11.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.23.11</h2>
<h3>Features</h3>
<ul>
<li>Added support for TypeScript 4.8.</li>
<li>Introduced a <code>skipErrorChecking</code> option which instructs TypeDoc to not ask TypeScript for compiler errors
before attempting to generate documentation. Turning this on may improve generation speed, but could also
cause a crash if your code contains compiler errors.</li>
<li>Added support for JS entry points when using packages mode, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2037">#2037</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Fixed crash when converting abstract mixin class, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2011">#2011</a>.</li>
<li>Readme files within monorepos now have <code>@link</code> tags resolved, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2029">#2029</a>.</li>
<li>Correctly resolve unqualified links to class members within parameters, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2031">#2031</a>.</li>
<li>TypeDoc will now consider other reflections with the same name as parents when resolving links, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2033">#2033</a>.</li>
<li>The &quot;Hierarchy&quot; and &quot;Type Parameters&quot; helpers on <code>DefaultThemeRenderContext</code> now contain all the HTML for their sections of the page, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2038">#2038</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/citkane"><code>@​citkane</code></a></li>
<li><a href="https://github.com/kaphula"><code>@​kaphula</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.23.11 (2022-08-26)</h2>
<h3>Features</h3>
<ul>
<li>Added support for TypeScript 4.8.</li>
<li>Introduced a <code>skipErrorChecking</code> option which instructs TypeDoc to not ask TypeScript for compiler errors
before attempting to generate documentation. Turning this on may improve generation speed, but could also
cause a crash if your code contains compiler errors.</li>
<li>Added support for JS entry points when using packages mode, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2037">#2037</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Fixed crash when converting abstract mixin class, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2011">#2011</a>.</li>
<li>Readme files within monorepos now have <code>@link</code> tags resolved, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2029">#2029</a>.</li>
<li>Correctly resolve unqualified links to class members within parameters, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2031">#2031</a>.</li>
<li>TypeDoc will now consider other reflections with the same name as parents when resolving links, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2033">#2033</a>.</li>
<li>The &quot;Hierarchy&quot; and &quot;Type Parameters&quot; helpers on <code>DefaultThemeRenderContext</code> now contain all the HTML for their sections of the page, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2038">#2038</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/citkane"><code>@​citkane</code></a></li>
<li><a href="https://github.com/kaphula"><code>@​kaphula</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>722351d</code></a> Update changelog for release</li>
<li><a href=""><code>94e996a</code></a> Release 0.23.11</li>
<li><a href=""><code>8346adb</code></a> Fix crash when converting abstract mixins</li>
<li><a href=""><code>0904477</code></a> Add support for JS entry points in packages mode</li>
<li><a href=""><code>25582a7</code></a> Update changelog</li>
<li><a href=""><code>d02a980</code></a> Merge remote-tracking branch 'origin/skip-error-checking'</li>
<li><a href=""><code>e9c3181</code></a> Remove default template headers of Hierarchy and Type Parameters from Default...</li>
<li><a href=""><code>08759bf</code></a> Add support for TypeScript 4.8</li>
<li><a href=""><code>c8028d1</code></a> Improve warning for multiple loads</li>
<li><a href=""><code>ae459f8</code></a> Check declaration merged reflections</li>
<li>Additional commits viewable in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.23.10...v0.23.11">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.23.10&new-version=0.23.11)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dbe94b216c58`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
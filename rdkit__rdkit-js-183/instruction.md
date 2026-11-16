# Issue

**Title:** Bump typedoc from 0.23.13 to 0.23.14

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.23.13 to 0.23.14.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.23.14</h2>
<h3>Features</h3>
<ul>
<li>Added support for defining one-off external link mappings with <code>externalSymbolLinkMappings</code> see
<a href="https://typedoc.org/guides/options/#externalsymbollinkmappings">the documentation</a> for usage examples and caveats, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2030">#2030</a>.</li>
<li>External link resolvers defined with <code>addUnknownSymbolResolver</code> will now be checked when resolving <code>@link</code> tags, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2030">#2030</a>.
Note: To support this, resolution will now happen during conversion, and as such, <code>Renderer.addUnknownSymbolResolver</code> has been
soft deprecated in favor of <code>Converter.addUnknownSymbolResolver</code>. Plugins should update to use the method on <code>Converter</code>.
<code>DefaultThemeRenderContext.attemptExternalResolution</code> has also been deprecated since it will repeat work done during conversion,
use <code>ReferenceType.externalUrl</code> instead.</li>
<li>Added <code>Converter.addUnknownSymbolResolver</code> for use by plugins supporting external links.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Fixed conversion of object literal types containing construct signatures, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2036">#2036</a>.</li>
<li>Fixed centering of title bar on wide displays, actually this time, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2046">#2046</a>.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.23.14 (2022-09-03)</h2>
<h3>Features</h3>
<ul>
<li>Added support for defining one-off external link mappings with <code>externalSymbolLinkMappings</code> see
<a href="https://typedoc.org/guides/options/#externalsymbollinkmappings">the documentation</a> for usage examples and caveats, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2030">#2030</a>.</li>
<li>External link resolvers defined with <code>addUnknownSymbolResolver</code> will now be checked when resolving <code>@link</code> tags, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2030">#2030</a>.
Note: To support this, resolution will now happen during conversion, and as such, <code>Renderer.addUnknownSymbolResolver</code> has been
soft deprecated in favor of <code>Converter.addUnknownSymbolResolver</code>. Plugins should update to use the method on <code>Converter</code>.
<code>DefaultThemeRenderContext.attemptExternalResolution</code> has also been deprecated since it will repeat work done during conversion,
use <code>ReferenceType.externalUrl</code> instead.</li>
<li>Added <code>Converter.addUnknownSymbolResolver</code> for use by plugins supporting external links.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Fixed conversion of object literal types containing construct signatures, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2036">#2036</a>.</li>
<li>Fixed centering of title bar on wide displays, actually this time, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2046">#2046</a>.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>71fb913</code></a> Update changelog for release</li>
<li><a href=""><code>49d4025</code></a> Bump version to 0.23.14</li>
<li><a href=""><code>990a794</code></a> Remove dead method</li>
<li><a href=""><code>d27a719</code></a> Add support for externalSymbolLinkMappings</li>
<li><a href=""><code>3872463</code></a> Add support for external resolution on <code>@link</code> tags</li>
<li><a href=""><code>02ec72b</code></a> Fix conversion of object literals with construct signatures</li>
<li><a href=""><code>e50d7bf</code></a> Upgrade <code>@types</code> package</li>
<li><a href=""><code>c72c75c</code></a> Fix centering of title bar</li>
<li>See full diff in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.23.13...v0.23.14">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.23.13&new-version=0.23.14)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
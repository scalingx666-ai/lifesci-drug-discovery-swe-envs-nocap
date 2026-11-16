# Issue

**Title:** Bump typedoc from 0.25.0 to 0.25.1

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.25.0 to 0.25.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.25.1</h2>
<h3>Features</h3>
<ul>
<li>Added <code>stripYamlFrontmatter</code> config option to remove YAML frontmatter from README.md, <a href="">#2381</a>.</li>
<li>Added <code>--excludeCategories</code> config option to remove reflections present in any excluded category, <a href="">#1407</a>.</li>
<li>If no tsconfig.json file is present, TypeDoc will now attempt to compile without setting any compiler options, <a href="">#2304</a>.</li>
<li>Navigation is now written to a JS file and built dynamically, which significantly decreases document generation time
with large projects and also provides large space benefits. Themes may now override <code>DefaultTheme.buildNavigation</code>
to customize the displayed navigation tree, <a href="">#2287</a>.
Note: This change renders <code>navigation.fullTree</code> obsolete. If you set it, TypeDoc will warn that it is being ignored.
It will be removed in v0.26.</li>
<li>The search index is now compressed before writing, which reduces most search index sizes by ~5-10x.</li>
<li>TypeDoc will now attempt to cache icons when <code>DefaultThemeRenderContext.icons</code> is overwritten by a custom theme.
Note: To perform this optimization, TypeDoc relies on <code>DefaultThemeRenderContext.iconCache</code> being rendered within
each page. TypeDoc does it in the <code>defaultLayout</code> template.</li>
<li>Cache URL derivation during generation, <a href="">#2386</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li><code>@property</code> now works as expected if used to override a method's documentation.</li>
<li>Deprecated functions/methods are now correctly rendered with a struck-out name.</li>
<li><code>--watch</code> mode works again, <a href="">#2378</a>.</li>
<li>Improved support for optional names within JSDoc types, <a href="">#2384</a>.</li>
<li>Fixed duplicate rendering of reflection flags on signature parameters, <a href="">#2385</a>.</li>
<li>TypeDoc now handles the <code>intrinsic</code> keyword if TS intrinsic types are included in documentation.</li>
<li><code>--exclude</code> is now respected when expanding globs in entry points, <a href="">#2376</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/ajesshope"><code>@​ajesshope</code></a></li>
<li><a href="https://github.com/HemalPatil"><code>@​HemalPatil</code></a></li>
<li><a href="https://github.com/hrueger"><code>@​hrueger</code></a></li>
<li><a href="https://github.com/typhonrt"><code>@​typhonrt</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.25.1 (2023-09-04)</h2>
<h3>Features</h3>
<ul>
<li>Added <code>stripYamlFrontmatter</code> config option to remove YAML frontmatter from README.md, <a href="">#2381</a>.</li>
<li>Added <code>--excludeCategories</code> config option to remove reflections present in any excluded category, <a href="">#1407</a>.</li>
<li>If no tsconfig.json file is present, TypeDoc will now attempt to compile without setting any compiler options, <a href="">#2304</a>.</li>
<li>Navigation is now written to a JS file and built dynamically, which significantly decreases document generation time
with large projects and also provides large space benefits. Themes may now override <code>DefaultTheme.buildNavigation</code>
to customize the displayed navigation tree, <a href="">#2287</a>.
Note: This change renders <code>navigation.fullTree</code> obsolete. If you set it, TypeDoc will warn that it is being ignored.
It will be removed in v0.26.</li>
<li>The search index is now compressed before writing, which reduces most search index sizes by ~5-10x.</li>
<li>TypeDoc will now attempt to cache icons when <code>DefaultThemeRenderContext.icons</code> is overwritten by a custom theme.
Note: To perform this optimization, TypeDoc relies on <code>DefaultThemeRenderContext.iconCache</code> being rendered within
each page. TypeDoc does it in the <code>defaultLayout</code> template.</li>
<li>Cache URL derivation during generation, <a href="">#2386</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li><code>@property</code> now works as expected if used to override a method's documentation.</li>
<li>Deprecated functions/methods are now correctly rendered with a struck-out name.</li>
<li><code>--watch</code> mode works again, <a href="">#2378</a>.</li>
<li>Improved support for optional names within JSDoc types, <a href="">#2384</a>.</li>
<li>Fixed duplicate rendering of reflection flags on signature parameters, <a href="">#2385</a>.</li>
<li>TypeDoc now handles the <code>intrinsic</code> keyword if TS intrinsic types are included in documentation.</li>
<li><code>--exclude</code> is now respected when expanding globs in entry points, <a href="">#2376</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/ajesshope"><code>@​ajesshope</code></a></li>
<li><a href="https://github.com/HemalPatil"><code>@​HemalPatil</code></a></li>
<li><a href="https://github.com/hrueger"><code>@​hrueger</code></a></li>
<li><a href="https://github.com/typhonrt"><code>@​typhonrt</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5e4c79d</code></a> Update changelog for release</li>
<li><a href=""><code>265bf49</code></a> Bump version to 0.25.1</li>
<li><a href=""><code>0985616</code></a> Handle projects without tsconfig files</li>
<li><a href=""><code>bcf3e04</code></a> Add excludeCategories option</li>
<li><a href=""><code>653b281</code></a> Respect --exclude when expanding globs in entry points</li>
<li><a href=""><code>a6823cf</code></a> Cache URL derivation during generation</li>
<li><a href=""><code>1f88a1f</code></a> Compress search index too</li>
<li><a href=""><code>d68ca2a</code></a> Update changelog</li>
<li><a href=""><code>dc4a16d</code></a> feat: <code>stripYamlFrontmatter</code> option (<a href="">#2387</a>)</li>
<li><a href=""><code>67ee6ac</code></a> Dynamically load navigation</li>
<li>Additional commits viewable in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.25.0...v0.25.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.25.0&new-version=0.25.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `658438fb661d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Bump typedoc from 0.23.11 to 0.23.12

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.23.11 to 0.23.12.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.23.12</h2>
<h3>Features</h3>
<ul>
<li>Added a new <code>ParameterType.Object</code> for declaring object options which will be shallowly merged when read from user configuration.</li>
<li>Added a new <code>Application.EVENT_BOOTSTRAP_END</code> event emitted when <code>Application.bootstrap</code> is called.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>TypeDoc will now work properly in packages mode when converting packages outside the current working directory, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2043">#2043</a>.</li>
<li>Fixed deprecation warning for <code>isIdentifierOrPrivateIdentifier</code>.</li>
<li>Fixed centering of title bar on wide displays, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2046">#2046</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/citkane"><code>@​citkane</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.23.12 (2022-08-31)</h2>
<h3>Features</h3>
<ul>
<li>Added a new <code>ParameterType.Object</code> for declaring object options which will be shallowly merged when read from user configuration.</li>
<li>Added a new <code>Application.EVENT_BOOTSTRAP_END</code> event emitted when <code>Application.bootstrap</code> is called.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>TypeDoc will now work properly in packages mode when converting packages outside the current working directory, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2043">#2043</a>.</li>
<li>Fixed deprecation warning for <code>isIdentifierOrPrivateIdentifier</code>.</li>
<li>Fixed centering of title bar on wide displays, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2046">#2046</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/citkane"><code>@​citkane</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c265735</code></a> Update changelog for release</li>
<li><a href=""><code>10a8916</code></a> Bump version to 0.23.12</li>
<li><a href=""><code>604585d</code></a> Update changelog for bootstrap event, tweaks</li>
<li><a href=""><code>f4345a6</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2040">#2040</a> from <a href="https://github-redirect.dependabot.com/citkane/issue/issues/2024">citkane/issue#2024</a></li>
<li><a href=""><code>9443d98</code></a> Fix centering of title bar</li>
<li><a href=""><code>877e1a7</code></a> Fix packages outside cwd</li>
<li><a href=""><code>a3acebd</code></a> Add tests for issue <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2024">#2024</a></li>
<li><a href=""><code>e19e4d8</code></a> Modify declaration types to allow for new <code>ObjectDeclarationOption</code> type</li>
<li><a href=""><code>d7f5a2e</code></a> Add a new <code>oldValue</code> function param to the application flow</li>
<li><a href=""><code>fa012f0</code></a> Create ParameterType.Object</li>
<li>Additional commits viewable in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.23.11...v0.23.12">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.23.11&new-version=0.23.12)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d97869a3c375`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Bump typedoc from 0.23.15 to 0.23.16

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.23.15 to 0.23.16.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.23.16</h2>
<h3>Features</h3>
<ul>
<li>Object types will now be pretty printed, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/1793">#1793</a>.</li>
<li>Added support for specifying the tsconfig.json file in packages mode with <code>{ &quot;typedoc&quot;: { &quot;tsconfig&quot;: &quot;tsconfig.lib.json&quot; }}</code> in package.json, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2061">#2061</a>.</li>
<li>In packages mode, readme files will now be automatically included if present, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2065">#2065</a>.</li>
<li>Added support for specifying the base file url for links to source code, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2068">#2068</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Private parameter properties will no longer be ignored, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2064">#2064</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/captainTorch"><code>@​captainTorch</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.23.16 (2022-10-10)</h2>
<h3>Features</h3>
<ul>
<li>Object types will now be pretty printed, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/1793">#1793</a>.</li>
<li>Added support for specifying the tsconfig.json file in packages mode with <code>{ &quot;typedoc&quot;: { &quot;tsconfig&quot;: &quot;tsconfig.lib.json&quot; }}</code> in package.json, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2061">#2061</a>.</li>
<li>In packages mode, readme files will now be automatically included if present, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2065">#2065</a>.</li>
<li>Added support for specifying the base file url for links to source code, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2068">#2068</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Private parameter properties will no longer be ignored, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2064">#2064</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/captainTorch"><code>@​captainTorch</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>2e8af77</code></a> Update changelog for release</li>
<li><a href=""><code>b653548</code></a> Bump version to 0.23.16</li>
<li><a href=""><code>6d09ebb</code></a> Experiment: Update actions versions</li>
<li><a href=""><code>38d1419</code></a> Fix lint</li>
<li><a href=""><code>7a3f521</code></a> Automatically discover readme files in packages mode</li>
<li><a href=""><code>535f3f3</code></a> Move depth to type.tsx, fix some bugs</li>
<li><a href=""><code>96f6e3e</code></a> Merge remote-tracking branch 'captainTorch/pretty-print'</li>
<li><a href=""><code>afd4afb</code></a> Support specifying base url for source code</li>
<li><a href=""><code>9aece44</code></a> Add support for &quot;tsconfig&quot; in monorepo config</li>
<li><a href=""><code>75edb48</code></a> linter warning fix</li>
<li>Additional commits viewable in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.23.15...v0.23.16">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.23.15&new-version=0.23.16)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd09fb0dc731`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
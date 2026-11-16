# Issue

**Title:** Bump tslib from 2.5.2 to 2.6.2

## Description

Bumps [tslib](https://github.com/Microsoft/tslib) from 2.5.2 to 2.6.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/Microsoft/tslib/releases">tslib's releases</a>.</em></p>
<blockquote>
<h2>tslib 2.6.2</h2>
<h2>What's Changed</h2>
<ul>
<li>Fix path to <code>exports[&quot;module&quot;][&quot;types&quot;]</code> by <a href="https://github.com/andrewbranch"><code>@​andrewbranch</code></a> in <a href="">microsoft/tslib#217</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/microsoft/tslib/compare/v2.6.1...v2.6.2">https://github.com/microsoft/tslib/compare/v2.6.1...v2.6.2</a></p>
<h2>tslib 2.6.1</h2>
<h2>What's Changed</h2>
<ul>
<li>Allow functions as values in __addDisposableResource by <a href="https://github.com/rbuckton"><code>@​rbuckton</code></a> in <a href="">microsoft/tslib#215</a></li>
<li>Stop using es6 syntax in the es6 file by <a href="https://github.com/andrewbranch"><code>@​andrewbranch</code></a> in <a href="">microsoft/tslib#216</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/microsoft/tslib/compare/2.6.0...v2.6.1">https://github.com/microsoft/tslib/compare/2.6.0...v2.6.1</a></p>
<h2>tslib 2.6.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Add helpers for <code>using</code> and <code>await using</code> by <a href="https://github.com/rbuckton"><code>@​rbuckton</code></a> in <a href="">microsoft/tslib#213</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/microsoft/tslib/compare/v2.5.3...2.6.0">https://github.com/microsoft/tslib/compare/v2.5.3...2.6.0</a></p>
<h2>tslib 2.5.3</h2>
<h2>What's Changed</h2>
<ul>
<li>Do not reference tslib.es6.js from package.json exports by <a href="https://github.com/andrewbranch"><code>@​andrewbranch</code></a> in <a href="">microsoft/tslib#208</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/microsoft/tslib/compare/2.5.2...v2.5.3">https://github.com/microsoft/tslib/compare/2.5.2...v2.5.3</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>49ac8dc</code></a> 2.6.2</li>
<li><a href=""><code>3071b51</code></a> Merge pull request <a href="">#217</a> from microsoft/bug/fix-modules-condition-types-path</li>
<li><a href=""><code>743045e</code></a> Fix path to exports[&quot;module&quot;][&quot;types&quot;]</li>
<li><a href=""><code>41c120d</code></a> 2.6.1</li>
<li><a href=""><code>be55012</code></a> Merge pull request <a href="">#216</a> from microsoft/bug/205</li>
<li><a href=""><code>8d4c782</code></a> Undo format on save</li>
<li><a href=""><code>74f91b3</code></a> Stop using es6 syntax in the es6 file</li>
<li><a href=""><code>1d606f6</code></a> Allow functions as values in __addDisposableResource (<a href="">#215</a>)</li>
<li><a href=""><code>7c7f3ae</code></a> 2.6.0</li>
<li><a href=""><code>f641b05</code></a> Add helpers for <code>using</code> and <code>await using</code> (<a href="">#213</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/Microsoft/tslib/compare/2.5.2...v2.6.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=tslib&package-manager=npm_and_yarn&previous-version=2.5.2&new-version=2.6.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `821e49284651`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
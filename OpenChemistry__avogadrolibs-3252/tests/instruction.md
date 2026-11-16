# Issue

**Title:** Bump jurplel/install-qt-action from 4.4.1 to 4.5.0 in /.github/workflows

## Description

Bumps [jurplel/install-qt-action](https://github.com/jurplel/install-qt-action) from 4.4.1 to 4.5.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/jurplel/install-qt-action/releases">jurplel/install-qt-action's releases</a>.</em></p>
<blockquote>
<h2>install-qt-action v4.5.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Group action output for readability by <a href="https://github.com/pzhlkj6612"><code>@​pzhlkj6612</code></a> in <a href="">jurplel/install-qt-action#378</a></li>
<li>CI: use &quot;npm ci&quot; only; merge steps; name steps; update comments by <a href="https://github.com/pzhlkj6612"><code>@​pzhlkj6612</code></a> in <a href="">jurplel/install-qt-action#379</a></li>
<li>Add more default values for &quot;arch&quot; based on aqtinstall source code; remove the fallback for impossible empty/falsy &quot;arch&quot; before install-qt by <a href="https://github.com/pzhlkj6612"><code>@​pzhlkj6612</code></a> in <a href="">jurplel/install-qt-action#380</a></li>
<li>Add &quot;CONTRIBUTING.md&quot; with example testing workflow by <a href="https://github.com/pzhlkj6612"><code>@​pzhlkj6612</code></a> in <a href="">jurplel/install-qt-action#383</a></li>
<li>Make default Windows Qt to MSVC version mapping orderly by <a href="https://github.com/tooomm"><code>@​tooomm</code></a> in <a href="">jurplel/install-qt-action#382</a></li>
<li>Bump undici from 6.28.0 to 6.29.0 in /action by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">jurplel/install-qt-action#384</a></li>
<li>README: Remove confusing &quot;or&quot; from <code>arch</code> docs; write clear sentences by <a href="https://github.com/tooomm"><code>@​tooomm</code></a> in <a href="">jurplel/install-qt-action#386</a></li>
<li>Bump brace-expansion in /action by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">jurplel/install-qt-action#388</a></li>
<li>Set outputs for current Qt installation; extract details definitively by <a href="https://github.com/pzhlkj6612"><code>@​pzhlkj6612</code></a> in <a href="">jurplel/install-qt-action#381</a></li>
<li>&quot;win64_msvc2022_arm64_cross_compiled&quot; needs parallel desktop install by <a href="https://github.com/pzhlkj6612"><code>@​pzhlkj6612</code></a> in <a href="">jurplel/install-qt-action#393</a></li>
<li>Deprecate &quot;tools-only&quot;; minor docs improvement by <a href="https://github.com/pzhlkj6612"><code>@​pzhlkj6612</code></a> in <a href="">jurplel/install-qt-action#394</a></li>
<li>Mark &quot;tools-only&quot; deprecated everywhere by <a href="https://github.com/pzhlkj6612"><code>@​pzhlkj6612</code></a> in <a href="">jurplel/install-qt-action#395</a></li>
<li>Expose Qt install paths as outputs; remove unused &quot;qtPath&quot;; add logs by <a href="https://github.com/pzhlkj6612"><code>@​pzhlkj6612</code></a> in <a href="">jurplel/install-qt-action#397</a></li>
<li>Warn before installing into an existing Qt directory by <a href="https://github.com/pzhlkj6612"><code>@​pzhlkj6612</code></a> in <a href="">jurplel/install-qt-action#398</a></li>
<li>README: Small tweaks by <a href="https://github.com/tooomm"><code>@​tooomm</code></a> in <a href="">jurplel/install-qt-action#392</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/jurplel/install-qt-action/compare/v4.4.1...v4.5.0">https://github.com/jurplel/install-qt-action/compare/v4.4.1...v4.5.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b344308</code></a> Build v4.5.0 on branch v4</li>
<li><a href=""><code>8a4de44</code></a> Merge pull request <a href="">#392</a></li>
<li><a href=""><code>72579ed</code></a> fix strikethrough</li>
<li><a href=""><code>1505871</code></a> review comments</li>
<li><a href=""><code>d04d3f4</code></a> oversight</li>
<li><a href=""><code>8462fc2</code></a> table formatting, deprecation highlighting</li>
<li><a href=""><code>74e4329</code></a> more section</li>
<li><a href=""><code>026dba1</code></a> shorter upgrade guide link</li>
<li><a href=""><code>c78ce75</code></a> Merge branch 'master' into patch-1</li>
<li><a href=""><code>34f1b11</code></a> Merge pull request <a href="">#398</a></li>
<li>Additional commits viewable in <a href="https://github.com/jurplel/install-qt-action/compare/a9c63c7c123f3069cff414e7e482d95dfa9d8125...b344308e4483fc892e0d27b3cd1b173ebdd95f06">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=jurplel/install-qt-action&package-manager=github_actions&previous-version=4.4.1&new-version=4.5.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d250eb3c62a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
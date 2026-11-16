# Issue

**Title:** deps(deps-dev): bump @semantic-release/exec from 6.0.3 to 7.1.0

## Description

Bumps [@semantic-release/exec](https://github.com/semantic-release/exec) from 6.0.3 to 7.1.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/semantic-release/exec/releases"><code>@​semantic-release/exec</code>'s releases</a>.</em></p>
<blockquote>
<h2>v7.1.0</h2>
<h1><a href="https://github.com/semantic-release/exec/compare/v7.0.3...v7.1.0">7.1.0</a> (2025-05-09)</h1>
<h3>Features</h3>
<ul>
<li><strong>error:</strong> print more useful error for non-process failure (<a href="">#449</a>) (<a href="">a285bc5</a>)</li>
</ul>
<h2>v7.0.3</h2>
<h2><a href="https://github.com/semantic-release/exec/compare/v7.0.2...v7.0.3">7.0.3</a> (2025-02-03)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>deps:</strong> update dependency execa to v9 (<a href="">643e2eb</a>)</li>
</ul>
<h2>v7.0.2</h2>
<h2><a href="https://github.com/semantic-release/exec/compare/v7.0.1...v7.0.2">7.0.2</a> (2025-02-01)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>deps:</strong> update dependency <code>@​semantic-release/error</code> to v4 (<a href="">#353</a>) (<a href="">471f963</a>)</li>
</ul>
<h2>v7.0.1</h2>
<h2><a href="https://github.com/semantic-release/exec/compare/v7.0.0...v7.0.1">7.0.1</a> (2025-02-01)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>deps:</strong> update dependency parse-json to v8 (<a href="">#394</a>) (<a href="">080440f</a>)</li>
</ul>
<h2>v7.0.0</h2>
<h1><a href="https://github.com/semantic-release/exec/compare/v6.0.3...v7.0.0">7.0.0</a> (2025-01-31)</h1>
<h3>Features</h3>
<ul>
<li>ES Module (<a href="">#411</a>) (<a href="">b4462db</a>)</li>
</ul>
<h3>BREAKING CHANGES</h3>
<ul>
<li>
<p>the minimum required version of semantic-release to use <code>@semantic-release/exec</code> is now v24.1.0; the warn logger method/function is now available to use in plugin</p>
</li>
<li>
<p><code>@semantic-release/exec</code> is now a native ES Module. It has named exports for each plugin hook (verifyConditions, analyzeCommits, verifyRelease, generateNotes, prepare, publish, addChannel, success, fail)</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a285bc5</code></a> feat(error): print more useful error for non-process failure (<a href="">#449</a>)</li>
<li><a href=""><code>aa1a2bc</code></a> chore(deps): lock file maintenance (<a href="">#451</a>)</li>
<li><a href=""><code>b0dc7ab</code></a> chore(deps): update dependency ava to v6.3.0 (<a href="">#450</a>)</li>
<li><a href=""><code>93bf408</code></a> chore(deps): lock file maintenance (<a href="">#448</a>)</li>
<li><a href=""><code>0e70c6f</code></a> chore(deps): lock file maintenance (<a href="">#446</a>)</li>
<li><a href=""><code>e643dc3</code></a> ci(action): update actions/setup-node action to v4.4.0 (<a href="">#445</a>)</li>
<li><a href=""><code>a08859e</code></a> chore(deps): lock file maintenance (<a href="">#444</a>)</li>
<li><a href=""><code>da1754e</code></a> chore(deps): lock file maintenance (<a href="">#443</a>)</li>
<li><a href=""><code>72668cc</code></a> chore(deps): lock file maintenance (<a href="">#442</a>)</li>
<li><a href=""><code>3c6a8a9</code></a> chore(deps): update dependency sinon to v20 (<a href="">#441</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/semantic-release/exec/compare/v6.0.3...v7.1.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@semantic-release/exec&package-manager=npm_and_yarn&previous-version=6.0.3&new-version=7.1.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `918e8acc7929`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Bump actions/upload-artifact from 4.4.0 to 4.4.3

## Description

Bumps [actions/upload-artifact](https://github.com/actions/upload-artifact) from 4.4.0 to 4.4.3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/upload-artifact/releases">actions/upload-artifact's releases</a>.</em></p>
<blockquote>
<h2>v4.4.3</h2>
<h2>What's Changed</h2>
<ul>
<li>Undo indirect dependency updates from <a href="">#627</a> by <a href="https://github.com/joshmgross"><code>@​joshmgross</code></a> in <a href="">actions/upload-artifact#632</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/upload-artifact/compare/v4.4.2...v4.4.3">https://github.com/actions/upload-artifact/compare/v4.4.2...v4.4.3</a></p>
<h2>v4.4.2</h2>
<h2>What's Changed</h2>
<ul>
<li>Bump <code>@actions/artifact</code> to 2.1.11 by <a href="https://github.com/robherley"><code>@​robherley</code></a> in <a href="">actions/upload-artifact#627</a>
<ul>
<li>Includes fix for relative symlinks not resolving properly</li>
</ul>
</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/upload-artifact/compare/v4.4.1...v4.4.2">https://github.com/actions/upload-artifact/compare/v4.4.1...v4.4.2</a></p>
<h2>v4.4.1</h2>
<h2>What's Changed</h2>
<ul>
<li>Add a section about hidden files by <a href="https://github.com/joshmgross"><code>@​joshmgross</code></a> in <a href="">actions/upload-artifact#607</a></li>
<li>Add workflow file for publishing releases to immutable action package by <a href="https://github.com/Jcambass"><code>@​Jcambass</code></a> in <a href="">actions/upload-artifact#621</a></li>
<li>Update <code>@​actions/artifact</code> to latest version, includes symlink and timeout fixes by <a href="https://github.com/robherley"><code>@​robherley</code></a> in <a href="">actions/upload-artifact#625</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/Jcambass"><code>@​Jcambass</code></a> made their first contribution in <a href="">actions/upload-artifact#621</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/upload-artifact/compare/v4.4.0...v4.4.1">https://github.com/actions/upload-artifact/compare/v4.4.0...v4.4.1</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b4b15b8</code></a> Merge pull request <a href="">#632</a> from actions/joshmgross/undo-dependency-changes</li>
<li><a href=""><code>92b01eb</code></a> Undo indirect dependency updates from <a href="">#627</a></li>
<li><a href=""><code>8448086</code></a> Merge pull request <a href="">#627</a> from actions/robherley/v4.4.2</li>
<li><a href=""><code>b1d4642</code></a> add explicit relative and absolute symlinks to workflow</li>
<li><a href=""><code>d50e660</code></a> bump version</li>
<li><a href=""><code>aabe6f8</code></a> build with <code>@​actions/artifact</code> v2.1.11</li>
<li><a href=""><code>604373d</code></a> Merge pull request <a href="">#625</a> from actions/robherley/artifact-2.1.10</li>
<li><a href=""><code>0150148</code></a> paste right core version</li>
<li><a href=""><code>a009b25</code></a> update licenses</li>
<li><a href=""><code>9f6f6f4</code></a> update <code>@​actions/core</code> and <code>@​actions/artifact</code> to latest versions</li>
<li>Additional commits viewable in <a href="https://github.com/actions/upload-artifact/compare/50769540e7f4bd5e21e526ee35c689e35e0d6874...b4b15b8c7c6ac21ea08fcf65892d2ee8f75cf882">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=actions/upload-artifact&package-manager=github_actions&previous-version=4.4.0&new-version=4.4.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
Dependabot will merge this PR once CI passes on it, as requested by @DhanshreeA.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5bb48a2f43f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
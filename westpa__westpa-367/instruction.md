# Issue

**Title:** Bump github/codeql-action from 2 to 3

## Description

Bumps [github/codeql-action](https://github.com/github/codeql-action) from 2 to 3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/releases">github/codeql-action's releases</a>.</em></p>
<blockquote>
<h2>CodeQL Bundle v2.15.5</h2>
<p>Bundles CodeQL CLI v2.15.5</p>
<ul>
<li>(<a href="https://github.com/github/codeql-cli-binaries/blob/HEAD/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql-cli-binaries/releases/tag/v2.15.5">release</a>)</li>
</ul>
<p>Includes the following CodeQL language packs from <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5"><code>github/codeql@codeql-cli/v2.15.5</code></a>:</p>
<ul>
<li><code>codeql/cpp-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/cpp/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/cpp/ql/src">source</a>)</li>
<li><code>codeql/cpp-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/cpp/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/cpp/ql/lib">source</a>)</li>
<li><code>codeql/csharp-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/csharp/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/csharp/ql/src">source</a>)</li>
<li><code>codeql/csharp-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/csharp/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/csharp/ql/lib">source</a>)</li>
<li><code>codeql/go-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/go/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/go/ql/src">source</a>)</li>
<li><code>codeql/go-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/go/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/go/ql/lib">source</a>)</li>
<li><code>codeql/java-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/java/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/java/ql/src">source</a>)</li>
<li><code>codeql/java-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/java/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/java/ql/lib">source</a>)</li>
<li><code>codeql/javascript-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/javascript/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/javascript/ql/src">source</a>)</li>
<li><code>codeql/javascript-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/javascript/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/javascript/ql/lib">source</a>)</li>
<li><code>codeql/python-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/python/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/python/ql/src">source</a>)</li>
<li><code>codeql/python-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/python/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/python/ql/lib">source</a>)</li>
<li><code>codeql/ruby-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/ruby/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/ruby/ql/src">source</a>)</li>
<li><code>codeql/ruby-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/ruby/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/ruby/ql/lib">source</a>)</li>
<li><code>codeql/swift-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/swift/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/swift/ql/src">source</a>)</li>
<li><code>codeql/swift-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/swift/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.5/swift/ql/lib">source</a>)</li>
</ul>
<h2>CodeQL Bundle v2.15.4</h2>
<p>Bundles CodeQL CLI v2.15.4</p>
<ul>
<li>(<a href="https://github.com/github/codeql-cli-binaries/blob/HEAD/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql-cli-binaries/releases/tag/v2.15.4">release</a>)</li>
</ul>
<p>Includes the following CodeQL language packs from <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4"><code>github/codeql@codeql-cli/v2.15.4</code></a>:</p>
<ul>
<li><code>codeql/cpp-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/cpp/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/cpp/ql/src">source</a>)</li>
<li><code>codeql/cpp-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/cpp/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/cpp/ql/lib">source</a>)</li>
<li><code>codeql/csharp-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/csharp/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/csharp/ql/src">source</a>)</li>
<li><code>codeql/csharp-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/csharp/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/csharp/ql/lib">source</a>)</li>
<li><code>codeql/go-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/go/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/go/ql/src">source</a>)</li>
<li><code>codeql/go-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/go/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/go/ql/lib">source</a>)</li>
<li><code>codeql/java-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/java/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/java/ql/src">source</a>)</li>
<li><code>codeql/java-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/java/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/java/ql/lib">source</a>)</li>
<li><code>codeql/javascript-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/javascript/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/javascript/ql/src">source</a>)</li>
<li><code>codeql/javascript-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/javascript/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/javascript/ql/lib">source</a>)</li>
<li><code>codeql/python-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/python/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/python/ql/src">source</a>)</li>
<li><code>codeql/python-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/python/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/python/ql/lib">source</a>)</li>
<li><code>codeql/ruby-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/ruby/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/ruby/ql/src">source</a>)</li>
<li><code>codeql/ruby-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/ruby/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/ruby/ql/lib">source</a>)</li>
<li><code>codeql/swift-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/swift/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/swift/ql/src">source</a>)</li>
<li><code>codeql/swift-all</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/swift/ql/lib/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.4/swift/ql/lib">source</a>)</li>
</ul>
<h2>CodeQL Bundle</h2>
<p>Bundles CodeQL CLI v2.15.3</p>
<ul>
<li>(<a href="https://github.com/github/codeql-cli-binaries/blob/HEAD/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql-cli-binaries/releases/tag/v2.15.3">release</a>)</li>
</ul>
<p>Includes the following CodeQL language packs from <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.3"><code>github/codeql@codeql-cli/v2.15.3</code></a>:</p>
<ul>
<li><code>codeql/cpp-queries</code> (<a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.3/cpp/ql/src/CHANGELOG.md">changelog</a>, <a href="https://github.com/github/codeql/tree/codeql-cli/v2.15.3/cpp/ql/src">source</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/blob/main/CHANGELOG.md">github/codeql-action's changelog</a>.</em></p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e0c2b0a</code></a> change version numbers inside processing function as well</li>
<li><a href=""><code>8e4a6c7</code></a> improve handling of changelog processing for backports</li>
<li><a href=""><code>511f073</code></a> Merge pull request <a href="">#2033</a> from github/dependabot/npm_and_yarn/npm-0a98872b3d</li>
<li><a href=""><code>ebf5a83</code></a> Merge pull request <a href="">#2035</a> from github/mergeback/v3.22.11-to-main-b374143c</li>
<li><a href=""><code>7813bda</code></a> Update checked-in dependencies</li>
<li><a href=""><code>2b2fb6b</code></a> Update changelog and version after v3.22.11</li>
<li><a href=""><code>b374143</code></a> Merge pull request <a href="">#2034</a> from github/update-v3.22.11-64e61baea</li>
<li><a href=""><code>95591ba</code></a> Merge branch 'main' into dependabot/npm_and_yarn/npm-0a98872b3d</li>
<li><a href=""><code>e2b5cc7</code></a> Update changelog for v3.22.11</li>
<li>See full diff in <a href="https://github.com/github/codeql-action/compare/v2...v3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=github/codeql-action&package-manager=github_actions&previous-version=2&new-version=3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37a4ceff3827`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
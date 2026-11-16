# Issue

**Title:** chore(deps-dev): bump minimatch from 10.2.6 to 11.0.8

## Description

Bumps [minimatch](https://github.com/isaacs/minimatch) from 10.2.6 to 11.0.8.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/isaacs/minimatch/releases">minimatch's releases</a>.</em></p>
<blockquote>
<h2>v11.0.7</h2>
<ul>
<li>Quadratic compile time for long wildcard patterns (regression in 11.0.0 <code>mergeRows</code>)</li>
</ul>
<p>Fixes GHSA-cf2h-pxjq-68xw: <a href="https://github.com/isaacs/minimatch/security/advisories/GHSA-cf2h-pxjq-68xw">https://github.com/isaacs/minimatch/security/advisories/GHSA-cf2h-pxjq-68xw</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/isaacs/minimatch/blob/main/changelog.md">minimatch's changelog</a>.</em></p>
<blockquote>
<h1>change log</h1>
<h2>11.0</h2>
<ul>
<li>Match each path portion with <code>Matcher</code> from
<code>@isaacs/nonrecursive-glob-match</code>, in place of a <code>RegExp</code>.
Items in <code>Minimatch.set</code> are now strings, <code>Matcher</code> objects, or
<code>GLOBSTAR</code>.</li>
<li>Remove <code>makeRe()</code>, <code>Minimatch#regexp</code>, and the <code>MMRegExp</code> type.</li>
<li>Remove the <code>AST</code> class.</li>
<li>Remove the <code>maxExtglobRecursion</code> option.</li>
<li>An empty path portion, such as the last one in <code>a/b/</code>, only
matches an empty pattern portion. So <code>a/b/</code> no longer matches
<code>a/b/?(x)</code> or <code>a/b/*(x)</code>, the same as <code>a/b/*</code>.</li>
<li>Add the <code>normalize</code> option, to normalize unicode in the pattern
and in each portion of the tested path.</li>
<li>Remove the <code>debug</code> option and the <code>debug()</code> method.</li>
<li>Remove the <code>matchOne()</code>, <code>slashSplit()</code>, and
<code>levelTwoFileOptimize()</code> methods. They are internal now.</li>
<li>Fix patterns with more than one <code>**</code> and sections of different
lengths between them, such as <code>**/a/b/c/**/d/**</code>, which failed
to match some paths since 10.2.3.</li>
<li>Fix <code>partial</code> matching of patterns with <code>**</code>, which since
10.2.3 matched some paths under a dot portion that <code>**</code> can not
walk, and did not match some paths that end in the pattern's
last portion.</li>
<li><code>partial</code> matching of patterns with many <code>**</code> no longer takes
exponential time.</li>
<li>On Windows, a <code>..</code> no longer removes the drive letter, or the
host and share of a UNC path, at the start of a pattern or (at
optimization level 2) a path. So <code>C:/a/../../x</code> no longer
matches <code>x</code> or <code>/x</code>.</li>
<li>On Windows, compare the host and share of UNC paths like
<code>//host/share/...</code> case-insensitively, the same as drive
letters.</li>
<li>On Windows, long UNC paths like <code>//?/UNC/host/share/...</code> match
<code>//host/share/...</code> and vice versa, the same as <code>//?/c:/...</code> and
<code>c:/...</code>.</li>
<li>At optimization level 2, throw a <code>RangeError</code> if splitting
<code>**/..</code> portions would make more than <code>braceExpandMax</code> patterns,
or add more than 1,000,000 path portions. Before, a short
pattern could take minutes to compile.</li>
<li>At optimization level 2, dedupe patterns without comparing each
pair, so that a large set is deduped in about linear time. Fix
<code>{**/x,x/y}</code>, which was deduped to <code>**/x</code>, so <code>x/y</code> did not
match.</li>
<li>Match a numeric brace range of 100 or more values, such as
<code>{0..999}</code>, as one pattern portion, in place of one pattern for
each value. For a glob walk, this is one directory read, in
place of a stat for each value. <code>hasMagic()</code> is true for these</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>35c928b</code></a> 11.0.8</li>
<li><a href=""><code>9ceff13</code></a> raise a more useful error when faced with excessive extglobs</li>
<li><a href=""><code>784603e</code></a> properly escape escaped braces, leading ! and #</li>
<li><a href=""><code>d70a7bb</code></a> Add item weight to cache</li>
<li><a href=""><code>9880b42</code></a> 11.0.7</li>
<li><a href=""><code>8a26917</code></a> Quadratic compile time for long wildcard patterns (regression in 11.0.0 `merg...</li>
<li><a href=""><code>4362d0b</code></a> 11.0.6</li>
<li><a href=""><code>b63dfb7</code></a> add missing environment setting to oidc release workflow</li>
<li><a href=""><code>fdc1891</code></a> npm pkg fix</li>
<li><a href=""><code>3e5984b</code></a> release with oidc</li>
<li>Additional commits viewable in <a href="https://github.com/isaacs/minimatch/compare/v10.2.6...v11.0.8">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~GitHub%20Actions">GitHub Actions</a>, a new releaser for minimatch since your current version.</p>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=minimatch&package-manager=npm_and_yarn&previous-version=10.2.6&new-version=11.0.8)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/epam/ketcher/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e9e420e853e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
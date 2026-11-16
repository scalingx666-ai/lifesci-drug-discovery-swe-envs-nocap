# Issue

**Title:** chore(deps-dev): bump glob from 13.0.6 to 14.0.2

## Description

Bumps [glob](https://github.com/isaacs/node-glob) from 13.0.6 to 14.0.2.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/isaacs/node-glob/blob/main/changelog.md">glob's changelog</a>.</em></p>
<blockquote>
<h1>changeglob</h1>
<h2>14</h2>
<ul>
<li>Use minimatch 11. Each portion of a pattern with magic is now
matched with a <code>Matcher</code> from <code>@isaacs/nonrecursive-glob-match</code>
in place of a <code>RegExp</code>, so patterns can no longer cause ReDoS.
Matching follows the minimatch 11 changes, which are closer to
Bash in some edge cases.</li>
<li><code>Pattern#pattern()</code> returns a <code>Matcher</code> for a portion with
magic. The <code>MMPattern</code> type is now minimatch's
<code>ParseReturnFiltered</code>, and the new <code>MMMatcher</code> type is the
<code>Matcher</code> part of it.</li>
<li>Rename <code>Pattern#isRegExp()</code> to <code>isMatcher()</code>, and
<code>Processor#testRegExp()</code> to <code>testMatcher()</code>.</li>
<li>Remove the <code>debug</code> option, which minimatch no longer has.</li>
<li>Add the <code>normalize</code> option, to normalize unicode in the pattern
and in the file names that it is matched against.</li>
<li><code>GlobWalker#walk()</code> and <code>walkSync()</code> return arrays in place of
sets, and <code>MatchRecord#entries()</code> is removed.</li>
<li><code>ignore</code> patterns that start with <code>/</code> now start at the same
place as other patterns that start with <code>/</code>: the <code>root</code> option
if set, or else the root of the <code>cwd</code>, such as <code>C:\</code> on
Windows.</li>
<li><code>ignore</code> patterns follow the <code>windowsPathsNoEscape</code> option,
the same as other patterns.</li>
<li>On Windows, patterns that start with a long UNC root like
<code>//?/UNC/host/share/</code> walk that share, the same as
<code>//host/share/</code>.</li>
<li>Faster <code>ignore</code> patterns (about 1.2 to 3 times faster), and
less work for each entry in a walk (about 10% faster sync, and
15% to 30% faster async, for large trees).</li>
<li>Allow <code>const string[]</code> or <code>readonly string[]</code> as <code>ignore</code>
option or <code>pattern</code> argument.</li>
<li>When the <code>signal</code> aborts an async walk, the walk stops. Before,
it rejected, but continued to read directories.</li>
</ul>
<h2>13</h2>
<ul>
<li>Move the CLI program out to a separate package, <code>glob-bin</code>.
Install that if you'd like to continue using glob from the
command line.</li>
</ul>
<h2>12</h2>
<ul>
<li>Remove the unsafe <code>--shell</code> option. The <code>--shell</code> option is now
ONLY supported on known shells where the behavior can be
implemented safely.</li>
</ul>
<h2>11.1</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>93957bf</code></a> 14.0.2</li>
<li><a href=""><code>4682e8c</code></a> fix: do not continue walking after signal abort</li>
<li><a href=""><code>668a669</code></a> 14.0.1</li>
<li><a href=""><code>6ff2314</code></a> allow const/readonly string[] for ignore, patterns</li>
<li><a href=""><code>bbe1e5d</code></a> 14.0.0</li>
<li><a href=""><code>d9586ad</code></a> use actual published deps, not symlinks</li>
<li><a href=""><code>8b16637</code></a> handle long unc forms</li>
<li><a href=""><code>5bcdc65</code></a> extglobs cannot contain /</li>
<li><a href=""><code>d8b40c2</code></a> handle root in platform-independent way, for ignores and patterns</li>
<li><a href=""><code>7d1c45a</code></a> add native fs glob test (todo on failure)</li>
<li>Additional commits viewable in <a href="https://github.com/isaacs/node-glob/compare/v13.0.6...v14.0.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=glob&package-manager=npm_and_yarn&previous-version=13.0.6&new-version=14.0.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dba836985c06`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
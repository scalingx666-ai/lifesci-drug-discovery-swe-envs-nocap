# Issue

**Title:** Bump mypy from 1.20.0 to 2.1.0

## Description

Bumps [mypy](https://github.com/python/mypy) from 1.20.0 to 2.1.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/python/mypy/blob/master/CHANGELOG.md">mypy's changelog</a>.</em></p>
<blockquote>
<h1>Mypy Release Notes</h1>
<h2>Next Release</h2>
<h2>Mypy 2.1</h2>
<p>We’ve just uploaded mypy 2.1.0 to the Python Package Index (<a href="https://pypi.org/project/mypy/">PyPI</a>).
Mypy is a static type checker for Python. This release includes new features, performance
improvements and bug fixes. You can install it as follows:</p>
<pre><code>python3 -m pip install -U mypy
</code></pre>
<p>You can read the full documentation for this release on <a href="http://mypy.readthedocs.io">Read the Docs</a>.</p>
<h3>librt.vecs: Fast Growable Array Type for Mypyc</h3>
<p>The new <code>librt.vecs</code> module provides an efficient growable array type <code>vec</code> that is
optimized for mypyc use. It provides fast, packed arrays with integer and floating point
value types, which can be <strong>several times faster</strong> than <code>list</code>, and tens of times faster
than <code>array.array</code> in code compiled using mypyc. It also supports nested <code>vec</code> objects and
non-value-type items, such as <code>vec[vec[str]]</code>.</p>
<p>Refer to the <a href="https://mypyc.readthedocs.io/en/latest/librt_vecs.html">documentation</a> for
the details.</p>
<p>Contributed by Jukka Lehtosalo.</p>
<h3>librt.random: Fast Pseudo-Random Number Generation</h3>
<p>The new <code>librt.random</code> module provides fast pseudo-random number generation that is
optimized for code compiled using mypyc. It can be 3x to 10x faster than the stdlib
<code>random</code> module in compiled code.</p>
<p>Refer to the <a href="https://mypyc.readthedocs.io/en/latest/librt_random.html">documentation</a> for
the details.</p>
<p>Contributed by Jukka Lehtosalo (PR <a href="">21433</a>).</p>
<h3>Mypyc Improvements</h3>
<ul>
<li>Enable incremental self-compilation (Vaggelis Danias, PR <a href="">21369</a>)</li>
<li>Make compilation order with multiple files consistent (Piotr Sawicki, PR <a href="">21419</a>)</li>
<li>Fix crash on accessing <code>StopAsyncIteration</code> (Piotr Sawicki, PR <a href="">21406</a>)</li>
<li>Fix incremental compilation with <code>separate</code> flag (Vaggelis Danias, PR <a href="">21299</a>)</li>
</ul>
<h3>Fixes to Crashes</h3>
<ul>
<li>Fix crash on partial type with <code>--allow-redefinition</code> and <code>global</code> declaration (Jukka Lehtosalo, PR <a href="">21428</a>)</li>
<li>Fix broken awaitable generator patching (Ivan Levkivskyi, PR <a href="">21435</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c1c336d</code></a> Remove +dev from version</li>
<li><a href=""><code>74df14b</code></a> Add changelog for mypy 2.1 (<a href="">#21464</a>)</li>
<li><a href=""><code>022d9bc</code></a> Revert &quot;TypeForm: Enable by default (<a href="">#21262</a>)&quot;</li>
<li><a href=""><code>8826288</code></a> [mypyc] Document librt.random (<a href="">#21463</a>)</li>
<li><a href=""><code>3f4067b</code></a> Bump librt version to 0.11.0 (<a href="">#21458</a>)</li>
<li><a href=""><code>2b1eb58</code></a> [mypyc] Enable incremental self-compilation (<a href="">#21369</a>)</li>
<li><a href=""><code>8152f4a</code></a> Respect file config comments for stale modules (<a href="">#21444</a>)</li>
<li><a href=""><code>116d60b</code></a> Fix nondeterminism from nonassociativity of overload joins (<a href="">#21455</a>)</li>
<li><a href=""><code>6c4af8e</code></a> Fix function call message change for small number of args (<a href="">#21432</a>)</li>
<li><a href=""><code>4b8fdca</code></a> [mypyc] Add librt.random module (<a href="">#21433</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/python/mypy/compare/v1.20.0...v2.1.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=mypy&package-manager=pip&previous-version=1.20.0&new-version=2.1.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4d9062d2031`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
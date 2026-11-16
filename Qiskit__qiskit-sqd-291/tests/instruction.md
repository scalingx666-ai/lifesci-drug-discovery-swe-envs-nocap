# Issue

**Title:** Bump mypy from 1.19.1 to 1.20.0

## Description

Bumps [mypy](https://github.com/python/mypy) from 1.19.1 to 1.20.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/python/mypy/blob/master/CHANGELOG.md">mypy's changelog</a>.</em></p>
<blockquote>
<h1>Mypy Release Notes</h1>
<h2>Next Release</h2>
<h2>Mypy 1.20</h2>
<p>We’ve just uploaded mypy 1.20.0 to the Python Package Index (<a href="https://pypi.org/project/mypy/">PyPI</a>).
Mypy is a static type checker for Python. This release includes new features, performance
improvements and bug fixes. You can install it as follows:</p>
<pre><code>python3 -m pip install -U mypy
</code></pre>
<p>You can read the full documentation for this release on <a href="http://mypy.readthedocs.io">Read the Docs</a>.</p>
<h3>Planned Changes to Defaults and Flags in Mypy 2.0</h3>
<p>As a reminder, we are planning to enable <code>--local-partial-types</code> by default in mypy 2.0, which
will likely be the next feature release. This will often require at least minor code changes. This
option is implicitly enabled by mypy daemon, so this makes the behavior of daemon and non-daemon
modes consistent.</p>
<p>Note that this release improves the compatibility of <code>--local-partial-types</code> significantly to
make the switch easier (see below for more).</p>
<p>This can also be configured in a mypy configuration file (use <code>False</code> to disable):</p>
<pre><code>local_partial_types = True
</code></pre>
<p>For more information, refer to the
<a href="https://mypy.readthedocs.io/en/stable/command_line.html#cmdoption-mypy-local-partial-types">documentation</a>.</p>
<p>We will also enable <code>--strict-bytes</code> by default in mypy 2.0. This usually requires at most
minor code changes to adopt. For more information, refer to the
<a href="https://mypy.readthedocs.io/en/stable/command_line.html#cmdoption-mypy-strict-bytes">documentation</a>.</p>
<p>Finally, <code>--allow-redefinition-new</code> will be renamed to <code>--allow-redefinition</code>. If you want
to continue using the older <code>--allow-redefinition</code> semantics which are less flexible (e.g.
limited support for conditional redefinitions), you can switch to <code>--allow-redefinition-old</code>,
which is currently supported as an alias to the legacy <code>--allow-redefinition</code> behavior.
To use <code>--allow-redefinition</code> in the upcoming mypy 2.0, you can't use <code>--no-local-partial-types</code>.
For more information, refer to the
<a href="https://mypy.readthedocs.io/en/stable/command_line.html#cmdoption-mypy-allow-redefinition-new">documentation</a>.</p>
<h3>Better Type Narrowing</h3>
<p>Mypy's implementation of narrowing has been substantially reworked. Mypy will now narrow more
aggressively, more consistently, and more correctly. In particular, you are likely to notice new
narrowing behavior in equality expressions (<code>==</code>), containment expressions (<code>in</code>),</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>770d3ca</code></a> Remove +dev from version</li>
<li><a href=""><code>4738ffa</code></a> Changelog updates for 1.20 (<a href="">#21109</a>)</li>
<li><a href=""><code>b4f07a7</code></a> Use 'native-parser' instead of 'native-parse' for optional dependency (<a href="">#21115</a>)</li>
<li><a href=""><code>7bec7b7</code></a> [mypyc] Document librt and librt.base64 (<a href="">#21114</a>)</li>
<li><a href=""><code>c482596</code></a> --allow-redefinition-new is no longer experimental (<a href="">#21110</a>)</li>
<li><a href=""><code>c916ca3</code></a> sdist: include <code>misc/{diff-cache,apply-cache-diff}.py</code> for `mypy/test/test_di...</li>
<li><a href=""><code>b137e4e</code></a> [mypyc] Speed up native-to-native imports within the same group (<a href="">#21101</a>)</li>
<li><a href=""><code>978b711</code></a> [mypyc] Fix range loop variable off-by-one after loop exit (<a href="">#21098</a>)</li>
<li><a href=""><code>67ada30</code></a> [stubtest] Check runtime availability of private types not marked `@type_chec...</li>
<li><a href=""><code>bdef6ef</code></a> librt cache tests: build respecting MYPY_TEST_PREFIX (<a href="">#21097</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/python/mypy/compare/v1.19.1...v1.20.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=mypy&package-manager=pip&previous-version=1.19.1&new-version=1.20.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21a463b4c0b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
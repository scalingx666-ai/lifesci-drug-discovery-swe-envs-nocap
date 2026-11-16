# Issue

**Title:** Bump mypy from 1.18.2 to 1.19.0

## Description

Bumps [mypy](https://github.com/python/mypy) from 1.18.2 to 1.19.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/python/mypy/blob/master/CHANGELOG.md">mypy's changelog</a>.</em></p>
<blockquote>
<h1>Mypy Release Notes</h1>
<h2>Next Release</h2>
<h3>Drop Support for Python 3.9</h3>
<p>Mypy no longer supports running with Python 3.9, which has reached end-of-life.
When running mypy with Python 3.10+, it is still possible to type check code
that needs to support Python 3.9 with the <code>--python-version 3.9</code> argument.
Support for this will be dropped in the first half of 2026!</p>
<p>Contributed by Marc Mueller (PR <a href="">20156</a>).</p>
<h2>Mypy 1.19</h2>
<p>We’ve just uploaded mypy 1.19.0 to the Python Package Index (<a href="https://pypi.org/project/mypy/">PyPI</a>).
Mypy is a static type checker for Python. This release includes new features, performance
improvements and bug fixes. You can install it as follows:</p>
<pre><code>python3 -m pip install -U mypy
</code></pre>
<p>You can read the full documentation for this release on <a href="http://mypy.readthedocs.io">Read the Docs</a>.</p>
<h3>Python 3.9 Support Ending Soon</h3>
<p>This is the last mypy feature release that supports Python 3.9, which reached
end of life in October 2025.</p>
<h3>Performance Improvements</h3>
<ul>
<li>Switch to a more dynamic SCC processing logic (Ivan Levkivskyi, PR <a href="">20053</a>)</li>
<li>Speed up type aliases (Ivan Levkivskyi, PR <a href="">19810</a>)</li>
</ul>
<h3>Fixed‑Format Cache Improvements</h3>
<p>Mypy uses a cache by default to speed up incremental runs by reusing partial results
from earlier runs. Mypy 1.18 added a new binary fixed-format cache representation as
an experimental feature. The feature is no longer experimental, and we are planning
to enable it by default in a future mypy release (possibly 1.20), since it's faster
and uses less space than the original, JSON-based cache format. Use
<code>--fixed-format-cache</code> to enable the fixed-format cache.</p>
<p>Mypy now has an extra dependency on the <code>librt</code> PyPI package, as it's needed for
cache serialization and deserialization.</p>
<p>Mypy ships with a tool to convert fixed-format cache files to the old JSON format.
Example of how to use this:</p>
<pre><code>$ python -m mypy.exportjson .mypy_cache/.../my_module.data.ff
</code></pre>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>0f068c9</code></a> Remove +dev</li>
<li><a href=""><code>6d5cf52</code></a> Various updates to 1.19 changelog (<a href="">#20304</a>)</li>
<li><a href=""><code>3c81308</code></a> Add draft version of 1.19 release notes (<a href="">#20296</a>)</li>
<li><a href=""><code>1999a20</code></a> [mypyc] librt base64: use existing SIMD CPU dispatch by customizing build fla...</li>
<li><a href=""><code>1b94fbb</code></a> [mypyc] Fix vtable pointer with inherited dunder new (<a href="">#20302</a>)</li>
<li><a href=""><code>13369cb</code></a> [mypyc] Fix crash on super in generator (<a href="">#20291</a>)</li>
<li><a href=""><code>a087a58</code></a> Update import map when new modules added (<a href="">#20271</a>)</li>
<li><a href=""><code>35e843c</code></a> [mypyc] Add efficient librt.base64.b64decode (<a href="">#20263</a>)</li>
<li><a href=""><code>094f66d</code></a> [mypyc] Add <strong>repr</strong> to AssignmentTarget subclasses (<a href="">#20258</a>)</li>
<li><a href=""><code>0738db3</code></a> Do not push partial types to the binder (<a href="">#20202</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/python/mypy/compare/v1.18.2...v1.19.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=mypy&package-manager=pip&previous-version=1.18.2&new-version=1.19.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4191e84e962d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
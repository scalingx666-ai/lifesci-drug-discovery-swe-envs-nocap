# Issue

**Title:** Bump pypa/cibuildwheel from 2.21.3 to 2.22.0

## Description

Bumps [pypa/cibuildwheel](https://github.com/pypa/cibuildwheel) from 2.21.3 to 2.22.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/releases">pypa/cibuildwheel's releases</a>.</em></p>
<blockquote>
<h2>Version 2.22.0</h2>
<ul>
<li>🌟 Added a new <code>CIBW_ENABLE</code>/<code>enable</code> feature that replaces <code>CIBW_FREETHREADED_SUPPORT</code>/<code>free-threaded-support</code> and <code>CIBW_PRERELEASE_PYTHONS</code> with a system that supports both. In cibuildwheel 3, this will also include a PyPy setting and the deprecated options will be removed. (<a href="">#2048</a>)</li>
<li>🌟 <a href="https://peps.python.org/pep-0735/">Dependency groups</a> are now supported for tests. Use <code>CIBW_TEST_GROUPS</code>/<code>test-groups</code> to specify groups in <code>[dependency-groups]</code> for testing. (<a href="">#2063</a>)</li>
<li>🌟 Support for the experimental Ubuntu-based ARMv7l manylinux image (<a href="">#2052</a>)</li>
<li>✨ Show a warning when cibuildwheel is run from Python 3.10 or older; cibuildwheel 3.0 will require Python 3.11 or newer as host (<a href="">#2050</a>)</li>
<li>🐛 Fix issue with stderr interfering with checking the docker version (<a href="">#2074</a>)</li>
<li>🛠 Python 3.9 is now used in <code>CIBW_BEFORE_ALL</code>/<code>before-all</code> on linux, replacing 3.8, which is now EoL (<a href="">#2043</a>)</li>
<li>🛠 Error messages for producing a pure-Python wheel are slightly more informative (<a href="">#2044</a>)</li>
<li>🛠 Better error when <code>uname -m</code> fails on ARM (<a href="">#2049</a>)</li>
<li>🛠 Better error when repair fails and docs for abi3audit on Windows (<a href="">#2058</a>)</li>
<li>🛠 Better error when <code>manylinux-interpreters ensure</code> fails (<a href="">#2066</a>)</li>
<li>🛠 Update Pyodide to 0.26.4, and adapt to the unbundled pyodide-build (now 0.29) (<a href="">#2090</a>)</li>
<li>🛠 Now cibuildwheel uses dependency-groups for development dependencies (<a href="">#2064</a>, <a href="">#2085</a>)</li>
<li>📚 Docs updates and tidy ups (<a href="">#2061</a>, <a href="">#2067</a>, <a href="">#2072</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/blob/main/docs/changelog.md">pypa/cibuildwheel's changelog</a>.</em></p>
<blockquote>
<h3>v2.22.0</h3>
<p><em>23 November 2024</em></p>
<ul>
<li>🌟 Added a new <code>CIBW_ENABLE</code>/<code>enable</code> feature that replaces <code>CIBW_FREETHREADED_SUPPORT</code>/<code>free-threaded-support</code> and <code>CIBW_PRERELEASE_PYTHONS</code> with a system that supports both. In cibuildwheel 3, this will also include a PyPy setting and the deprecated options will be removed. (<a href="">#2048</a>)</li>
<li>🌟 <a href="https://peps.python.org/pep-0735/">Dependency groups</a> are now supported for tests. Use <code>CIBW_TEST_GROUPS</code>/<code>test-groups</code> to specify groups in <code>[dependency-groups]</code> for testing. (<a href="">#2063</a>)</li>
<li>🌟 Support for the experimental Ubuntu-based ARMv7l manylinux image (<a href="">#2052</a>)</li>
<li>✨ Show a warning when cibuildwheel is run from Python 3.10 or older; cibuildwheel 3.0 will require Python 3.11 or newer as host (<a href="">#2050</a>)</li>
<li>🐛 Fix issue with stderr interfering with checking the docker version (<a href="">#2074</a>)</li>
<li>🛠 Python 3.9 is now used in <code>CIBW_BEFORE_ALL</code>/<code>before-all</code> on linux, replacing 3.8, which is now EoL (<a href="">#2043</a>)</li>
<li>🛠 Error messages for producing a pure-Python wheel are slightly more informative (<a href="">#2044</a>)</li>
<li>🛠 Better error when <code>uname -m</code> fails on ARM (<a href="">#2049</a>)</li>
<li>🛠 Better error when repair fails and docs for abi3audit on Windows (<a href="">#2058</a>)</li>
<li>🛠 Better error when <code>manylinux-interpreters ensure</code> fails (<a href="">#2066</a>)</li>
<li>🛠 Update Pyodide to 0.26.4, and adapt to the unbundled pyodide-build (now 0.29) (<a href="">#2090</a>)</li>
<li>🛠 Now cibuildwheel uses dependency-groups for development dependencies (<a href="">#2064</a>, <a href="">#2085</a>)</li>
<li>📚 Docs updates and tidy ups (<a href="">#2061</a>, <a href="">#2067</a>, <a href="">#2072</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ee63bf1</code></a> Bump version: v2.22.0</li>
<li><a href=""><code>d3eeba7</code></a> chore: bump Ruff to 0.8.0 (<a href="">#2092</a>)</li>
<li><a href=""><code>109020e</code></a> Updates for Pyodide builds after <code>pyodide-build</code> was unvendored (<a href="">#2090</a>)</li>
<li><a href=""><code>fd99000</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#2087</a>)</li>
<li><a href=""><code>e158f22</code></a> ci: update gitlab for dependency-groups (<a href="">#2089</a>)</li>
<li><a href=""><code>8f21eb1</code></a> chore: use dependency-groups (<a href="">#2064</a>)</li>
<li><a href=""><code>aac31ae</code></a> docs: fix update scripts usage (<a href="">#2067</a>)</li>
<li><a href=""><code>b882b84</code></a> fix: update the macOS image used on Cirrus CI (<a href="">#2085</a>)</li>
<li><a href=""><code>243085f</code></a> [Bot] Update dependencies (<a href="">#2086</a>)</li>
<li><a href=""><code>df6f886</code></a> feat: add manylinux armv7l (<a href="">#2052</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pypa/cibuildwheel/compare/v2.21.3...v2.22.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pypa/cibuildwheel&package-manager=github_actions&previous-version=2.21.3&new-version=2.22.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7bf03d8d245`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
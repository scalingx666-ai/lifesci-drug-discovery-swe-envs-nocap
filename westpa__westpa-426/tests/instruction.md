# Issue

**Title:** Bump pypa/cibuildwheel from 2.17.0 to 2.18.1

## Description

Bumps [pypa/cibuildwheel](https://github.com/pypa/cibuildwheel) from 2.17.0 to 2.18.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/releases">pypa/cibuildwheel's releases</a>.</em></p>
<blockquote>
<h2>v2.18.1</h2>
<ul>
<li>🌟 Add free-threaded Linux and Windows builds for 3.13. New identifiers <code>cp313t-*</code>, new option <code>CIBW_FREE_THREADED_SUPPORT</code>/<code>tool.cibuildwheel.free-threaded-support</code> required to opt-in. <a href="https://cibuildwheel.pypa.io/en/stable/options/#free-threaded-support">See the docs</a> for more information. (<a href="">#1831</a>)</li>
<li>✨ The <code>container-engine</code> is now a build (non-global) option. (<a href="">#1792</a>)</li>
<li>🛠 The build backend for cibuildwheel is now hatchling. (<a href="">#1297</a>)</li>
<li>🛠 Significant improvements and modernization to our noxfile. (<a href="">#1823</a>)</li>
<li>🛠 Use pylint's new GitHub Actions reporter instead of a custom matcher. (<a href="">#1823</a>)</li>
<li>🛠 Unpin virtualenv updates for Python 3.7+ (<a href="">#1830</a>)</li>
<li>🐛 Fix running linux tests from Windows or macOS ARM. (<a href="">#1788</a>)</li>
<li>📚 Fix our documentation build. (<a href="">#1821</a>)</li>
</ul>
<h2>v2.18.0</h2>
<ul>
<li>✨ Adds CPython 3.13 support, under the prerelease flag <a href="https://cibuildwheel.pypa.io/en/stable/options/#prerelease-pythons">CIBW_PRERELEASE_PYTHONS</a>. This version of cibuildwheel uses 3.13.0b1. Free-threading mode is not available yet (<a href="">#1657</a>), waiting on official binaries (planned for beta 2) and pip support.
<em>While CPython is in beta, the ABI can change, so your wheels might not be compatible with the final release. For this reason, we don't recommend distributing wheels until RC1, at which point 3.13 will be available in cibuildwheel without the flag.</em> (<a href="">#1815</a>)</li>
<li>✨ Musllinux now defaults to <code>musllinux_1_2</code>. You can set the older <code>musllinux_1_1</code> via config if needed. (<a href="">#1817</a>)</li>
<li>🛠 No longer pre-seed setuptools/wheel in virtual environments (<a href="">#1819</a>)</li>
<li>🛠 Respect the constraints file when building with pip, matching build (<a href="">#1818</a>)</li>
<li>🛠 Use uv to compile our pinned dependencies, 10x faster and doesn't require special setup (<a href="">#1778</a>)</li>
<li>🐛 Fix an issue with the schema (<a href="">#1788</a>)</li>
<li>📚 Document the new delocate error checking macOS versions (<a href="">#1766</a>)</li>
<li>📚 Document Rust builds (<a href="">#1816</a>)</li>
<li>📚 Speed up our readthedocs builds with uv, 26 seconds -&gt; 6 seconds to install dependencies (<a href="">#1816</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/blob/main/docs/changelog.md">pypa/cibuildwheel's changelog</a>.</em></p>
<blockquote>
<h3>v2.18.1</h3>
<ul>
<li>🌟 Add free-threaded Linux and Windows builds for 3.13. New identifiers <code>cp313t-*</code>, new option <code>CIBW_FREE_THREADED_SUPPORT</code>/<code>tool.cibuildwheel.free-threaded-support</code> required to opt-in. <a href="https://cibuildwheel.pypa.io/en/stable/options/#free-threaded-support">See the docs</a> for more information. (<a href="">#1831</a>)</li>
<li>✨ The <code>container-engine</code> is now a build (non-global) option. (<a href="">#1792</a>)</li>
<li>🛠 The build backend for cibuildwheel is now hatchling. (<a href="">#1297</a>)</li>
<li>🛠 Significant improvements and modernization to our noxfile. (<a href="">#1823</a>)</li>
<li>🛠 Use pylint's new GitHub Actions reporter instead of a custom matcher. (<a href="">#1823</a>)</li>
<li>🛠 Unpin virtualenv updates for Python 3.7+ (<a href="">#1830</a>)</li>
<li>🐛 Fix running linux tests from Windows or macOS ARM. (<a href="">#1788</a>)</li>
<li>📚 Fix our documentation build. (<a href="">#1821</a>)</li>
</ul>
<h3>v2.18.0</h3>
<p><em>12 May 2024</em></p>
<ul>
<li>
<p>✨ Adds CPython 3.13 support, under the prerelease flag <a href="https://cibuildwheel.pypa.io/en/stable/options/#prerelease-pythons">CIBW_PRERELEASE_PYTHONS</a>. This version of cibuildwheel uses 3.13.0b1. Free-threading mode is not available yet (<a href="">#1657</a>), waiting on official binaries (planned for beta 2) and pip support.</p>
<p><em>While CPython is in beta, the ABI can change, so your wheels might not be compatible with the final release. For this reason, we don't recommend distributing wheels until RC1, at which point 3.13 will be available in cibuildwheel without the flag.</em> (<a href="">#1815</a>)</p>
</li>
<li>
<p>✨ Musllinux now defaults to <code>musllinux_1_2</code>. You can set the older <code>musllinux_1_1</code> via config if needed. (<a href="">#1817</a>)</p>
</li>
<li>
<p>🛠 No longer pre-seed setuptools/wheel in virtual environments (<a href="">#1819</a>)</p>
</li>
<li>
<p>🛠 Respect the constraints file when building with pip, matching build (<a href="">#1818</a>)</p>
</li>
<li>
<p>🛠 Use uv to compile our pinned dependencies, 10x faster and doesn't require special setup (<a href="">#1778</a>)</p>
</li>
<li>
<p>🐛 Fix an issue with the schema (<a href="">#1788</a>)</p>
</li>
<li>
<p>📚 Document the new delocate error checking macOS versions (<a href="">#1766</a>)</p>
</li>
<li>
<p>📚 Document Rust builds (<a href="">#1816</a>)</p>
</li>
<li>
<p>📚 Speed up our readthedocs builds with uv, 26 seconds -&gt; 6 seconds to install dependencies (<a href="">#1816</a>)</p>
</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ba8be0d</code></a> Bump version: v2.18.1</li>
<li><a href=""><code>90dd476</code></a> doc: add documentation for the <code>CIBW_FREE_THREADED_SUPPORT</code> option</li>
<li><a href=""><code>b613249</code></a> chore: pass a PythonConfiguration to install_cpython</li>
<li><a href=""><code>3992d57</code></a> feat: add option to opt-in free-threaded builds</li>
<li><a href=""><code>345467c</code></a> feat: add support for free-threaded (no-gil) Python 3.13</li>
<li><a href=""><code>791e41c</code></a> [Bot] Update dependencies (<a href="">#1832</a>)</li>
<li><a href=""><code>9d5f5e6</code></a> Make <code>container-engine</code> a build (non-global) option (<a href="">#1792</a>)</li>
<li><a href=""><code>1b354cf</code></a> chore: move to hatchling (<a href="">#1297</a>)</li>
<li><a href=""><code>d1a4c9c</code></a> chore: un-pin virtualenv update (<a href="">#1830</a>)</li>
<li><a href=""><code>78bca57</code></a> fix(tests): linux tests from macOS/Windows arm64 (<a href="">#1829</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pypa/cibuildwheel/compare/v2.17.0...v2.18.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pypa/cibuildwheel&package-manager=github_actions&previous-version=2.17.0&new-version=2.18.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `40fe71e4e393`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
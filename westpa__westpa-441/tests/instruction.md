# Issue

**Title:** Bump pypa/cibuildwheel from 2.19.2 to 2.20.0

## Description

Bumps [pypa/cibuildwheel](https://github.com/pypa/cibuildwheel) from 2.19.2 to 2.20.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/releases">pypa/cibuildwheel's releases</a>.</em></p>
<blockquote>
<h2>Version 2.20.0</h2>
<ul>
<li>🌟 CPython 3.13 wheels are now built by default - without the <code>CIBW_PRERELEASE_PYTHONS</code> flag. It's time to build and upload these wheels to PyPI! This release includes CPython 3.13.0rc1, which is guaranteed to be ABI compatible with the final release. Free-threading is still behind a flag/config option. (<a href="">#1950</a>)</li>
<li>✨ Provide a <code>CIBW_ALLOW_EMPTY</code> environment variable as an alternative to the command line flag. (<a href="">#1937</a>)</li>
<li>🐛 Don't use uv on PyPy3.8 on Windows, it stopped working starting in 0.2.25. Note that PyPy 3.8 is EoL. (<a href="">#1868</a>)</li>
<li>🛠 Set the <code>VSCMD_ARG_TGT_ARCH</code> variable based on target arch. (<a href="">#1876</a>)</li>
<li>🛠 Undo cleaner output on pytest 8-8.2 now that 8.3 is out. (<a href="">#1943</a>)</li>
<li>📚 Update examples to use Python 3.12 on host  (cibuildwheel will require Python 3.11+ on the host machine starting in October 2024) (<a href="">#1919</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/blob/main/docs/changelog.md">pypa/cibuildwheel's changelog</a>.</em></p>
<blockquote>
<h3>v2.20.0</h3>
<ul>
<li>🌟 CPython 3.13 wheels are now built by default - without the <code>CIBW_PRERELEASE_PYTHONS</code> flag. It's time to build and upload these wheels to PyPI! This release includes CPython 3.13.0rc1, which is guaranteed to be ABI compatible with the final release. Free-threading is still behind a flag/config option. (<a href="">#1950</a>)</li>
<li>✨ Provide a <code>CIBW_ALLOW_EMPTY</code> environment variable as an alternative to the command line flag. (<a href="">#1937</a>)</li>
<li>🐛 Don't use uv on PyPy3.8 on Windows, it stopped working starting in 0.2.25. Note that PyPy 3.8 is EoL. (<a href="">#1868</a>)</li>
<li>🛠 Set the <code>VSCMD_ARG_TGT_ARCH</code> variable based on target arch. (<a href="">#1876</a>)</li>
<li>🛠 Undo cleaner output on pytest 8-8.2 now that 8.3 is out. (<a href="">#1943</a>)</li>
<li>📚 Update examples to use Python 3.12 on host  (cibuildwheel will require Python 3.11+ on the host machine starting in October 2024) (<a href="">#1919</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>bd033a4</code></a> Bump version: v2.20.0</li>
<li><a href=""><code>9d023cf</code></a> Build CPython 3.13 by default (<a href="">#1950</a>)</li>
<li><a href=""><code>8a69dbd</code></a> [Bot] Update dependencies (<a href="">#1949</a>)</li>
<li><a href=""><code>147de6f</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#1947</a>)</li>
<li><a href=""><code>e217e44</code></a> [Bot] Update dependencies (<a href="">#1946</a>)</li>
<li><a href=""><code>871ef6b</code></a> tests: show xfail traceback summaries again (<a href="">#1943</a>)</li>
<li><a href=""><code>fac72f0</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#1944</a>)</li>
<li><a href=""><code>d4c3321</code></a> feat: add <code>CIBW_ALLOW_EMPTY</code> environment variable (<a href="">#1937</a>)</li>
<li><a href=""><code>5af5df4</code></a> [Bot] Update dependencies (<a href="">#1935</a>)</li>
<li><a href=""><code>6c5cf87</code></a> docs: fix nox docs command (<a href="">#1938</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pypa/cibuildwheel/compare/v2.19.2...v2.20.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pypa/cibuildwheel&package-manager=github_actions&previous-version=2.19.2&new-version=2.20.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `888a7606fbdc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
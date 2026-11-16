# Issue

**Title:** Bump pypa/cibuildwheel from 4.3.4 to 4.3.5 in /.github/workflows

## Description

Bumps [pypa/cibuildwheel](https://github.com/pypa/cibuildwheel) from 4.3.4 to 4.3.5.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/releases">pypa/cibuildwheel's releases</a>.</em></p>
<blockquote>
<h2>v4.3.5</h2>
<ul>
<li>🐛 Stops passing the target build environment to the host virtualenv call, regression in v4.3.4 (<a href="">#3023</a>)</li>
<li>🛠 Updates dependencies and constraints (pyodide-build 0.39.3, CPython 3.15.2, etc) (<a href="">#3024</a>, <a href="">#3027</a>)</li>
<li>💼 Updates CI actions (<a href="">#3025</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/blob/main/docs/changelog.md">pypa/cibuildwheel's changelog</a>.</em></p>
<blockquote>
<hr />
<h2>title: Changelog
ref: changelog</h2>
<h1>Changelog</h1>
<h3>v4.3.5</h3>
<p><em>27 October 2026</em></p>
<ul>
<li>🐛 Stops passing the target build environment to the host virtualenv call, regression in v4.3.4 (<a href="">#3023</a>)</li>
<li>🛠 Updates dependencies and constraints (pyodide-build 0.39.3, CPython 3.15.2, etc) (<a href="">#3024</a>, <a href="">#3027</a>)</li>
<li>💼 Updates CI actions (<a href="">#3025</a>)</li>
</ul>
<h3>v4.3.4</h3>
<p><em>22 October 2026</em></p>
<ul>
<li>🔐 Warns when a uv build frontend is selected and the host uv is older than 0.13.4, which still trusts the compromised eMudhra CA roots (<a href="">#3021</a>)</li>
<li>🔐 Uses cibuildwheel's CA bundle for pip on Python 3.9, where pip uses its bundled certifi, which still trusts the compromised eMudhra roots (<a href="">#3017</a>)</li>
<li>🔐 Uses cibuildwheel's CA bundle for pip on GraalPy, where truststore is not supported (<a href="">#3019</a>)</li>
<li>🔐 Uses cibuildwheel's CA bundle in Android, iOS, and Pyodide cross venvs, where pip uses the host's OpenSSL CA file (<a href="">#3020</a>)</li>
<li>🐛 Seeds build's isolated environment with the pinned pip on macOS and Windows, fixing GraalPy 25.0 builds (<a href="">#3018</a>)</li>
<li>💼 Stops Azure cache growth from <code>restoreKeys</code> (<a href="">#3022</a>)</li>
</ul>
<h3>v4.3.3</h3>
<p><em>21 October 2026</em></p>
<ul>
<li>🔐 Updates manylinux images and pip to fix vulnerability to <a href="https://emudhra.we-have-a-problem.com/">eMudhra</a>.</li>
</ul>
<h3>v4.3.2</h3>
<p><em>20 October 2026</em></p>
<ul>
<li>🔐 Updates our dependency pins to certifi==2026.10.19, following the <a href="https://emudhra.we-have-a-problem.com/">eMudhra Intermediate CA Compromise</a>. Linux builds may still be vulnerable through manylinux images - a patch release will soon follow if so.</li>
</ul>
<h3>v4.3.1</h3>
<p><em>10 October 2026</em></p>
<ul>
<li>🛠 Updates CPython 3.15 to the final 3.15.0 release (<a href="">#3009</a>)</li>
</ul>
<h3>v4.3.0</h3>
<p><em>5 October 2026</em></p>
<ul>
<li>✨ Extends <a href="https://cibuildwheel.pypa.io/en/stable/configuration/#inherit">option inheritance</a> to every configuration layer, so global and platform-specific settings can append or prepend to existing values, including cibuildwheel's defaults. Environment variables can also extend earlier settings using <code>CIBW_INHERIT</code>. (<a href="">#2928</a>)</li>
<li>✨ Adds PyPy 3.12 support and updates PyPy 3.11 to v8.0.0, available with the <code>pypy</code> <a href="https://cibuildwheel.pypa.io/en/stable/options/#enable"><code>enable</code></a> flag (<a href="">#2998</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f9b966c</code></a> Bump version: v4.3.5</li>
<li><a href=""><code>7e3caea</code></a> Update constraints (<a href="">#3027</a>)</li>
<li><a href=""><code>dff3913</code></a> chore(deps): bump the actions group with 2 updates (<a href="">#3025</a>)</li>
<li><a href=""><code>2956993</code></a> fix: do not pass target environment to the host virtualenv call (<a href="">#3023</a>)</li>
<li><a href=""><code>5d621c9</code></a> [Bot] Update dependencies (<a href="">#3024</a>)</li>
<li>See full diff in <a href="https://github.com/pypa/cibuildwheel/compare/b9e566a2b284570af229f6c2a33673410d0389a3...f9b966cfadf4109556cadc5bb39ddb72d0ce664e">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pypa/cibuildwheel&package-manager=github_actions&previous-version=4.3.4&new-version=4.3.5)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9bdd96dd2a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
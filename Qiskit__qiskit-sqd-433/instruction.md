# Issue

**Title:** Bump ruff from 0.16.9 to 0.17.3

## Description

Bumps [ruff](https://github.com/astral-sh/ruff) from 0.16.9 to 0.17.3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/releases">ruff's releases</a>.</em></p>
<blockquote>
<h2>0.17.3</h2>
<h2>Release Notes</h2>
<p>Released on 2026-10-26.</p>
<h3>Preview features</h3>
<ul>
<li>[<code>suspicious</code>] Add <code>shared-clock-mock</code> (<a href="">#29074</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>pyupgrade</code>] Avoid incorrect conversions to f-strings (<code>UP032</code>) (<a href="">#25485</a>)</li>
</ul>
<h3>Performance</h3>
<ul>
<li>Buffer stdout in <code>ruff format</code> (<a href="">#29631</a>)</li>
<li>Specialize ASCII identifier lexing (<a href="">#29503</a>)</li>
<li>Speed up identifier and keyword lexing (<a href="">#29463</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>[<code>flake8-bandit</code>] Describe what the rule actually checks for <code>httpx</code> (<code>S113</code>) (<a href="">#27936</a>)</li>
</ul>
<h3>Contributors</h3>
<ul>
<li><a href="https://github.com/itsvedantkumar"><code>@​itsvedantkumar</code></a></li>
<li><a href="https://github.com/charliermarsh"><code>@​charliermarsh</code></a></li>
<li><a href="https://github.com/anishgirianish"><code>@​anishgirianish</code></a></li>
</ul>
<h2>Install ruff 0.17.3</h2>
<h3>Install prebuilt binaries via shell script</h3>
<pre lang="sh"><code>curl --proto '=https' --tlsv1.2 -LsSf https://releases.astral.sh/github/ruff/releases/download/0.17.3/ruff-installer.sh | sh
</code></pre>
<h3>Install prebuilt binaries via powershell script</h3>
<pre lang="sh"><code>powershell -ExecutionPolicy Bypass -c &quot;irm https://releases.astral.sh/github/ruff/releases/download/0.17.3/ruff-installer.ps1 | iex&quot;
</code></pre>
<h2>Download ruff 0.17.3</h2>
<table>
<thead>
<tr>
<th>File</th>
<th>Platform</th>
<th>Checksum</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.17.3/ruff-aarch64-apple-darwin.tar.gz">ruff-aarch64-apple-darwin.tar.gz</a></td>
<td>Apple Silicon macOS</td>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.17.3/ruff-aarch64-apple-darwin.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.17.3/ruff-x86_64-apple-darwin.tar.gz">ruff-x86_64-apple-darwin.tar.gz</a></td>
<td>Intel macOS</td>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.17.3/ruff-x86_64-apple-darwin.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.17.3/ruff-aarch64-pc-windows-msvc.zip">ruff-aarch64-pc-windows-msvc.zip</a></td>
<td>ARM64 Windows</td>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.17.3/ruff-aarch64-pc-windows-msvc.zip.sha256">checksum</a></td>
</tr>
</tbody>
</table>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/blob/main/CHANGELOG.md">ruff's changelog</a>.</em></p>
<blockquote>
<h2>0.17.3</h2>
<p>Released on 2026-10-26.</p>
<h3>Preview features</h3>
<ul>
<li>[<code>suspicious</code>] Add <code>shared-clock-mock</code> (<a href="">#29074</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>pyupgrade</code>] Avoid incorrect conversions to f-strings (<code>UP032</code>) (<a href="">#25485</a>)</li>
</ul>
<h3>Performance</h3>
<ul>
<li>Buffer stdout in <code>ruff format</code> (<a href="">#29631</a>)</li>
<li>Specialize ASCII identifier lexing (<a href="">#29503</a>)</li>
<li>Speed up identifier and keyword lexing (<a href="">#29463</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>[<code>flake8-bandit</code>] Describe what the rule actually checks for <code>httpx</code> (<code>S113</code>) (<a href="">#27936</a>)</li>
</ul>
<h3>Contributors</h3>
<ul>
<li><a href="https://github.com/itsvedantkumar"><code>@​itsvedantkumar</code></a></li>
<li><a href="https://github.com/charliermarsh"><code>@​charliermarsh</code></a></li>
<li><a href="https://github.com/anishgirianish"><code>@​anishgirianish</code></a></li>
</ul>
<h2>0.17.2</h2>
<p>Released on 2026-10-22.</p>
<h3>Preview features</h3>
<ul>
<li>[<code>complexity</code>] Add <code>unnecessary-regular-expression-compile</code> (<a href="">#25533</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Avoid syntax errors for type variables with starred constraints (<code>UP040</code>, <code>UP046</code>, <code>UP047</code>, <code>RUF053</code>) (<a href="">#28362</a>)</li>
<li>[<code>pydocstyle</code>] Treat backslash-escaped <code>*args</code> and <code>**kwargs</code> as documented (<code>D417</code>) (<a href="">#29536</a>)</li>
<li>[<code>pylint</code>] Avoid false positive on starred elements (<code>PLE0643</code>) (<a href="">#29483</a>)</li>
<li>[<code>pylint</code>] Mark fixes unsafe when deleting comments (<code>PLR5501</code>, <code>PLW0120</code>) (<a href="">#29414</a>)</li>
<li>[<code>pyupgrade</code>] Mark fix unsafe when deleting comments (<code>UP035</code>) (<a href="">#29413</a>)</li>
</ul>
<h3>Performance</h3>
<ul>
<li>Avoid intermediate names in lint name resolution (<a href="">#29506</a>)</li>
<li>Prefilter bidirectional Unicode checks by UTF-8 leading bytes (<a href="">#29561</a>)</li>
<li>Share postfix parsing and reduce expression copies (<a href="">#29480</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ba65abf</code></a> Bump version to 0.17.3 (<a href="">#29745</a>)</li>
<li><a href=""><code>fb2f921</code></a> [ty] Fix narrowing of strings and integers compared with enum members (<a href="">#29743</a>)</li>
<li><a href=""><code>d181287</code></a> [ty] Index nominal union alternatives (<a href="">#29196</a>)</li>
<li><a href=""><code>07872ad</code></a> [ty] Preserve string literals in comparisons with <code>LiteralString</code> (<a href="">#29741</a>)</li>
<li><a href=""><code>95888b2</code></a> [ty] Preserve narrowing after guarded match subject captures (<a href="">#29558</a>)</li>
<li><a href=""><code>3c8166b</code></a> [ty] Fix hang when negating recursive unions of instance types (<a href="">#29652</a>)</li>
<li><a href=""><code>3fd20e0</code></a> [ty] Preserve generic callback specializations during return refinement (<a href="">#29667</a>)</li>
<li><a href=""><code>2f0a29e</code></a> [ty] Record predicate truthiness alongside expression inference (<a href="">#29706</a>)</li>
<li><a href=""><code>60f104a</code></a> [ty] Honor <a href="https://github.com/override"><code>@​override</code></a> on overload implementations in stubs (<a href="">#29470</a>)</li>
<li><a href=""><code>207ec3a</code></a> [ty] Add diagnostic baseline support (<a href="">#27636</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/ruff/compare/0.16.9...0.17.3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruff&package-manager=pip&previous-version=0.16.9&new-version=0.17.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5504edde4cc4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
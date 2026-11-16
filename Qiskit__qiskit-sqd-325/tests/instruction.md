# Issue

**Title:** Bump ruff from 0.15.15 to 0.15.20

## Description

Bumps [ruff](https://github.com/astral-sh/ruff) from 0.15.15 to 0.15.20.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/releases">ruff's releases</a>.</em></p>
<blockquote>
<h2>0.15.20</h2>
<h2>Release Notes</h2>
<p>Released on 2026-06-25.</p>
<h3>Preview features</h3>
<ul>
<li>Allow human-readable names in rule selectors (<a href="">#25887</a>)</li>
<li>Emit a warning instead of an error for unknown rule selectors (<a href="">#26113</a>)</li>
<li>Match <code>noqa</code> shebang handling in <code>ruff:ignore</code> comments (<a href="">#26286</a>)</li>
<li>[<code>ruff</code>] Remove <code>pytest-fixture-autouse</code> (<code>RUF076</code>) (<a href="">#26240</a>, <a href="">#26371</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Add versioning sections to custom crate READMEs (<a href="">#26317</a>)</li>
<li>Update <code>ruff_python_parser</code> README for crates.io (<a href="">#26315</a>)</li>
<li>[<code>perflint</code>] Clarify that <code>PERF402</code> applies to any iterable (<a href="">#26242</a>)</li>
</ul>
<h3>Contributors</h3>
<ul>
<li><a href="https://github.com/dhruvmanila"><code>@​dhruvmanila</code></a></li>
<li><a href="https://github.com/MichaReiser"><code>@​MichaReiser</code></a></li>
<li><a href="https://github.com/ntBre"><code>@​ntBre</code></a></li>
<li><a href="https://github.com/trilamsr"><code>@​trilamsr</code></a></li>
</ul>
<h2>Install ruff 0.15.20</h2>
<h3>Install prebuilt binaries via shell script</h3>
<pre lang="sh"><code>curl --proto '=https' --tlsv1.2 -LsSf https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-installer.sh | sh
</code></pre>
<h3>Install prebuilt binaries via powershell script</h3>
<pre lang="sh"><code>powershell -ExecutionPolicy Bypass -c &quot;irm https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-installer.ps1 | iex&quot;
</code></pre>
<h2>Download ruff 0.15.20</h2>
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
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-aarch64-apple-darwin.tar.gz">ruff-aarch64-apple-darwin.tar.gz</a></td>
<td>Apple Silicon macOS</td>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-aarch64-apple-darwin.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-x86_64-apple-darwin.tar.gz">ruff-x86_64-apple-darwin.tar.gz</a></td>
<td>Intel macOS</td>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-x86_64-apple-darwin.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-aarch64-pc-windows-msvc.zip">ruff-aarch64-pc-windows-msvc.zip</a></td>
<td>ARM64 Windows</td>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-aarch64-pc-windows-msvc.zip.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-i686-pc-windows-msvc.zip">ruff-i686-pc-windows-msvc.zip</a></td>
<td>x86 Windows</td>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-i686-pc-windows-msvc.zip.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-x86_64-pc-windows-msvc.zip">ruff-x86_64-pc-windows-msvc.zip</a></td>
<td>x64 Windows</td>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-x86_64-pc-windows-msvc.zip.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-aarch64-unknown-linux-gnu.tar.gz">ruff-aarch64-unknown-linux-gnu.tar.gz</a></td>
<td>ARM64 Linux</td>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-aarch64-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-i686-unknown-linux-gnu.tar.gz">ruff-i686-unknown-linux-gnu.tar.gz</a></td>
<td>x86 Linux</td>
<td><a href="https://releases.astral.sh/github/ruff/releases/download/0.15.20/ruff-i686-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
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
<h2>0.15.20</h2>
<p>Released on 2026-06-25.</p>
<h3>Preview features</h3>
<ul>
<li>Allow human-readable names in rule selectors (<a href="">#25887</a>)</li>
<li>Emit a warning instead of an error for unknown rule selectors (<a href="">#26113</a>)</li>
<li>Match <code>noqa</code> shebang handling in <code>ruff:ignore</code> comments (<a href="">#26286</a>)</li>
<li>[<code>ruff</code>] Remove <code>pytest-fixture-autouse</code> (<code>RUF076</code>) (<a href="">#26240</a>, <a href="">#26371</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Add versioning sections to custom crate READMEs (<a href="">#26317</a>)</li>
<li>Update <code>ruff_python_parser</code> README for crates.io (<a href="">#26315</a>)</li>
<li>[<code>perflint</code>] Clarify that <code>PERF402</code> applies to any iterable (<a href="">#26242</a>)</li>
</ul>
<h3>Contributors</h3>
<ul>
<li><a href="https://github.com/dhruvmanila"><code>@​dhruvmanila</code></a></li>
<li><a href="https://github.com/MichaReiser"><code>@​MichaReiser</code></a></li>
<li><a href="https://github.com/ntBre"><code>@​ntBre</code></a></li>
<li><a href="https://github.com/trilamsr"><code>@​trilamsr</code></a></li>
</ul>
<h2>0.15.19</h2>
<p>Released on 2026-06-23.</p>
<h3>Preview features</h3>
<ul>
<li>Support human-readable names when hovering suppression comments and in code actions (<a href="">#26114</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Fall back to default settings when editor-only settings are invalid (<a href="">#26244</a>)</li>
<li>Fix panic when inserting text at a notebook cell boundary (<a href="">#26111</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>[<code>pylint</code>] Update fix suggestions for <code>__floor__</code>, <code>__trunc__</code>, <code>__length_hint__</code>, and <code>__matmul__</code> variants (<code>PLC2801</code>) (<a href="">#26239</a>)</li>
</ul>
<h3>Performance</h3>
<ul>
<li>Avoid allocating when parsing single string literals (<a href="">#26200</a>)</li>
<li>Avoid reallocating singleton call arguments (<a href="">#26223</a>)</li>
<li>Lazily create source files for lint diagnostics (<a href="">#26226</a>)</li>
<li>Optimize formatter text width and indentation (<a href="">#26236</a>)</li>
<li>Reserve capacity for builtin bindings (<a href="">#26229</a>)</li>
<li>Skip repeated-key checks for singleton dictionaries (<a href="">#26228</a>)</li>
<li>Use ArrayVec for qualified name segments (<a href="">#26224</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f82a36b</code></a> Bump 0.15.20 (<a href="">#26376</a>)</li>
<li><a href=""><code>af32943</code></a> Improve the summarise-ecosystem-results skill (<a href="">#26378</a>)</li>
<li><a href=""><code>485ebab</code></a> Remove <code>RUF076</code> name from schema (<a href="">#26371</a>)</li>
<li><a href=""><code>ef81835</code></a> [ty] Implement rust-analyzer's &quot;Click for full compiler diagnostic&quot; feature (...</li>
<li><a href=""><code>572b31e</code></a> [<code>ruff</code>] Remove <code>pytest-fixture-autouse</code> (<code>RUF076</code>) (<a href="">#26240</a>)</li>
<li><a href=""><code>f703f21</code></a> Allow human-readable names in rule selectors (<a href="">#25887</a>)</li>
<li><a href=""><code>0d726b2</code></a> [ty] Reuse equality semantics for membership compatibility (<a href="">#25955</a>)</li>
<li><a href=""><code>dbe6e98</code></a> [ty] Infer definite equality comparison results (<a href="">#26337</a>)</li>
<li><a href=""><code>e700ea3</code></a> [ty] Prove TypedDict structural patterns exhaustive (<a href="">#26285</a>)</li>
<li><a href=""><code>6a0d2ec</code></a> [ty] Widen inferred class-valued instance attributes (<a href="">#26338</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/ruff/compare/0.15.15...0.15.20">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruff&package-manager=pip&previous-version=0.15.15&new-version=0.15.20)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
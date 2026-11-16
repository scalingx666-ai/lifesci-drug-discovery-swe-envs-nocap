# Issue

**Title:** Bump ruff from 0.9.4 to 0.9.9

## Description

Bumps [ruff](https://github.com/astral-sh/ruff) from 0.9.4 to 0.9.9.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/releases">ruff's releases</a>.</em></p>
<blockquote>
<h2>0.9.9</h2>
<h2>Release Notes</h2>
<h3>Preview features</h3>
<ul>
<li>Fix caching of unsupported-syntax errors (<a href="">#16425</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Only show unsupported-syntax errors in editors when preview mode is enabled (<a href="">#16429</a>)</li>
</ul>
<h2>Contributors</h2>
<ul>
<li><a href="https://github.com/InSyncWithFoo"><code>@​InSyncWithFoo</code></a></li>
<li><a href="https://github.com/MichaReiser"><code>@​MichaReiser</code></a></li>
<li><a href="https://github.com/dhruvmanila"><code>@​dhruvmanila</code></a></li>
<li><a href="https://github.com/ntBre"><code>@​ntBre</code></a></li>
</ul>
<h2>Install ruff 0.9.9</h2>
<h3>Install prebuilt binaries via shell script</h3>
<pre lang="sh"><code>curl --proto '=https' --tlsv1.2 -LsSf https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-installer.sh | sh
</code></pre>
<h3>Install prebuilt binaries via powershell script</h3>
<pre lang="sh"><code>powershell -ExecutionPolicy ByPass -c &quot;irm https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-installer.ps1 | iex&quot;
</code></pre>
<h2>Download ruff 0.9.9</h2>
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
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-aarch64-apple-darwin.tar.gz">ruff-aarch64-apple-darwin.tar.gz</a></td>
<td>Apple Silicon macOS</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-aarch64-apple-darwin.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-x86_64-apple-darwin.tar.gz">ruff-x86_64-apple-darwin.tar.gz</a></td>
<td>Intel macOS</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-x86_64-apple-darwin.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-aarch64-pc-windows-msvc.zip">ruff-aarch64-pc-windows-msvc.zip</a></td>
<td>ARM64 Windows</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-aarch64-pc-windows-msvc.zip.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-i686-pc-windows-msvc.zip">ruff-i686-pc-windows-msvc.zip</a></td>
<td>x86 Windows</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-i686-pc-windows-msvc.zip.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-x86_64-pc-windows-msvc.zip">ruff-x86_64-pc-windows-msvc.zip</a></td>
<td>x64 Windows</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-x86_64-pc-windows-msvc.zip.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-aarch64-unknown-linux-gnu.tar.gz">ruff-aarch64-unknown-linux-gnu.tar.gz</a></td>
<td>ARM64 Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-aarch64-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-i686-unknown-linux-gnu.tar.gz">ruff-i686-unknown-linux-gnu.tar.gz</a></td>
<td>x86 Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-i686-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-powerpc64-unknown-linux-gnu.tar.gz">ruff-powerpc64-unknown-linux-gnu.tar.gz</a></td>
<td>PPC64 Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-powerpc64-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-powerpc64le-unknown-linux-gnu.tar.gz">ruff-powerpc64le-unknown-linux-gnu.tar.gz</a></td>
<td>PPC64LE Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-powerpc64le-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-s390x-unknown-linux-gnu.tar.gz">ruff-s390x-unknown-linux-gnu.tar.gz</a></td>
<td>S390x Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-s390x-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-x86_64-unknown-linux-gnu.tar.gz">ruff-x86_64-unknown-linux-gnu.tar.gz</a></td>
<td>x64 Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-x86_64-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-armv7-unknown-linux-gnueabihf.tar.gz">ruff-armv7-unknown-linux-gnueabihf.tar.gz</a></td>
<td>ARMv7 Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-armv7-unknown-linux-gnueabihf.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-aarch64-unknown-linux-musl.tar.gz">ruff-aarch64-unknown-linux-musl.tar.gz</a></td>
<td>ARM64 MUSL Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.9.9/ruff-aarch64-unknown-linux-musl.tar.gz.sha256">checksum</a></td>
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
<h2>0.9.9</h2>
<h3>Preview features</h3>
<ul>
<li>Fix caching of unsupported-syntax errors (<a href="">#16425</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Only show unsupported-syntax errors in editors when preview mode is enabled (<a href="">#16429</a>)</li>
</ul>
<h2>0.9.8</h2>
<h3>Preview features</h3>
<ul>
<li>Start detecting version-related syntax errors in the parser (<a href="">#16090</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>[<code>pylint</code>] Mark fix unsafe (<code>PLW1507</code>) (<a href="">#16343</a>)</li>
<li>[<code>pylint</code>] Catch <code>case np.nan</code>/<code>case math.nan</code> in <code>match</code> statements (<code>PLW0177</code>) (<a href="">#16378</a>)</li>
<li>[<code>ruff</code>] Add more Pydantic models variants to the list of default copy semantics (<code>RUF012</code>) (<a href="">#16291</a>)</li>
</ul>
<h3>Server</h3>
<ul>
<li>Avoid indexing the project if <code>configurationPreference</code> is <code>editorOnly</code> (<a href="">#16381</a>)</li>
<li>Avoid unnecessary info at non-trace server log level (<a href="">#16389</a>)</li>
<li>Expand <code>ruff.configuration</code> to allow inline config (<a href="">#16296</a>)</li>
<li>Notify users for invalid client settings (<a href="">#16361</a>)</li>
</ul>
<h3>Configuration</h3>
<ul>
<li>Add <code>per-file-target-version</code> option (<a href="">#16257</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>refurb</code>] Do not consider docstring(s) (<code>FURB156</code>) (<a href="">#16391</a>)</li>
<li>[<code>flake8-self</code>] Ignore attribute accesses on instance-like variables (<code>SLF001</code>) (<a href="">#16149</a>)</li>
<li>[<code>pylint</code>] Fix false positives, add missing methods, and support positional-only parameters (<code>PLE0302</code>) (<a href="">#16263</a>)</li>
<li>[<code>flake8-pyi</code>] Mark <code>PYI030</code> fix unsafe when comments are deleted (<a href="">#16322</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix example for <code>S611</code> (<a href="">#16316</a>)</li>
<li>Normalize inconsistent markdown headings in docstrings (<a href="">#16364</a>)</li>
<li>Document MSRV policy (<a href="">#16384</a>)</li>
</ul>
<h2>0.9.7</h2>
<h3>Preview features</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>091d0af</code></a> Bump version to Ruff 0.9.9 (<a href="">#16434</a>)</li>
<li><a href=""><code>3d72138</code></a> Check <code>LinterSettings::preview</code> for version-related syntax errors (<a href="">#16429</a>)</li>
<li><a href=""><code>4a23756</code></a> Avoid caching files with unsupported syntax errors (<a href="">#16425</a>)</li>
<li><a href=""><code>af62f79</code></a> Prioritize &quot;bug&quot; label for changelog sections (<a href="">#16433</a>)</li>
<li><a href=""><code>0ced8d0</code></a> [<code>flake8-copyright</code>] Add links to applicable options (<code>CPY001</code>) (<a href="">#16421</a>)</li>
<li><a href=""><code>a8e171f</code></a> Fix string-length limit in documentation for PYI054 (<a href="">#16432</a>)</li>
<li><a href=""><code>cf83584</code></a> Show version-related syntax errors in the playground (<a href="">#16419</a>)</li>
<li><a href=""><code>764aa0e</code></a> Allow passing <code>ParseOptions</code> to inline tests (<a href="">#16357</a>)</li>
<li><a href=""><code>568cf88</code></a> Bump version to 0.9.8 (<a href="">#16414</a>)</li>
<li><a href=""><code>040071b</code></a> [red-knot] Ignore surrounding whitespace when looking for `&lt;!-- snapshot-diag...</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/ruff/compare/0.9.4...0.9.9">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruff&package-manager=pip&previous-version=0.9.4&new-version=0.9.9)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eedfcf980fb3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
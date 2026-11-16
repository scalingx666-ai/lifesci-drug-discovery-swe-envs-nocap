# Issue

**Title:** Bump ruff from 0.9.9 to 0.11.2

## Description

Bumps [ruff](https://github.com/astral-sh/ruff) from 0.9.9 to 0.11.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/releases">ruff's releases</a>.</em></p>
<blockquote>
<h2>0.11.2</h2>
<h2>Release Notes</h2>
<h3>Preview features</h3>
<ul>
<li>[syntax-errors] Fix false-positive syntax errors emitted for annotations on variadic parameters before Python 3.11 (<a href="">#16878</a>)</li>
</ul>
<h2>Contributors</h2>
<ul>
<li><a href="https://github.com/AlexWaygood"><code>@​AlexWaygood</code></a></li>
<li><a href="https://github.com/MatthewMckee4"><code>@​MatthewMckee4</code></a></li>
<li><a href="https://github.com/dhruvmanila"><code>@​dhruvmanila</code></a></li>
<li><a href="https://github.com/junhsonjb"><code>@​junhsonjb</code></a></li>
<li><a href="https://github.com/mtshiba"><code>@​mtshiba</code></a></li>
<li><a href="https://github.com/ntBre"><code>@​ntBre</code></a></li>
</ul>
<h2>Install ruff 0.11.2</h2>
<h3>Install prebuilt binaries via shell script</h3>
<pre lang="sh"><code>curl --proto '=https' --tlsv1.2 -LsSf https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-installer.sh | sh
</code></pre>
<h3>Install prebuilt binaries via powershell script</h3>
<pre lang="sh"><code>powershell -ExecutionPolicy ByPass -c &quot;irm https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-installer.ps1 | iex&quot;
</code></pre>
<h2>Download ruff 0.11.2</h2>
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
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-aarch64-apple-darwin.tar.gz">ruff-aarch64-apple-darwin.tar.gz</a></td>
<td>Apple Silicon macOS</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-aarch64-apple-darwin.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-x86_64-apple-darwin.tar.gz">ruff-x86_64-apple-darwin.tar.gz</a></td>
<td>Intel macOS</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-x86_64-apple-darwin.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-aarch64-pc-windows-msvc.zip">ruff-aarch64-pc-windows-msvc.zip</a></td>
<td>ARM64 Windows</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-aarch64-pc-windows-msvc.zip.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-i686-pc-windows-msvc.zip">ruff-i686-pc-windows-msvc.zip</a></td>
<td>x86 Windows</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-i686-pc-windows-msvc.zip.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-x86_64-pc-windows-msvc.zip">ruff-x86_64-pc-windows-msvc.zip</a></td>
<td>x64 Windows</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-x86_64-pc-windows-msvc.zip.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-aarch64-unknown-linux-gnu.tar.gz">ruff-aarch64-unknown-linux-gnu.tar.gz</a></td>
<td>ARM64 Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-aarch64-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-i686-unknown-linux-gnu.tar.gz">ruff-i686-unknown-linux-gnu.tar.gz</a></td>
<td>x86 Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-i686-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-powerpc64-unknown-linux-gnu.tar.gz">ruff-powerpc64-unknown-linux-gnu.tar.gz</a></td>
<td>PPC64 Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-powerpc64-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-powerpc64le-unknown-linux-gnu.tar.gz">ruff-powerpc64le-unknown-linux-gnu.tar.gz</a></td>
<td>PPC64LE Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-powerpc64le-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-s390x-unknown-linux-gnu.tar.gz">ruff-s390x-unknown-linux-gnu.tar.gz</a></td>
<td>S390x Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-s390x-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-x86_64-unknown-linux-gnu.tar.gz">ruff-x86_64-unknown-linux-gnu.tar.gz</a></td>
<td>x64 Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-x86_64-unknown-linux-gnu.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-armv7-unknown-linux-gnueabihf.tar.gz">ruff-armv7-unknown-linux-gnueabihf.tar.gz</a></td>
<td>ARMv7 Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-armv7-unknown-linux-gnueabihf.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-aarch64-unknown-linux-musl.tar.gz">ruff-aarch64-unknown-linux-musl.tar.gz</a></td>
<td>ARM64 MUSL Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-aarch64-unknown-linux-musl.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-i686-unknown-linux-musl.tar.gz">ruff-i686-unknown-linux-musl.tar.gz</a></td>
<td>x86 MUSL Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-i686-unknown-linux-musl.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-x86_64-unknown-linux-musl.tar.gz">ruff-x86_64-unknown-linux-musl.tar.gz</a></td>
<td>x64 MUSL Linux</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-x86_64-unknown-linux-musl.tar.gz.sha256">checksum</a></td>
</tr>
<tr>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-arm-unknown-linux-musleabihf.tar.gz">ruff-arm-unknown-linux-musleabihf.tar.gz</a></td>
<td>ARMv6 MUSL Linux (Hardfloat)</td>
<td><a href="https://github.com/astral-sh/ruff/releases/download/0.11.2/ruff-arm-unknown-linux-musleabihf.tar.gz.sha256">checksum</a></td>
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
<h2>0.11.2</h2>
<h3>Preview features</h3>
<ul>
<li>[syntax-errors] Fix false-positive syntax errors emitted for annotations on variadic parameters before Python 3.11 (<a href="">#16878</a>)</li>
</ul>
<h2>0.11.1</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Add <code>chain</code>, <code>chain_linear</code> and <code>cross_downstream</code> for <code>AIR302</code> (<a href="">#16647</a>)</li>
<li>[syntax-errors] Improve error message and range for pre-PEP-614 decorator syntax errors (<a href="">#16581</a>)</li>
<li>[syntax-errors] PEP 701 f-strings before Python 3.12 (<a href="">#16543</a>)</li>
<li>[syntax-errors] Parenthesized context managers before Python 3.9 (<a href="">#16523</a>)</li>
<li>[syntax-errors] Star annotations before Python 3.11 (<a href="">#16545</a>)</li>
<li>[syntax-errors] Star expression in index before Python 3.11 (<a href="">#16544</a>)</li>
<li>[syntax-errors] Unparenthesized assignment expressions in sets and indexes (<a href="">#16404</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Server: Allow <code>FixAll</code> action in presence of version-specific syntax errors (<a href="">#16848</a>)</li>
<li>[<code>flake8-bandit</code>] Allow raw strings in <code>suspicious-mark-safe-usage</code> (<code>S308</code>) <a href="">#16702</a> (<a href="">#16770</a>)</li>
<li>[<code>refurb</code>] Avoid panicking <code>unwrap</code> in <code>verbose-decimal-constructor</code> (<code>FURB157</code>) (<a href="">#16777</a>)</li>
<li>[<code>refurb</code>] Fix starred expressions fix (<code>FURB161</code>) (<a href="">#16550</a>)</li>
<li>Fix <code>--statistics</code> reporting for unsafe fixes (<a href="">#16756</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>[<code>flake8-executables</code>] Allow <code>uv run</code> in shebang line for <code>shebang-missing-python</code> (<code>EXE003</code>) (<a href="">#16849</a>,<a href="">#16855</a>)</li>
</ul>
<h3>CLI</h3>
<ul>
<li>Add <code>--exit-non-zero-on-format</code> (<a href="">#16009</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Update Ruff tutorial to avoid non-existent fix in <code>__init__.py</code> (<a href="">#16818</a>)</li>
<li>[<code>flake8-gettext</code>] Swap <code>format-</code> and <code>printf-in-get-text-func-call</code> examples (<code>INT002</code>, <code>INT003</code>) (<a href="">#16769</a>)</li>
</ul>
<h2>0.11.0</h2>
<p>This is a follow-up to release 0.10.0. Because of a mistake in the release process, the <code>requires-python</code> inference changes were not included in that release. Ruff 0.11.0 now includes this change as well as the stabilization of the preview behavior for <code>PGH004</code>.</p>
<h3>Breaking changes</h3>
<ul>
<li>
<p><strong>Changes to how the Python version is inferred when a <code>target-version</code> is not specified</strong> (<a href="">#16319</a>)</p>
<p>In previous versions of Ruff, you could specify your Python version with:</p>
<ul>
<li>The <code>target-version</code> option in a <code>ruff.toml</code> file or the <code>[tool.ruff]</code> section of a pyproject.toml file.</li>
</ul>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4773878</code></a> Bump 0.11.2 (<a href="">#16896</a>)</li>
<li><a href=""><code>2a4d835</code></a> Use the common <code>OperatorPrecedence</code> for the parser (<a href="">#16747</a>)</li>
<li><a href=""><code>04a8756</code></a> [red-knot] Check subtype relation between callable types (<a href="">#16804</a>)</li>
<li><a href=""><code>193c381</code></a> [red-knot] Check whether two callable types are equivalent (<a href="">#16698</a>)</li>
<li><a href=""><code>63e78b4</code></a> [red-knot] Ban most <code>Type::Instance</code> types in type expressions (<a href="">#16872</a>)</li>
<li><a href=""><code>296d67a</code></a> Special-case value-expression inference of special form subscriptions (<a href="">#16877</a>)</li>
<li><a href=""><code>42cbce5</code></a> [syntax-errors] Fix star annotation before Python 3.11 (<a href="">#16878</a>)</li>
<li><a href=""><code>6760251</code></a> Recognize <code>SyntaxError:</code> as an error code for ecosystem checks (<a href="">#16879</a>)</li>
<li><a href=""><code>23382f5</code></a> [red-knot] add test cases result in false positive errors (<a href="">#16856</a>)</li>
<li><a href=""><code>c1971fd</code></a> Bump 0.11.1 (<a href="">#16871</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/ruff/compare/0.9.9...0.11.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruff&package-manager=pip&previous-version=0.9.9&new-version=0.11.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4e802ef1dae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
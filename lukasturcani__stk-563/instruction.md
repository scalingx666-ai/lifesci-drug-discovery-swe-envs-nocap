# Issue

**Title:** Bump wheel from 0.45.1 to 0.46.2

## Description

Bumps [wheel](https://github.com/pypa/wheel) from 0.45.1 to 0.46.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/wheel/releases">wheel's releases</a>.</em></p>
<blockquote>
<h2>0.46.2</h2>
<ul>
<li>Restored the <code>bdist_wheel</code> command for compatibility with <code>setuptools</code> older than v70.1</li>
<li>Importing <code>wheel.bdist_wheel</code> now emits a <code>FutureWarning</code> instead of a <code>DeprecationWarning</code></li>
<li>Fixed <code>wheel unpack</code> potentially altering the permissions of files outside of the destination tree with maliciously crafted wheels (CVE-2026-24049)</li>
</ul>
<h2>0.46.1</h2>
<ul>
<li>Temporarily restored the <code>wheel.macosx_libfile</code> module (<a href="">#659</a>)</li>
</ul>
<h2>0.46.0</h2>
<ul>
<li>Dropped support for Python 3.8</li>
<li>Removed the <code>bdist_wheel</code> setuptools command implementation and entry point. The <code>wheel.bdist_wheel</code> module is now just an alias to <code>setuptools.command.bdist_wheel</code>, emitting a deprecation warning on import.</li>
<li>Removed vendored <code>packaging</code> in favor of a run-time dependency on it</li>
<li>Made the <code>wheel.metadata</code> module private (with a deprecation warning if it's imported</li>
<li>Made the <code>wheel.cli</code> package private (no deprecation warning)</li>
<li>Fixed an exception when calling the <code>convert</code> command with an empty description field</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pypa/wheel/blob/main/docs/news.rst">wheel's changelog</a>.</em></p>
<blockquote>
<h1>Release Notes</h1>
<p><strong>UNRELEASED</strong></p>
<ul>
<li>Fixed <code>wheel unpack</code> taking the mode of the unpack directory itself from the
archive when a wheel contains a member whose name is made up entirely of empty,
<code>.</code> or <code>..</code> path components (such as <code>../</code>), which let a malicious wheel
leave the unpacked tree world-writable</li>
<li>Fixed <code>wheel pack --build-number</code> accepting build tags that are invalid in a
wheel file name (not starting with a digit, or containing <code>-</code>), the same
validation <code>wheel tags --build</code> already performs</li>
<li>Fixed the macOS platform-tag warning always using the plural &quot;these files&quot;
wording, even when only a single library required a higher deployment target
(<code> &lt;</code>_)</li>
</ul>
<p><strong>0.48.0 (2026-08-12)</strong></p>
<ul>
<li>Added a <code>--local-version</code> option to <code>wheel pack</code> to add, replace, or remove a
PEP 440 local version identifier from a wheel
(<code> &lt;</code>_)</li>
<li>Fixed <code>wheel convert</code> unnecessarily upgrading compatible core metadata versions
(<code> &lt;</code>_)</li>
<li>Fixed <code>wheel tags</code> producing invalid archives when retagging wheels whose
entries use ZIP64, by dropping the central-directory ZIP64 extra field that is
not valid in a local file header
(<code> &lt;</code>_)</li>
<li>Fixed <code>wheel convert</code> writing the converted wheel outside the destination
directory when the input archive contained a maliciously crafted project name
or version with path separators (arbitrary file write / path traversal)
(<code>GHSA-vgq5-9859-3mmw &lt;https://github.com/pypa/wheel/security/advisories/GHSA-vgq5-9859-3mmw&gt;</code>_)</li>
</ul>
<p><strong>0.47.0 (2026-04-22)</strong></p>
<ul>
<li>Added the <code>wheel info</code> subcommand to display metadata about wheel files without
unpacking them (<code> &lt;</code>_)</li>
<li>Fixed <code>WheelFile</code> raising <code>Missing RECORD file</code> when the wheel filename contains
uppercase characters (e.g. <code>Django-3.2.5.whl</code>) but the <code>.dist-info</code> directory
inside uses normalized lowercase naming
(<code> &lt;</code>_)</li>
</ul>
<p><strong>0.46.3 (2026-01-22)</strong></p>
<ul>
<li>Fixed <code>ImportError: cannot import name '_setuptools_logging' from 'wheel'</code> when
installed alongside an old version of setuptools and running the <code>bdist_wheel</code>
command (<code> &lt;</code>_)</li>
</ul>
<p><strong>0.46.2 (2026-01-22)</strong></p>
<ul>
<li>Restored the <code>bdist_wheel</code> command for compatibility with <code>setuptools</code> older than</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>eba4036</code></a> Updated the version number for v0.46.2</li>
<li><a href=""><code>557fb54</code></a> Created a new release</li>
<li><a href=""><code>7a7d2de</code></a> Fixed security issue around wheel unpack (<a href="">#675</a>)</li>
<li><a href=""><code>41418fa</code></a> Fixed test failures due to metadata normalization changes</li>
<li><a href=""><code>c1d442b</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#674</a>)</li>
<li><a href=""><code>0bac882</code></a> Update github actions environments (<a href="">#673</a>)</li>
<li><a href=""><code>be9f45b</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#667</a>)</li>
<li><a href=""><code>6244f08</code></a> Update pre-commit ruff legacy alias (<a href="">#668</a>)</li>
<li><a href=""><code>15b7577</code></a> PEP 639 compliance (<a href="">#670</a>)</li>
<li><a href=""><code>fc8cb41</code></a> Revert &quot;Removed redundant Python version from the publish workflow (<a href="">#666</a>)&quot;</li>
<li>Additional commits viewable in <a href="https://github.com/pypa/wheel/compare/0.45.1...0.46.2">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04c594de560c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
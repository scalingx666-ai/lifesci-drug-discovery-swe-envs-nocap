# Issue

**Title:** Bump pypa/cibuildwheel from 4.2.1 to 4.3.4

## Description

Bumps [pypa/cibuildwheel](https://github.com/pypa/cibuildwheel) from 4.2.1 to 4.3.4.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/releases">pypa/cibuildwheel's releases</a>.</em></p>
<blockquote>
<h2>v4.3.4</h2>
<ul>
<li>🔐 Warns when a uv build frontend is selected and the host uv is older than 0.13.4, which still trusts the compromised eMudhra CA roots (<a href="">#3021</a>)</li>
<li>🔐 Uses cibuildwheel's CA bundle for pip on Python 3.9, where pip uses its bundled certifi, which still trusts the compromised eMudhra roots (<a href="">#3017</a>)</li>
<li>🔐 Uses cibuildwheel's CA bundle for pip on GraalPy, where truststore is not supported (<a href="">#3019</a>)</li>
<li>🔐 Uses cibuildwheel's CA bundle in Android, iOS, and Pyodide cross venvs, where pip uses the host's OpenSSL CA file (<a href="">#3020</a>)</li>
<li>🐛 Seeds build's isolated environment with the pinned pip on macOS and Windows, fixing GraalPy 25.0 builds (<a href="">#3018</a>)</li>
<li>💼 Stops Azure cache growth from <code>restoreKeys</code> (<a href="">#3022</a>)</li>
</ul>
<h2>v4.3.3</h2>
<ul>
<li>🔐 Updates manylinux images and pip to fix vulnerability to <a href="https://emudhra.we-have-a-problem.com/">eMudhra</a>.</li>
</ul>
<h2>v4.3.2</h2>
<ul>
<li>🔐 Updates our dependency pins to certifi==2026.10.19, following the <a href="https://emudhra.we-have-a-problem.com/">eMudhra Intermediate CA Compromise</a>. Linux builds may still be vulnerable through manylinux images - a patch release will soon follow if so.</li>
</ul>
<h2>v4.3.1</h2>
<ul>
<li>🛠 Updates CPython 3.15 to the final 3.15.0 release (<a href="">#3009</a>)</li>
</ul>
<h2>v4.3.0</h2>
<ul>
<li>✨ Extends <a href="https://cibuildwheel.pypa.io/en/stable/configuration/#inherit">option inheritance</a> to every configuration layer, so global and platform-specific settings can append or prepend to existing values, including cibuildwheel's defaults. Environment variables can also extend earlier settings using <code>CIBW_INHERIT</code>. (<a href="">#2928</a>)</li>
<li>✨ Adds PyPy 3.12 support and updates PyPy 3.11 to v8.0.0, available with the <code>pypy</code> <a href="https://cibuildwheel.pypa.io/en/stable/options/#enable"><code>enable</code></a> flag (<a href="">#2998</a>)</li>
<li>✨ Adds GraalPy 3.13 (v25.3) support on Linux, Windows, and macOS arm64, available with the <code>graalpy</code> <a href="https://cibuildwheel.pypa.io/en/stable/options/#enable"><code>enable</code></a> flag (<a href="">#2982</a>)</li>
<li>✨ Adds <a href="https://cibuildwheel.pypa.io/en/stable/options/#log-fold-mode"><code>log-fold-mode</code></a> to override CI log folding, including <code>CIBW_LOG_FOLD_MODE=disabled</code> to keep build steps expanded (<a href="">#2972</a>)</li>
<li>✨ Adds a <code>python-path</code> input to the GitHub Action to choose the Python interpreter used to run cibuildwheel, and falls back to system <code>python3</code> on runner architectures unsupported by <code>setup-python</code>, such as native riscv64 (<a href="">#2990</a>)</li>
<li>🐛 Fixes Windows command execution when paths or arguments contain shell metacharacters, including dependency specifiers containing <code>&lt;</code> or <code>&gt;</code> (<a href="">#2978</a>)</li>
<li>🛠 Improves readability of logged commands whose arguments contain quotes (<a href="">#2993</a>)</li>
<li>🛠 Updates Pyodide to 0.27.8, 0.29.5, and 314.0.7, and updates its build tooling, including auditwheel-emscripten 0.3.0 (<a href="">#2996</a>)</li>
<li>🛠 Updates dependencies and container pins, including CPython 3.15.0rc3 (<a href="">#2986</a>, <a href="">#3003</a>)</li>
<li>📚 Corrects references to <code>--archs</code> in CLI help, error messages, and documentation (<a href="">#2992</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pypa/cibuildwheel/blob/main/docs/changelog.md">pypa/cibuildwheel's changelog</a>.</em></p>
<blockquote>
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
<li>✨ Adds GraalPy 3.13 (v25.3) support on Linux, Windows, and macOS arm64, available with the <code>graalpy</code> <a href="https://cibuildwheel.pypa.io/en/stable/options/#enable"><code>enable</code></a> flag (<a href="">#2982</a>)</li>
<li>✨ Adds <a href="https://cibuildwheel.pypa.io/en/stable/options/#log-fold-mode"><code>log-fold-mode</code></a> to override CI log folding, including <code>CIBW_LOG_FOLD_MODE=disabled</code> to keep build steps expanded (<a href="">#2972</a>)</li>
<li>✨ Adds a <code>python-path</code> input to the GitHub Action to choose the Python interpreter used to run cibuildwheel, and falls back to system <code>python3</code> on runner architectures unsupported by <code>setup-python</code>, such as native riscv64 (<a href="">#2990</a>)</li>
<li>🐛 Fixes Windows command execution when paths or arguments contain shell metacharacters, including dependency specifiers containing <code>&lt;</code> or <code>&gt;</code> (<a href="">#2978</a>)</li>
<li>🛠 Improves readability of logged commands whose arguments contain quotes (<a href="">#2993</a>)</li>
<li>🛠 Updates Pyodide to 0.27.8, 0.29.5, and 314.0.7, and updates its build tooling, including auditwheel-emscripten 0.3.0 (<a href="">#2996</a>)</li>
<li>🛠 Updates dependencies and container pins, including CPython 3.15.0rc3 (<a href="">#2986</a>, <a href="">#3003</a>)</li>
<li>📚 Corrects references to <code>--archs</code> in CLI help, error messages, and documentation (<a href="">#2992</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b9e566a</code></a> Bump version: v4.3.4</li>
<li><a href=""><code>0d511ac</code></a> fix: use cibuildwheel's CA bundle in cross venvs (<a href="">#3020</a>)</li>
<li><a href=""><code>d6c9b11</code></a> feat: warn when uv is too old to have the eMudhra CA fix (<a href="">#3021</a>)</li>
<li><a href=""><code>4463120</code></a> fix: seed build's isolated env with the pinned pip (<a href="">#3018</a>)</li>
<li><a href=""><code>6d4911a</code></a> fix: use cibuildwheel's CA bundle for pip on GraalPy (<a href="">#3019</a>)</li>
<li><a href=""><code>54d1a6f</code></a> ci: stop Azure cache growth from restoreKeys (<a href="">#3022</a>)</li>
<li><a href=""><code>5891574</code></a> fix: use cibuildwheel's CA bundle for pip on Python 3.9 (<a href="">#3017</a>)</li>
<li><a href=""><code>8c2dcd2</code></a> Bump version: v4.3.3</li>
<li><a href=""><code>56459e6</code></a> [Bot] Update dependencies (<a href="">#3012</a>)</li>
<li><a href=""><code>afd09e6</code></a> chore(deps): bump the actions group with 4 updates (<a href="">#3013</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pypa/cibuildwheel/compare/v4.2.1...v4.3.4">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd9b8eb9addf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** deps(deps): bump the minor-and-patch group with 22 updates

## Description

Bumps the minor-and-patch group with 22 updates:

| Package | From | To |
| --- | --- | --- |
| [coverage](https://github.com/nedbat/coveragepy) | `7.10.6` | `7.10.7` |
| [gseapy](https://github.com/zqfang/GSEApy) | `1.1.9` | `1.1.10` |
| [mkdocs-include-markdown-plugin](https://github.com/mondeja/mkdocs-include-markdown-plugin) | `7.1.7` | `7.2.0` |
| [mkdocs-material](https://github.com/squidfunk/mkdocs-material) | `9.6.18` | `9.6.21` |
| [mkdocstrings](https://github.com/mkdocstrings/mkdocstrings) | `0.30.0` | `0.30.1` |
| [pandas](https://github.com/pandas-dev/pandas) | `2.3.2` | `2.3.3` |
| [pubchempy](https://github.com/mcs07/PubChemPy) | `1.0.4` | `1.0.5` |
| [pydantic](https://github.com/pydantic/pydantic) | `2.11.7` | `2.11.9` |
| [pymilvus](https://github.com/milvus-io/pymilvus) | `2.6.1` | `2.6.2` |
| [pypdf](https://github.com/py-pdf/pypdf) | `6.0.0` | `6.1.1` |
| [pytest](https://github.com/pytest-dev/pytest) | `8.4.1` | `8.4.2` |
| [pyzotero](https://github.com/urschrei/pyzotero) | `1.6.11` | `1.6.16` |
| [scipy](https://github.com/scipy/scipy) | `1.16.1` | `1.16.2` |
| [streamlit](https://github.com/streamlit/streamlit) | `1.49.1` | `1.50.0` |
| [xlsxwriter](https://github.com/jmcnamara/XlsxWriter) | `3.2.5` | `3.2.9` |
| [datasets](https://github.com/huggingface/datasets) | `4.0.0` | `4.1.1` |
| [beautifulsoup4](https://www.crummy.com/software/BeautifulSoup/bs4/) | `4.13.5` | `4.14.2` |
| [azure-identity](https://github.com/Azure/azure-sdk-for-python) | `1.24.0` | `1.25.0` |
| [ruff](https://github.com/astral-sh/ruff) | `0.12.11` | `0.13.2` |
| [mypy](https://github.com/python/mypy) | `1.17.1` | `1.18.2` |
| [safety](https://github.com/pyupio/safety) | `3.2.9` | `3.6.2` |
| [twine](https://github.com/pypa/twine) | `6.1.0` | `6.2.0` |

Updates `coverage` from 7.10.6 to 7.10.7
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/nedbat/coveragepy/blob/master/CHANGES.rst">coverage's changelog</a>.</em></p>
<blockquote>
<h2>Version 7.10.7 — 2025-09-21</h2>
<ul>
<li>
<p>Performance: with branch coverage in large files, generating HTML, JSON, or
LCOV reports could take far too long due to some quadratic behavior when
creating the function and class index pages.  This is now fixed, closing
<code>issue 2048</code>_.  Thanks to Daniel Diniz for help diagnosing the problem.</p>
</li>
<li>
<p>Most warnings and a few errors now have links to a page in the docs
explaining the specific message.  Closes <code>issue 1921</code>_.</p>
</li>
</ul>
<p>.. _issue 1921: <a href="">nedbat/coveragepy#1921</a>
.. _issue 2048: <a href="">nedbat/coveragepy#2048</a></p>
<p>.. _changes_7-10-6:</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>92a2af5</code></a> docs: sample HTML for 7.10.7</li>
<li><a href=""><code>952afda</code></a> docs: prep for 7.10.7</li>
<li><a href=""><code>a301761</code></a> build: riscv64 wheels (<a href="">#2055</a>)</li>
<li><a href=""><code>5daff8d</code></a> docs: now source is formatted with ruff</li>
<li><a href=""><code>04bbc3a</code></a> docs: discuss cog in the contributing docs</li>
<li><a href=""><code>c181b93</code></a> build: use cog --check-fail-msg to instruct devs</li>
<li><a href=""><code>33c4ba1</code></a> chore: make upgrade</li>
<li><a href=""><code>0744b73</code></a> chore: bump the action-dependencies group across 1 directory with 2 updates (...</li>
<li><a href=""><code>0d5a112</code></a> perf: bulk narrowing to avoid N**2. <a href="">#2048</a></li>
<li><a href=""><code>a868ed9</code></a> docs: mention Python Discord on the index page</li>
<li>Additional commits viewable in <a href="https://github.com/nedbat/coveragepy/compare/7.10.6...7.10.7">compare view</a></li>
</ul>
</details>
<br />

Updates `gseapy` from 1.1.9 to 1.1.10
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/zqfang/GSEApy/releases">gseapy's releases</a>.</em></p>
<blockquote>
<h2>gseapy-v1.1.10</h2>
<p>Bump version</p>
<ul>
<li>support py3.14 and drop py3.7</li>
<li>Fix potential filtering error, <a href="">#315</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/zqfang/GSEApy/compare/v1.1.9...v1.1.10">https://github.com/zqfang/GSEApy/compare/v1.1.9...v1.1.10</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>051e760</code></a> bump version</li>
<li><a href=""><code>0ef0f13</code></a> python3.14 support</li>
<li><a href=""><code>25f902b</code></a> fix filter, <a href="">#315</a></li>
<li>See full diff in <a href="https://github.com/zqfang/GSEApy/compare/v1.1.9...v1.1.10">compare view</a></li>
</ul>
</details>
<br />

Updates `mkdocs-include-markdown-plugin` from 7.1.7 to 7.2.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/mondeja/mkdocs-include-markdown-plugin/releases">mkdocs-include-markdown-plugin's releases</a>.</em></p>
<blockquote>
<h2>v7.2.0</h2>
<h2>New features</h2>
<ul>
<li>Add new argument <code>order</code> to sort multiple inclusions.</li>
</ul>
<h2>v7.1.8</h2>
<h2>Bug fixes</h2>
<ul>
<li>Escape substitution placeholders to prevent malformed output in edge cases.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>708a374</code></a> Add new argument <code>order</code> to sort inclusions (<a href="">#279</a>)</li>
<li><a href=""><code>8b77f66</code></a> Add a security policy (<a href="">#278</a>)</li>
<li><a href=""><code>7466d67</code></a> Escape placeholders to avoid input collisions (<a href="">#277</a>)</li>
<li><a href=""><code>1ae8fca</code></a> Cheaper placeholders (<a href="">#276</a>)</li>
<li><a href=""><code>39fb303</code></a> Fix tests for <code>comments</code> global config and update JSON Schema (<a href="">#275</a>)</li>
<li><a href=""><code>6581671</code></a> Bump pypa/gh-action-pypi-publish in /.github/workflows (<a href="">#273</a>)</li>
<li>See full diff in <a href="https://github.com/mondeja/mkdocs-include-markdown-plugin/compare/v7.1.7...v7.2.0">compare view</a></li>
</ul>
</details>
<br />

Updates `mkdocs-material` from 9.6.18 to 9.6.21
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/squidfunk/mkdocs-material/releases">mkdocs-material's releases</a>.</em></p>
<blockquote>
<h2>mkdocs-material-9.6.21</h2>
<ul>
<li>Updated Serbian translations</li>
<li>Fixed <a href="">#8458</a>: Temporary pin of click dependency</li>
</ul>
<h2>mkdocs-material-9.6.20</h2>
<ul>
<li>Fixed <a href="">#8446</a>: Deprecation warning as of Python 3.14 in Emoji extension</li>
<li>Fixed <a href="">#8440</a>: <code>&amp;</code> character not escaped in search highlighting</li>
<li>Fixed <a href="">#8439</a>: FontAwesome icons color not set in social cards (regression)</li>
</ul>
<h2>mkdocs-material-9.6.19</h2>
<ul>
<li>Added support for Python 3.14</li>
<li>Updated Bahasa Malaysia translations</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/squidfunk/mkdocs-material/blob/master/CHANGELOG">mkdocs-material's changelog</a>.</em></p>
<blockquote>
<p>mkdocs-material-9.6.21 (2025-09-30)</p>
<ul>
<li>Updated Serbian translations</li>
<li>Fixed <a href="">#8458</a>: Temporary pin of click dependency</li>
</ul>
<p>mkdocs-material-9.6.20 (2025-09-15)</p>
<ul>
<li>Fixed <a href="">#8446</a>: Deprecation warning as of Python 3.14 in Emoji extension</li>
<li>Fixed <a href="">#8440</a>: <code>&amp;</code> character not escaped in search highlighting</li>
<li>Fixed <a href="">#8439</a>: FontAwesome icons color not set in social cards (regression)</li>
</ul>
<p>mkdocs-material-9.6.19 (2025-09-07)</p>
<ul>
<li>Added support for Python 3.14</li>
<li>Updated Bahasa Malaysia translations</li>
</ul>
<p>mkdocs-material-9.6.18 (2025-08-22)</p>
<ul>
<li>Updated Azerbaijani translations</li>
<li>Fixed last compat issues with [minijinja], now 100% compatible</li>
</ul>
<p>mkdocs-material-9.6.17 (2025-08-15)</p>
<ul>
<li>Fixed <a href="">#8396</a>: Videos do not autoplay when inside a content tab</li>
<li>Fixed <a href="">#8394</a>: Stroke width not effective in Mermaid.js diagrams</li>
<li>Fixed disappearing version selector when hiding page title</li>
</ul>
<p>mkdocs-material-9.6.16 (2025-07-26)</p>
<ul>
<li>Fixed <a href="">#8349</a>: Info plugin doesn't correctly detect virtualenv in some cases</li>
<li>Fixed <a href="">#8334</a>: Find-in-page detects matches in hidden search result list</li>
</ul>
<p>mkdocs-material-9.6.15 (2025-07-01)</p>
<ul>
<li>Updated Mongolian translations</li>
<li>Improved semantic markup of &quot;edit this page&quot; button</li>
<li>Improved info plugin virtual environment resolution</li>
<li>Fixed <a href="">#8291</a>: Large font size setting throws of breakpoints in JavaScript</li>
</ul>
<p>mkdocs-material-9.6.14 (2025-05-13)</p>
<ul>
<li>Fixed <a href="">#8215</a>: Social plugin crashes when CairoSVG is updated to 2.8</li>
</ul>
<p>mkdocs-material-9.6.13 (2025-05-10)</p>
<ul>
<li>Fixed <a href="">#8204</a>: Annotations showing list markers in print view</li>
<li>Fixed <a href="">#8153</a>: Improve style of cardinality symbols in Mermaid.js ER diagrams</li>
</ul>
<p>mkdocs-material-9.6.12 (2025-04-17)</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f7cacc0</code></a> Prepare 9.6.21 release</li>
<li><a href=""><code>6f715fb</code></a> Unpinned click</li>
<li><a href=""><code>97e275c</code></a> Updated Serbian languages (<a href="">#8445</a>)</li>
<li><a href=""><code>f0b0b59</code></a> Prepare 9.6.20 release</li>
<li><a href=""><code>900981b</code></a> Fixed deprecation warning as of Python 3.14 in Emoji extension</li>
<li><a href=""><code>ed00263</code></a> Documentation (<a href="">#8443</a>)</li>
<li><a href=""><code>a4f42bb</code></a> Updated Premium sponsors</li>
<li><a href=""><code>63d7e74</code></a> Fixed FontAwesome icons having fill attributes</li>
<li><a href=""><code>ee67845</code></a> Fixed &amp; not escaped in search highlighting</li>
<li><a href=""><code>2fe55ee</code></a> Prepare 9.6.19 release</li>
<li>Additional commits viewable in <a href="https://github.com/squidfunk/mkdocs-material/compare/9.6.18...9.6.21">compare view</a></li>
</ul>
</details>
<br />

Updates `mkdocstrings` from 0.30.0 to 0.30.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/mkdocstrings/mkdocstrings/releases">mkdocstrings's releases</a>.</em></p>
<blockquote>
<h2>0.30.1</h2>
<h2><a href="https://github.com/mkdocstrings/mkdocstrings/releases/tag/0.30.1">0.30.1</a> - 2025-09-19</h2>
<p><!-- raw HTML omitted --><a href="https://github.com/mkdocstrings/mkdocstrings/compare/0.30.0...0.30.1">Compare with 0.30.0</a><!-- raw HTML omitted --></p>
<h3>Bug Fixes</h3>
<ul>
<li>Create default SSL context in main thread before downloading inventories (<a href="">eec7fb4</a> by Çağlar Kutlu). <a href="https://redirect.github.com/mkdocstrings/mkdocstrings/issue/796">Issue-796</a>, <a href="">PR-797</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/mkdocstrings/mkdocstrings/blob/main/CHANGELOG.md">mkdocstrings's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/mkdocstrings/mkdocstrings/releases/tag/0.30.1">0.30.1</a> - 2025-09-19</h2>
<p><!-- raw HTML omitted --><a href="https://github.com/mkdocstrings/mkdocstrings/compare/0.30.0...0.30.1">Compare with 0.30.0</a><!-- raw HTML omitted --></p>
<h3>Bug Fixes</h3>
<ul>
<li>Create default SSL context in main thread before downloading inventories (<a href="">eec7fb4</a> by Çağlar Kutlu). <a href="https://redirect.github.com/mkdocstrings/mkdocstrings/issue/796">Issue-796</a>, <a href="">PR-797</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b550cdb</code></a> chore: Prepare release 0.30.1</li>
<li><a href=""><code>18f6504</code></a> ci: Fix warning</li>
<li><a href=""><code>eec7fb4</code></a> fix: Create default SSL context in main thread before downloading inventories</li>
<li><a href=""><code>5726771</code></a> doc: Add links to MATLAB handler</li>
<li><a href=""><code>85f4479</code></a> docs: Fix broken NVidia link in README</li>
<li>See full diff in <a href="https://github.com/mkdocstrings/mkdocstrings/compare/0.30.0...0.30.1">compare view</a></li>
</ul>
</details>
<br />

Updates `pandas` from 2.3.2 to 2.3.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pandas-dev/pandas/releases">pandas's releases</a>.</em></p>
<blockquote>
<h2>Pandas 2.3.3</h2>
<p>We are pleased to announce the release of pandas 2.3.3.
This release includes some improvements and fixes to the future string data type (preview feature for the upcoming pandas 3.0). We recommend that all users upgrade to this version.</p>
<p>See the <a href="https://pandas.pydata.org/pandas-docs/version/2.3/whatsnew/v2.3.3.html">full whatsnew</a> for a list of all the changes.
Pandas 2.3.3 supports Python 3.9 and higher, and is the first release to support Python 3.14.</p>
<p>The release will be available on the conda-forge channel:</p>
<pre><code>conda install pandas --channel conda-forge
</code></pre>
<p>Or via PyPI:</p>
<pre><code>python3 -m pip install --upgrade pandas
</code></pre>
<p>Please report any issues with the release on the <a href="https://github.com/pandas-dev/pandas/issues">pandas issue tracker</a>.</p>
<p>Thanks to all the contributors who made this release possible.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9c8bc3e</code></a> RLS: 2.3.3</li>
<li><a href=""><code>6aa788a</code></a> [backport 2.3.x] DOC: prepare 2.3.3 whatsnew notes for release (<a href="">#62499</a>) (<a href="">#62508</a>)</li>
<li><a href=""><code>b64f0df</code></a> [backport 2.3.x] BUG: avoid validation error for ufunc with string[python] ar...</li>
<li><a href=""><code>058eb2b</code></a> [backport 2.3.x] BUG: String[pyarrow] comparison with mixed object (<a href="">#62424</a>) (...</li>
<li><a href=""><code>2ca088d</code></a> [backport 2.3.x] DEPR: remove the Period resampling deprecation (<a href="">#62480</a>) (<a href="">#62</a>...</li>
<li><a href=""><code>92bf98f</code></a> [backport 2.3.x] BUG: fix .str.isdigit to honor unicode superscript for older...</li>
<li><a href=""><code>e57c7d6</code></a> Backport PR <a href="">#62452</a> on branch 2.3.x (TST: Adjust tests for numexpr 2.13) (<a href="">#62454</a>)</li>
<li><a href=""><code>e0fe9a0</code></a> Backport to 2.3.x: REGR: from_records not initializing subclasses properly (#...</li>
<li><a href=""><code>23a1085</code></a> BUG: improve future warning for boolean operations with missaligned indexes (...</li>
<li><a href=""><code>6113696</code></a> Backport PR <a href="">#62396</a> on branch 2.3.x (PKG/DOC: indicate Python 3.14 support in ...</li>
<li>Additional commits viewable in <a href="https://github.com/pandas-dev/pandas/compare/v2.3.2...v2.3.3">compare view</a></li>
</ul>
</details>
<br />

Updates `pubchempy` from 1.0.4 to 1.0.5
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/mcs07/PubChemPy/releases">pubchempy's releases</a>.</em></p>
<blockquote>
<h2>PubChemPy 1.0.5</h2>
<h2>What's Changed</h2>
<ul>
<li>Fix 'is not' with a literal' by <a href="https://github.com/mehr-licht"><code>@​mehr-licht</code></a> in <a href="">mcs07/PubChemPy#53</a></li>
<li>update print instructions in the documentation by <a href="https://github.com/nbehrnd"><code>@​nbehrnd</code></a> in <a href="">mcs07/PubChemPy#58</a></li>
<li>update/adjustment of notebooks to Python 3 by <a href="https://github.com/nbehrnd"><code>@​nbehrnd</code></a> in <a href="">mcs07/PubChemPy#65</a></li>
<li>Add .gitignore file by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#105</a></li>
<li>Remove non-functioning Travis CI by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#106</a></li>
<li>Modernize python packaging by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#108</a></li>
<li>Fix documentation build by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#109</a></li>
<li>Adjust readthedocs.yaml config by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#110</a></li>
<li>Fix readthedocs environment by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#111</a></li>
<li>Better dev tooling by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#112</a></li>
<li>Fix regex to use raw string by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#113</a></li>
<li>API Change for SMILES types by <a href="https://github.com/aidandj"><code>@​aidandj</code></a> in <a href="">mcs07/PubChemPy#102</a></li>
<li>Further updates for SMILES API changes by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#114</a></li>
<li>Further refinement of new SMILES API by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#115</a></li>
<li>Rename default branch to main by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#116</a></li>
<li>Fix missing namespace in docs search example by <a href="https://github.com/bertiewooster"><code>@​bertiewooster</code></a> in <a href="">mcs07/PubChemPy#78</a></li>
<li>Fix to_dict for substances lacking any compound record by <a href="https://github.com/HYUNSEONG-KIM"><code>@​HYUNSEONG-KIM</code></a> in <a href="">mcs07/PubChemPy#60</a></li>
<li>Better CAS registry numbers docs and notebook by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#117</a></li>
<li>Allow using Mozilla certifi package or custom SSL certs by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#118</a></li>
<li>Fix mol weight float prop types by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#120</a></li>
<li>Fix failing tests due to data changes by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#121</a></li>
<li>Rate-limit tests by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#122</a></li>
<li>Add GitHub Actions CI to run tests by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#123</a></li>
<li>Better error handling by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#124</a></li>
<li>Update docs URLs by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#125</a></li>
<li>Remove python 2 support by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#126</a></li>
<li>Remove wildcard imports in tests by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#127</a></li>
<li>Better enum constants and API docs by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#128</a></li>
<li>Further attempt to fix flaky tests by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#129</a></li>
<li>Formatting, pre-commit, docs by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#130</a></li>
<li>Fix synonyms test by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#131</a></li>
<li>pytest rerun URLError by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#132</a></li>
<li>Documentation improvements by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#134</a></li>
<li>Pathlib support for download function by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#135</a></li>
<li>Update docs URLs to pubchempy.org by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#136</a></li>
<li>README update and other tidying by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#137</a></li>
<li>Add codemeta.json and CITATION.cff by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#139</a></li>
<li>Add conda instructions to README by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#140</a></li>
<li>Tweak README badges by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#141</a></li>
<li>Add code check CI by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#142</a></li>
<li>Add workflow for publishing to PyPI by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#147</a></li>
<li>Bump version 1.0.4 =&gt; 1.0.5 by <a href="https://github.com/mcs07"><code>@​mcs07</code></a> in <a href="">mcs07/PubChemPy#146</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/mehr-licht"><code>@​mehr-licht</code></a> made their first contribution in <a href="">mcs07/PubChemPy#53</a></li>
<li><a href="https://github.com/nbehrnd"><code>@​nbehrnd</code></a> made their first contribution in <a href="">mcs07/PubChemPy#58</a></li>
<li><a href="https://github.com/aidandj"><code>@​aidandj</code></a> made their first contribution in <a href="">mcs07/PubChemPy#102</a></li>
<li><a href="https://github.com/bertiewooster"><code>@​bertiewooster</code></a> made their first contribution in <a href="">mcs07/PubChemPy#78</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9935a14</code></a> Bump version 1.0.4 =&gt; 1.0.5 (<a href="">#146</a>)</li>
<li><a href=""><code>0d169bd</code></a> Add workflow for publishing to PyPI (<a href="">#147</a>)</li>
<li><a href=""><code>a5d8646</code></a> Add code check CI (<a href="">#142</a>)</li>
<li><a href=""><code>acab904</code></a> Tweak README badges (<a href="">#141</a>)</li>
<li><a href=""><code>21355e5</code></a> Add conda instructions to README (<a href="">#140</a>)</li>
<li><a href=""><code>1f65a0b</code></a> Add codemeta.json and CITATION.cff (<a href="">#139</a>)</li>
<li><a href=""><code>4a58fc3</code></a> README update and other tidying (<a href="">#137</a>)</li>
<li><a href=""><code>1371248</code></a> Update docs URLs to pubchempy.org (<a href="">#136</a>)</li>
<li><a href=""><code>a2adbc3</code></a> Pathlib support for download function (<a href="">#135</a>)</li>
<li><a href=""><code>dced9e4</code></a> Documentation improvements (<a href="">#134</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/mcs07/PubChemPy/compare/v1.0.4...v1.0.5">compare view</a></li>
</ul>
</details>
<br />

Updates `pydantic` from 2.11.7 to 2.11.9
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pydantic/pydantic/releases">pydantic's releases</a>.</em></p>
<blockquote>
<h2>v2.11.9 2025-09-13</h2>
<h3>What's Changed</h3>
<h4>Fixes</h4>
<ul>
<li>Backport v1.10.23 changes by <a href="https://github.com/Viicos"><code>@​Viicos</code></a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/pydantic/pydantic/compare/v2.11.8...v2.11.9">https://github.com/pydantic/pydantic/compare/v2.11.8...v2.11.9</a></p>
<h2>v2.11.8 2025-09-13</h2>
<h2>v2.11.8 (2025-09-13)</h2>
<h3>What's Changed</h3>
<h4>Fixes</h4>
<ul>
<li>Fix mypy plugin for mypy 1.18 by <a href="https://github.com/cdce8p"><code>@​cdce8p</code></a> in <a href="">#12209</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/pydantic/pydantic/compare/v2.11.7...v2.11.8">https://github.com/pydantic/pydantic/compare/v2.11.7...v2.11.8</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pydantic/pydantic/blob/v2.11.9/HISTORY.md">pydantic's changelog</a>.</em></p>
<blockquote>
<h2>v2.11.9 (2025-09-13)</h2>
<p><a href="https://github.com/pydantic/pydantic/releases/tag/v2.11.9">GitHub release</a></p>
<h3>What's Changed</h3>
<h4>Fixes</h4>
<ul>
<li>Backport v1.10.23 changes by <a href="https://github.com/Viicos"><code>@​Viicos</code></a></li>
</ul>
<h2>v2.11.8 (2025-09-13)</h2>
<p><a href="https://github.com/pydantic/pydantic/releases/tag/v2.11.8">GitHub release</a></p>
<h3>What's Changed</h3>
<h4>Fixes</h4>
<ul>
<li>Fix mypy plugin for mypy 1.18 by <a href="https://github.com/cdce8p"><code>@​cdce8p</code></a> in <a href="">#12209</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9231095</code></a> Prepare release v2.11.9</li>
<li><a href=""><code>f003a89</code></a> Backport v1.10.23 changes</li>
<li><a href=""><code>96b81dd</code></a> Prepare release v2.11.8</li>
<li><a href=""><code>966f377</code></a> Fix mypy v2 plugin for upcoming <code>1.18</code> mypy release</li>
<li>See full diff in <a href="https://github.com/pydantic/pydantic/compare/v2.11.7...v2.11.9">compare view</a></li>
</ul>
</details>
<br />

Updates `pymilvus` from 2.6.1 to 2.6.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/milvus-io/pymilvus/releases">pymilvus's releases</a>.</em></p>
<blockquote>
<h2>PyMilvus v2.6.2 Release Notes</h2>
<h2>What's Changed</h2>
<ul>
<li>fix: Refine partial upsert to preserve unspecified fields (<a href="">#2955</a>) by <a href="https://github.com/weiliu1031"><code>@​weiliu1031</code></a> in <a href="">milvus-io/pymilvus#2970</a></li>
<li>fix: Correct validation logic for partial upsert requests (<a href="">#2974</a>) by <a href="https://github.com/weiliu1031"><code>@​weiliu1031</code></a> in <a href="">milvus-io/pymilvus#2977</a></li>
<li>feat: support group by json field(<a href="">#2884</a>) by <a href="https://github.com/MrPresent-Han"><code>@​MrPresent-Han</code></a> in <a href="">milvus-io/pymilvus#2980</a></li>
<li>enhance: [2.6]Run actions when push to repo to enable cov compare by <a href="https://github.com/XuanYang-cn"><code>@​XuanYang-cn</code></a> in <a href="">milvus-io/pymilvus#2969</a></li>
<li>support connectType if use oss-bucket by <a href="https://github.com/lentitude2tk"><code>@​lentitude2tk</code></a> in <a href="">milvus-io/pymilvus#2988</a></li>
<li>enhance: Sync PyMilvus milvus-proto commit to v2.6.2 by <a href="https://github.com/XuanYang-cn"><code>@​XuanYang-cn</code></a> in <a href="">milvus-io/pymilvus#2995</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/milvus-io/pymilvus/compare/v2.6.1...v2.6.2">https://github.com/milvus-io/pymilvus/compare/v2.6.1...v2.6.2</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e9fbd2d</code></a> enhance: Sync PyMilvus milvus-proto commit to v2.6.2 (<a href="">#2995</a>)</li>
<li><a href=""><code>9d2556a</code></a> [cherry-pick] support connectType if use oss-bucket (<a href="">#2988</a>)</li>
<li><a href=""><code>8b09a7c</code></a> enhance: [2.6]Run actions when push to repo to enable cov compare (<a href="">#2969</a>)</li>
<li><a href=""><code>6bdb7a5</code></a> feat: support group by json field(<a href="">#2884</a>) (<a href="">#2980</a>)</li>
<li><a href=""><code>8c0a472</code></a> fix: Correct validation logic for partial upsert requests (<a href="">#2974</a>) (<a href="">#2977</a>)</li>
<li><a href=""><code>dfde56d</code></a> fix: Refine partial upsert to preserve unspecified fields (<a href="">#2955</a>) (<a href="">#2970</a>)</li>
<li>See full diff in <a href="https://github.com/milvus-io/pymilvus/compare/v2.6.1...v2.6.2">compare view</a></li>
</ul>
</details>
<br />

Updates `pypdf` from 6.0.0 to 6.1.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/py-pdf/pypdf/releases">pypdf's releases</a>.</em></p>
<blockquote>
<h2>Version 6.1.1, 2025-09-28</h2>
<h2>What's new</h2>
<h3>Bug Fixes (BUG)</h3>
<ul>
<li>Insert new embedded files in a sorted manner (<a href="">#3477</a>) by <a href="https://github.com/stefan6419846"><code>@​stefan6419846</code></a></li>
<li>Fix name tree handling for embedded files with Kids-based inputs (<a href="">#3475</a>) by <a href="https://github.com/stefan6419846"><code>@​stefan6419846</code></a></li>
<li>Make embedding files not break PDF/A-3 compliance (<a href="">#3472</a>) by <a href="https://github.com/stefan6419846"><code>@​stefan6419846</code></a></li>
</ul>
<h3>Documentation (DOC)</h3>
<ul>
<li>Document AFRelationship handling for PDF/A and provide constants (<a href="">#3478</a>) by <a href="https://github.com/stefan6419846"><code>@​stefan6419846</code></a></li>
</ul>
<p><a href="https://github.com/py-pdf/pypdf/compare/6.1.0...6.1.1">Full Changelog</a></p>
<h2>Version 6.1.0, 2025-09-21</h2>
<h2>What's new</h2>
<h3>New Features (ENH)</h3>
<ul>
<li>Enhance XMP metadata handling with creation and setter methods (<a href="">#3410</a>) by <a href="https://github.com/Arya-A-Nair"><code>@​Arya-A-Nair</code></a></li>
<li>Add all font metrics for base 14 Type 1 PDF fonts (<a href="">#3363</a>) by <a href="https://github.com/PJBrs"><code>@​PJBrs</code></a></li>
<li>Allow deleting embedded files (<a href="">#3461</a>) by <a href="https://github.com/stefan6419846"><code>@​stefan6419846</code></a></li>
<li>Add support for Python in FIPS mode for document identifier (<a href="">#3438</a>) by <a href="https://github.com/xnox"><code>@​xnox</code></a></li>
</ul>
<h3>Bug Fixes (BUG)</h3>
<ul>
<li>Fix handling of UTF-16 encoded destination titles (<a href="">#3463</a>) by <a href="https://github.com/stefan6419846"><code>@​stefan6419846</code></a></li>
<li>Guard empty input to prevent IndexError (<a href="">#3448</a>) by <a href="https://github.com/KyleJung0828"><code>@​KyleJung0828</code></a></li>
</ul>
<h3>Developer Experience (DEV)</h3>
<ul>
<li>Fix type hint for XMP metadata setter to add bytes type (<a href="">#3464</a>) by <a href="https://github.com/stefan6419846"><code>@​stefan6419846</code></a></li>
</ul>
<p><a href="https://github.com/py-pdf/pypdf/compare/6.0.0...6.1.0">Full Changelog</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/py-pdf/pypdf/blob/main/CHANGELOG.md">pypdf's changelog</a>.</em></p>
<blockquote>
<h2>Version 6.1.1, 2025-09-28</h2>
<h3>Bug Fixes (BUG)</h3>
<ul>
<li>Insert new embedded files in a sorted manner (<a href="">#3477</a>)</li>
<li>Fix name tree handling for embedded files with Kids-based inputs (<a href="">#3475</a>)</li>
<li>Make embedding files not break PDF/A-3 compliance (<a href="">#3472</a>)</li>
</ul>
<h3>Documentation (DOC)</h3>
<ul>
<li>Document AFRelationship handling for PDF/A and provide constants (<a href="">#3478</a>)</li>
</ul>
<p><a href="https://github.com/py-pdf/pypdf/compare/6.1.0...6.1.1">Full Changelog</a></p>
<h2>Version 6.1.0, 2025-09-21</h2>
<h3>New Features (ENH)</h3>
<ul>
<li>Enhance XMP metadata handling with creation and setter methods (<a href="">#3410</a>)</li>
<li>Add all font metrics for base 14 Type 1 PDF fonts (<a href="">#3363</a>)</li>
<li>Allow deleting embedded files (<a href="">#3461</a>)</li>
<li>Add support for Python in FIPS mode for document identifier (<a href="">#3438</a>)</li>
</ul>
<h3>Bug Fixes (BUG)</h3>
<ul>
<li>Fix handling of UTF-16 encoded destination titles (<a href="">#3463</a>)</li>
<li>Guard empty input to prevent IndexError (<a href="">#3448</a>)</li>
</ul>
<h3>Developer Experience (DEV)</h3>
<ul>
<li>Fix type hint for XMP metadata setter to add bytes type (<a href="">#3464</a>)</li>
</ul>
<p><a href="https://github.com/py-pdf/pypdf/compare/6.0.0...6.1.0">Full Changelog</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9cb878c</code></a> REL: 6.1.1</li>
<li><a href=""><code>5848de3</code></a> DOC: Document AFRelationship handling for PDF/A and provide constants (<a href="">#3478</a>)</li>
<li><a href=""><code>322d810</code></a> STY: Use removeprefix (<a href="">#3469</a>)</li>
<li><a href=""><code>506a110</code></a> BUG: Insert new embedded files in a sorted manner (<a href="">#3477</a>)</li>
<li><a href=""><code>1bb97b9</code></a> MAINT: Correct two misspellings (<a href="">#3476</a>)</li>
<li><a href=""><code>e3a16d4</code></a> BUG: Fix name tree handling for embedded files with Kids-based inputs (<a href="">#3475</a>)</li>
<li><a href=""><code>5c5b3bd</code></a> BUG: Make embedding files not break PDF/A-3 compliance (<a href="">#3472</a>)</li>
<li><a href=""><code>d40f359</code></a> REL: 6.1.0</li>
<li><a href=""><code>27b66aa</code></a> ENH: Enhance XMP metadata handling with creation and setter methods (<a href="">#3410</a>)</li>
<li><a href=""><code>b6fff56</code></a> BUG: Fix handling of UTF-16 encoded destination titles (<a href="">#3463</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/py-pdf/pypdf/compare/6.0.0...6.1.1">compare view</a></li>
</ul>
</details>
<br />

Updates `pytest` from 8.4.1 to 8.4.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest/releases">pytest's releases</a>.</em></p>
<blockquote>
<h2>8.4.2</h2>
<h1>pytest 8.4.2 (2025-09-03)</h1>
<h2>Bug fixes</h2>
<ul>
<li>
<p><a href="">#13478</a>: Fixed a crash when using <code>console_output_style</code>{.interpreted-text role=&quot;confval&quot;} with <code>times</code> and a module is skipped.</p>
</li>
<li>
<p><a href="">#13530</a>: Fixed a crash when using <code>pytest.approx</code>{.interpreted-text role=&quot;func&quot;} and <code>decimal.Decimal</code>{.interpreted-text role=&quot;class&quot;} instances with the <code>decimal.FloatOperation</code>{.interpreted-text role=&quot;class&quot;} trap set.</p>
</li>
<li>
<p><a href="">#13549</a>: No longer evaluate type annotations in Python <code>3.14</code> when inspecting function signatures.</p>
<p>This prevents crashes during module collection when modules do not explicitly use <code>from __future__ import annotations</code> and import types for annotations within a <code>if TYPE_CHECKING:</code> block.</p>
</li>
<li>
<p><a href="">#13559</a>: Added missing [int]{.title-ref} and [float]{.title-ref} variants to the [Literal]{.title-ref} type annotation of the [type]{.title-ref} parameter in <code>pytest.Parser.addini</code>{.interpreted-text role=&quot;meth&quot;}.</p>
</li>
<li>
<p><a href="">#13563</a>: <code>pytest.approx</code>{.interpreted-text role=&quot;func&quot;} now only imports <code>numpy</code> if NumPy is already in <code>sys.modules</code>. This fixes unconditional import behavior introduced in [8.4.0]{.title-ref}.</p>
</li>
</ul>
<h2>Improved documentation</h2>
<ul>
<li><a href="">#13577</a>: Clarify that <code>pytest_generate_tests</code> is discovered in test modules/classes; other hooks must be in <code>conftest.py</code> or plugins.</li>
</ul>
<h2>Contributor-facing changes</h2>
<ul>
<li><a href="">#13480</a>: Self-testing: fixed a few test failures when run with <code>-Wdefault</code> or a similar override.</li>
<li><a href="">#13547</a>: Self-testing: corrected expected message for <code>test_doctest_unexpected_exception</code> in Python <code>3.14</code>.</li>
<li><a href="">#13684</a>: Make pytest's own testsuite insensitive to the presence of the <code>CI</code> environment variable -- by <code>ogrisel</code>{.interpreted-text role=&quot;user&quot;}.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>bfae422</code></a> Prepare release version 8.4.2</li>
<li><a href=""><code>8990538</code></a> Fix passenv CI in tox ini and make tests insensitive to the presence of the C...</li>
<li><a href=""><code>ca676bf</code></a> Merge pull request <a href="">#13687</a> from pytest-dev/patchback/backports/8.4.x/e63f6e51c...</li>
<li><a href=""><code>975a60a</code></a> Merge pull request <a href="">#13686</a> from pytest-dev/patchback/backports/8.4.x/12bde8af6...</li>
<li><a href=""><code>7723ce8</code></a> Merge pull request <a href="">#13683</a> from even-even/fix_Exeption_to_Exception_in_errorMe...</li>
<li><a href=""><code>b7f0568</code></a> Merge pull request <a href="">#13685</a> from CoretexShadow/fix/docs-pytest-generate-tests</li>
<li><a href=""><code>2c94c4a</code></a> add missing colon (<a href="">#13640</a>) (<a href="">#13641</a>)</li>
<li><a href=""><code>c3d7684</code></a> Merge pull request <a href="">#13606</a> from pytest-dev/patchback/backports/8.4.x/5f9938563...</li>
<li><a href=""><code>dc6e3be</code></a> Merge pull request <a href="">#13605</a> from The-Compiler/training-update-2025-07</li>
<li><a href=""><code>f87289c</code></a> Fix crash with <code>times</code> output style and skipped module (<a href="">#13573</a>) (<a href="">#13579</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest/compare/8.4.1...8.4.2">compare view</a></li>
</ul>
</details>
<br />

Updates `pyzotero` from 1.6.11 to 1.6.16
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ed2bc7a</code></a> Merge pull request <a href="">#247</a> from urschrei/shugel/push-mwqsrpultnvq</li>
<li><a href=""><code>3fee58c</code></a> Use a constant for the default item limit</li>
<li><a href=""><code>a102d76</code></a> Merge pull request <a href="">#246</a> from urschrei/shugel/push-kkkmxlzropss</li>
<li><a href=""><code>8f56a6c</code></a> Fix locale parameter being ignored when using add_parameters</li>
<li><a href=""><code>a091179</code></a> Merge pull request <a href="">#245</a> from urschrei/shugel/push-uqllxmvynkmu</li>
<li><a href=""><code>25c3adc</code></a> Better string formatting in doc examples</li>
<li><a href=""><code>c6cb5cc</code></a> Merge pull request <a href="">#244</a> from urschrei/shugel/push-ylpxltsxqyqq</li>
<li><a href=""><code>be3026a</code></a> README install instructions update</li>
<li><a href=""><code>6111ad1</code></a> Merge pull request <a href="">#242</a> from urschrei/dependabot/github_actions/gha-updates-7...</li>
<li><a href=""><code>7a8b4c8</code></a> Bump the gha-updates group with 2 updates</li>
<li>Additional commits viewable in <a href="https://github.com/urschrei/pyzotero/compare/v1.6.11...v1.6.16">compare view</a></li>
</ul>
</details>
<br />

Updates `scipy` from 1.16.1 to 1.16.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/scipy/scipy/releases">scipy's releases</a>.</em></p>
<blockquote>
<h1>SciPy 1.16.2 Release Notes</h1>
<p>SciPy <code>1.16.2</code> is a bug-fix release with no new features
compared to <code>1.16.1</code>. This is the first stable release of
SciPy to provide Windows on ARM wheels on PyPI.</p>
<h1>Authors</h1>
<ul>
<li>Name (commits)</li>
<li>Dietrich Brunn (1)</li>
<li>Ralf Gommers (6)</li>
<li>Adam Jones (1)</li>
<li>Gleb Khmyznikov (1) +</li>
<li>Jost Migenda (1) +</li>
<li>newyork_loki (1)</li>
<li>Nick ODell (3)</li>
<li>Dimitri Papadopoulos Orfanos (1)</li>
<li>Ilhan Polat (2)</li>
<li>Tyler Reddy (26)</li>
<li>Mugunthan Selvanayagam (1) +</li>
<li>Shuhei Watanabe (1) +</li>
</ul>
<p>A total of 12 people contributed to this release.
People with a &quot;+&quot; by their names contributed a patch for the first time.
This list of names is automatically generated, and may not be fully complete.</p>
<p>The full issue and pull request lists, and the release asset hashes are available
in the associated <code>README.txt</code> file.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b1296b9</code></a> REL: 1.16.2 release commit [wheel build]</li>
<li><a href=""><code>e0ef26f</code></a> Merge pull request <a href="">#23543</a> from tylerjereddy/treddy_backports_1.16.2</li>
<li><a href=""><code>959fc7c</code></a> CI: PR 23543 revisions [wheel build]</li>
<li><a href=""><code>01c9517</code></a> TST: PR 23543 revisions</li>
<li><a href=""><code>c3f4323</code></a> DOC, MAINT: PR 23543 revisions</li>
<li><a href=""><code>381549e</code></a> BUG: fix memory leaks in <code>optimize.nnls</code> and <code>linalg.sqrtm</code> (<a href="">#23563</a>)</li>
<li><a href=""><code>3f48506</code></a> CI: pin scikit-umfpack to 0.3.3 to avoid failures, 0.4.2 is broken. (<a href="">#23576</a>)</li>
<li><a href=""><code>f1c648a</code></a> TST: PR 23543 revisions</li>
<li><a href=""><code>963a466</code></a> CI: bump OpenBLAS version to latest release (0.3.29.265.1)</li>
<li><a href=""><code>57c0b27</code></a> BUG: PR 23543 revisions</li>
<li>Additional commits viewable in <a href="https://github.com/scipy/scipy/compare/v1.16.1...v1.16.2">compare view</a></li>
</ul>
</details>
<br />

Updates `streamlit` from 1.49.1 to 1.50.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/streamlit/streamlit/releases">streamlit's releases</a>.</em></p>
<blockquote>
<h2>1.50.0</h2>
<!-- raw HTML omitted -->
<h2>What's Changed</h2>
<h3>Breaking Changes 🛠</h3>
<ul>
<li>refactor: deprecate kwargs in st.plotly_chart and add config dict instead by <a href="https://github.com/zyfy29"><code>@​zyfy29</code></a> in <a href="">streamlit/streamlit#12291</a></li>
<li>Use <code>key</code> as main identity for <code>st.checkbox</code> &amp; <code>st.toggle</code> by <a href="https://github.com/lukasmasuch"><code>@​lukasmasuch</code></a> in <a href="">streamlit/streamlit#12372</a></li>
<li>Remove <code>**kwargs</code> support from <code>st.write</code> by <a href="https://github.com/lukasmasuch"><code>@​lukasmasuch</code></a> in <a href="">streamlit/streamlit#12375</a></li>
<li>Use <code>key</code> as main identity for <code>st.number_input</code> by <a href="https://github.com/lukasmasuch"><code>@​lukasmasuch</code></a> in <a href="">streamlit/streamlit#12437</a></li>
<li>Use <code>key</code> as main identity for <code>st.text_area</code> &amp; <code>st.text_input</code> by <a href="https://github.com/lukasmasuch"><code>@​lukasmasuch</code></a> in <a href="">streamlit/streamlit#12397</a></li>
</ul>
<h3>New Features 🎉</h3>
<ul>
<li>Add <code>MultiselectColumn</code> for <code>st.dataframe</code> and <code>st.data_editor</code> by <a href="https://github.com/lukasmasuch"><code>@​lukasmasuch</code></a> in <a href="">streamlit/streamlit#9223</a></li>
<li>Add support for source directly in theming font configs by <a href="https://github.com/mayagbarnes"><code>@​mayagbarnes</code></a> in <a href="">streamlit/streamlit#12239</a></li>
<li>[feat] Add <code>default</code> param to <code>st.tabs</code> by <a href="https://github.com/sfc-gh-bnisco"><code>@​sfc-gh-bnisco</code></a> in <a href="">streamlit/streamlit#12313</a></li>
<li>Add <code>border</code> parameter to <code>st.table</code> by <a href="https://github.com/jrieke"><code>@​jrieke</code></a> in <a href="">streamlit/streamlit#11796</a></li>
<li>[feat] Hover, active, focus-visible states for CopyButton by <a href="https://github.com/sfc-gh-bnisco"><code>@​sfc-gh-bnisco</code></a> in <a href="">streamlit/streamlit#12348</a></li>
<li>[AdvancedLayouts] Adds a width parameters to <code>st.line_chart</code>. by <a href="https://github.com/sfc-gh-lwilby"><code>@​sfc-gh-lwilby</code></a> in <a href="">streamlit/streamlit#11923</a></li>
<li>Add main theme color config options by <a href="https://github.com/mayagbarnes"><code>@​mayagbarnes</code></a> in <a href="">streamlit/streamlit#12288</a></li>
<li>Use <code>key</code> as main identity for button widgets by <a href="https://github.com/lukasmasuch"><code>@​lukasmasuch</code></a> in <a href="">streamlit/streamlit#12332</a></li>
<li>Add <code>sort</code> parameter to <code>st.bar_chart</code> by <a href="https://github.com/jrieke"><code>@​jrieke</code></a> in <a href="">streamlit/streamlit#12339</a></li>
<li>Add theme background color config options by <a href="https://github.com/mayagbarnes"><code>@​mayagbarnes</code></a> in <a href="">streamlit/streamlit#12405</a></li>
<li>Add theme text color config options by <a href="https://github.com/mayagbarnes"><code>@​mayagbarnes</code></a> in <a href="">streamlit/streamlit#12438</a></li>
<li>Use <code>key</code> as main identity for <code>st.time_input</code> &amp; <code>st.date_input</code> by <a href="https://github.com/lukasmasuch"><code>@​lukasmasuch</code></a> in <a href="">streamlit/streamlit#12464</a></li>
<li>[feat] Add sample rate parameter to <code>st.audio_input</code> component by <a href="https://github.com/sfc-gh-nbellante"><code>@​sfc-gh-nbellante</code></a> in <a href="">streamlit/streamlit#12272</a></li>
<li>Metric supports numerics like decimal. by <a href="https://github.com/aebrahim"><code>@​aebrahim</code></a> in <a href="">streamlit/streamlit#12377</a></li>
<li>Show slider tick labels on hover by <a href="https://github.com/lukasmasuch"><code>@​lukasmasuch</code></a> in <a href="">streamlit/streamlit#12367</a></li>
<li>[AdvancedLayouts] Add height param to <code>st.graphviz_chart</code> by <a href="https://github.com/sfc-gh-lwilby"><code>@​sfc-gh-lwilby</code></a> in <a href="">streamlit/streamlit#12297</a></li>
<li>Use <code>key</code> as main ident...

_Description has been truncated_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `045bc847ff96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
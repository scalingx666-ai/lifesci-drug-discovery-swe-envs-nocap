# Issue

**Title:** build(deps): bump the uv group across 1 directory with 3 updates

## Description

Bumps the uv group with 3 updates in the / directory: [torch](https://github.com/pytorch/pytorch), [mistune](https://github.com/lepture/mistune) and [soupsieve](https://github.com/facelessuser/soupsieve).

Updates `torch` from 2.12.1 to 2.13.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytorch/pytorch/releases">torch's releases</a>.</em></p>
<blockquote>
<h1>PyTorch 2.13.0 Release Notes</h1>
<ul>
<li><a href="https://github.com/pytorch/pytorch/blob/HEAD/#highlights">Highlights</a></li>
<li><a href="https://github.com/pytorch/pytorch/blob/HEAD/#backwards-incompatible-changes">Backwards Incompatible Changes</a></li>
<li><a href="https://github.com/pytorch/pytorch/blob/HEAD/#deprecations">Deprecations</a></li>
<li><a href="https://github.com/pytorch/pytorch/blob/HEAD/#new-features">New Features</a></li>
<li><a href="https://github.com/pytorch/pytorch/blob/HEAD/#improvements">Improvements</a></li>
<li><a href="https://github.com/pytorch/pytorch/blob/HEAD/#bug-fixes">Bug fixes</a></li>
<li><a href="https://github.com/pytorch/pytorch/blob/HEAD/#performance">Performance</a></li>
<li><a href="https://github.com/pytorch/pytorch/blob/HEAD/#documentation">Documentation</a></li>
<li><a href="https://github.com/pytorch/pytorch/blob/HEAD/#developers">Developers</a></li>
</ul>
<h1>Highlights</h1>
<!-- raw HTML omitted -->
<p>For more details about these highlighted features, you can look at the release blogpost. Below are the full release notes for this release.</p>
<h1>Tracked Regressions</h1>
<h3>ROCm wheels break <code>torch.compile</code> on CPU in environments without a GPU</h3>
<p>Running a <code>torch==2.13.0+rocm7.2</code> wheel in an environment where no GPU is available (<code>torch.cuda.is_available()</code> is <code>False</code>) breaks <code>torch.compile</code> on the CPU path: the first compile raises <code>RuntimeError: Can't detect vectorized ISA for CPU</code> (<a href="">#189194</a>). This is a regression from <code>torch==2.12.1+rocm7.2</code>, which compiles CPU code fine (detecting e.g. <code>VecAVX2</code>) in the same setup. The 2.13 ROCm wheel appears to rely on something present in the ROCm builder image to detect the CPU vectorized ISA, so it works when run on a ROCm image but fails on a plain CPU-only image.</p>
<p>Workaround: run the <code>+rocm</code> wheel on a ROCm image, or install a standard CPU/CUDA build for GPU-less environments.</p>
<h1>Backwards Incompatible Changes</h1>
<ul>
<li>
<p>Stop building CPython 3.13t (free-threaded) binaries (<a href="">#182951</a>)</p>
<p>Upstream <code>pypa/manylinux</code> removed CPython 3.13t (free-threaded) on 2026-05-07, because 3.13t
was experimental and has been superseded by the now-non-experimental CPython 3.14t. As a result,
PyTorch 2.13 no longer ships <code>cp313t</code> wheels (Linux, Triton, and related artifacts). Users on the
free-threaded interpreter should move to Python 3.14t.</p>
<p>PyTorch 2.12:</p>
<pre lang="bash"><code># cp313t (free-threaded 3.13) wheels were available
python3.13t -m pip install torch
</code></pre>
<p>PyTorch 2.13:</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>cf30153</code></a> [release/2.13] Strip +PTX from CUDA arch list on release/RC builds (<a href="">#188914</a>) ...</li>
<li><a href=""><code>3e3e24b</code></a> [release/2.13] Restrict cuda-bindings to Python &lt; 3.15 for CUDA 12.9 builds (...</li>
<li><a href=""><code>7986b06</code></a> [release/2.13] Bump binary build timeout 280 -&gt; 400 minutes (<a href="">#188551</a>)</li>
<li><a href=""><code>0bdbc26</code></a> [release/2.13] Add CUDA 12.9 to TORCH_CUDA_ARCH_LIST tables (<a href="">#188443</a>)</li>
<li><a href=""><code>9cabb45</code></a> [release/2.13] Update manywheel docker image pin to 78e737ad (<a href="">#188409</a>)</li>
<li><a href=""><code>78e737a</code></a> [release/2.13] Revert &quot;Tighten generalized scatter graph target (<a href="">#184075</a>)&quot; (#...</li>
<li><a href=""><code>0bb9b5b</code></a> [release/2.13] Revert &quot;dynamo: round-trip torch.cuda.stream ctx mgr across gr...</li>
<li><a href=""><code>aaac2bf</code></a> [release/2.13] Revert &quot;[Reland] Port D104346887/PR 182675 for index_add fast ...</li>
<li><a href=""><code>9330813</code></a> Fix build_with_debinfo.py broken by CONFIGURE_DEPENDS globbing (<a href="">#188192</a>)</li>
<li><a href=""><code>4e077a7</code></a> Remove setuptools upper bound (<a href="">#188190</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pytorch/pytorch/compare/v2.12.1...v2.13.0">compare view</a></li>
</ul>
</details>
<br />

Updates `mistune` from 3.2.1 to 3.3.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/lepture/mistune/releases">mistune's releases</a>.</em></p>
<blockquote>
<h2>v3.3.0</h2>
<h3>   🐞 Bug Fixes</h3>
<ul>
<li>Resolve O(n^2) DoS in parse_link_text (CWE-400)  -  by <strong>bhanugoudm041</strong> <a href=""><!-- raw HTML omitted -->(b6b49)<!-- raw HTML omitted --></a></li>
<li>Resolve O(n^2) DoS in parse_link_text (CWE-400)-Type handling/testing done  -  by <strong>bhanugoudm041</strong> <a href=""><!-- raw HTML omitted -->(b3af8)<!-- raw HTML omitted --></a></li>
<li><strong>block</strong>: Avoid quadratic ref link scans  -  by <a href="https://github.com/lepture"><code>@​lepture</code></a> <a href=""><!-- raw HTML omitted -->(2b04d)<!-- raw HTML omitted --></a></li>
<li><strong>cli</strong>: Add entrypoint and utf-8 output  -  by <a href="https://github.com/lepture"><code>@​lepture</code></a> <a href=""><!-- raw HTML omitted -->(2f244)<!-- raw HTML omitted --></a></li>
<li><strong>directives</strong>: Constrain include targets  -  by <a href="https://github.com/lepture"><code>@​lepture</code></a> <a href=""><!-- raw HTML omitted -->(1bef3)<!-- raw HTML omitted --></a></li>
<li><strong>formatting</strong>: Avoid quadratic marker scans  -  by <a href="https://github.com/lepture"><code>@​lepture</code></a> <a href=""><!-- raw HTML omitted -->(96d0f)<!-- raw HTML omitted --></a></li>
<li><strong>image</strong>: Validate figure width option  -  by <a href="https://github.com/lepture"><code>@​lepture</code></a> <a href=""><!-- raw HTML omitted -->(e3e51)<!-- raw HTML omitted --></a></li>
<li><strong>inline</strong>: Avoid bracket parsing DoS  -  by <a href="https://github.com/lepture"><code>@​lepture</code></a> <a href=""><!-- raw HTML omitted -->(25f25)<!-- raw HTML omitted --></a></li>
<li><strong>math</strong>: Reject currency patterns and cross-line matches in inline math  -  by <a href="https://github.com/geopanther"><code>@​geopanther</code></a> <a href=""><!-- raw HTML omitted -->(566e1)<!-- raw HTML omitted --></a></li>
<li><strong>math</strong>: Support display and backtick math  -  by <a href="https://github.com/lepture"><code>@​lepture</code></a> <a href=""><!-- raw HTML omitted -->(1141e)<!-- raw HTML omitted --></a></li>
<li><strong>renderer</strong>: Render plugin list and table nodes  -  by <a href="https://github.com/lepture"><code>@​lepture</code></a> <a href=""><!-- raw HTML omitted -->(614b0)<!-- raw HTML omitted --></a></li>
<li><strong>renderer</strong>: Block encoded unsafe URL schemes  -  by <a href="https://github.com/lepture"><code>@​lepture</code></a> <a href=""><!-- raw HTML omitted -->(c7101)<!-- raw HTML omitted --></a></li>
<li><strong>toc</strong>: Avoid generated id collisions  -  by <a href="https://github.com/lepture"><code>@​lepture</code></a> <a href=""><!-- raw HTML omitted -->(c4093)<!-- raw HTML omitted --></a></li>
</ul>
<h3>   🏎 Performance</h3>
<ul>
<li>Improve performance  -  by <a href="https://github.com/lepture"><code>@​lepture</code></a> <a href=""><!-- raw HTML omitted -->(bf95c)<!-- raw HTML omitted --></a></li>
</ul>
<h5>    <a href="https://github.com/lepture/mistune/compare/v3.2.1...v3.3.0">View changes on GitHub</a></h5>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/lepture/mistune/blob/main/docs/changes.rst">mistune's changelog</a>.</em></p>
<blockquote>
<h2>Version 3.3.0</h2>
<p><strong>Released on Jun 21, 2026</strong></p>
<ul>
<li>Improve CommonMark compatibility and parser performance.</li>
<li>Add command line entrypoint with UTF-8 output.</li>
<li>Support display and backtick math.</li>
<li>Render plugin list and table nodes in Markdown renderer.</li>
<li>Escape leading block markers in Markdown renderer.</li>
<li>Fix RST renderer for block quotes nested in lists.</li>
<li>Avoid generated heading ID collisions in TOC.</li>
<li>Harden URL, image, figure, and include directive handling.</li>
<li>Fix quadratic scans in inline links, reference links, and formatting markers.</li>
<li>Fix math escaping, currency pattern matching, and cross-line matching.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>15c3b79</code></a> chore: release 3.3.0</li>
<li><a href=""><code>bdc01ad</code></a> tests: increase run time on pypy</li>
<li><a href=""><code>7cf1814</code></a> tests: increase run time for pypy</li>
<li><a href=""><code>6dfdc3d</code></a> tests: add more tests</li>
<li><a href=""><code>17c50f6</code></a> chore: fix mypy issues</li>
<li><a href=""><code>63abe4b</code></a> chore: use ruff check and format</li>
<li><a href=""><code>e6c1b18</code></a> chore: resolve mypy issues</li>
<li><a href=""><code>dcf8902</code></a> test(math): cover escaped math output</li>
<li><a href=""><code>c4093c4</code></a> fix(toc): avoid generated id collisions</li>
<li><a href=""><code>e3e51de</code></a> fix(image): validate figure width option</li>
<li>Additional commits viewable in <a href="https://github.com/lepture/mistune/compare/v3.2.1...v3.3.0">compare view</a></li>
</ul>
</details>
<br />

Updates `soupsieve` from 2.6 to 2.8.4
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/facelessuser/soupsieve/releases">soupsieve's releases</a>.</em></p>
<blockquote>
<h2>2.8.4</h2>
<ul>
<li><strong>FIX</strong>: Fix another inefficient attribute pattern (<a href="https://github.com/mauriceng98"><code>@​mauriceng98</code></a>).</li>
<li><strong>FIX</strong>: Limit total number of selectors processed in a pattern to prevent massive selector requests (<a href="https://github.com/mauriceng98"><code>@​mauriceng98</code></a>).</li>
</ul>
<h2>2.8.3</h2>
<ul>
<li><strong>FIX</strong>: Fix inefficient attribute pattern.</li>
</ul>
<h2>2.8.2</h2>
<ul>
<li><strong>FIX</strong>: Ensure custom selectors or namespace dictionaries reject non-string keys (<a href="https://github.com/mundanevision20"><code>@​mundanevision20</code></a>).</li>
<li><strong>FIX</strong>: Fix handling of <code>:in-range</code> and <code>:out-of-range</code> with end of year weeks (<a href="https://github.com/mundanevision20"><code>@​mundanevision20</code></a>).</li>
<li><strong>FIX</strong>: Fix a potential infinite loop in the pretty printing debug function (<a href="https://github.com/mundanevision20"><code>@​mundanevision20</code></a>).</li>
</ul>
<h2>2.8.1</h2>
<ul>
<li><strong>FIX</strong>: Changes in tests to accommodate latest Python HTML parser changes.</li>
</ul>
<h2>2.8</h2>
<ul>
<li><strong>NEW</strong>: Drop support for Python 3.8.</li>
<li><strong>NEW</strong>: Add support for Python 3.14.</li>
<li><strong>NEW</strong>: Deploy with PyPI's &quot;Trusted Publisher&quot;.</li>
</ul>
<h2>2.7</h2>
<ul>
<li><strong>NEW</strong>: Add <code>:open</code> pseudo selector.</li>
<li><strong>NEW</strong>: Add <code>:muted</code> pseudo selector.</li>
<li><strong>NEW</strong>: Recognize the following pseudo selectors: <code>:autofill</code>, <code>:buffering</code>, <code>:fullscreen</code>, <code>:picture-in-picture</code>,
<code>:popover-open</code>, <code>:seeking</code>, <code>:stalled</code>, and <code>:volume-locked</code>. These selectors, while recognized, will not match any
element as they require a live environment to check element states and browser states. This just prevents Soup Sieve
from failing when any of these selectors are specified.</li>
<li><strong>NEW</strong>: A number of existing pseudo-classes are no longer noted as experimental.</li>
<li><strong>FIX</strong>: Typing fixes.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>28108ab</code></a> Limit excessive selectors</li>
<li><a href=""><code>ef18872</code></a> Fix test for Windows</li>
<li><a href=""><code>eb43976</code></a> Merge commit from fork</li>
<li><a href=""><code>3a661b2</code></a> Fix typo in pseudo-classes.md (<a href="">#294</a>)</li>
<li><a href=""><code>0cb533d</code></a> Update hatchling version requirement in pyproject.toml (<a href="">#290</a>)</li>
<li><a href=""><code>5aedc41</code></a> Update doc theme</li>
<li><a href=""><code>d7c4784</code></a> Attribute pattern fix (<a href="">#289</a>)</li>
<li><a href=""><code>09e106d</code></a> Fix grammar</li>
<li><a href=""><code>09b2769</code></a> Update docs</li>
<li><a href=""><code>c6e80fc</code></a> Various fixes by <a href="https://github.com/mundanevision20"><code>@​mundanevision20</code></a> (<a href="">#288</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/facelessuser/soupsieve/compare/2.6...2.8.4">compare view</a></li>
</ul>
</details>
<br />

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
- `@dependabot ignore <dependency name> major version` will close this group update PR and stop Dependabot creating any more for the specific dependency's major version (unless you unignore this specific dependency's major version or upgrade to it yourself)
- `@dependabot ignore <dependency name> minor version` will close this group update PR and stop Dependabot creating any more for the specific dependency's minor version (unless you unignore this specific dependency's minor version or upgrade to it yourself)
- `@dependabot ignore <dependency name>` will close this group update PR and stop Dependabot creating any more for the specific dependency (unless you unignore this specific dependency or upgrade to it yourself)
- `@dependabot unignore <dependency name>` will remove all of the ignore conditions of the specified dependency
- `@dependabot unignore <dependency name> <ignore condition>` will remove the ignore condition of the specified dependency and ignore conditions
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/WMD-group/SMACT/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a309ac3fabe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
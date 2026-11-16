# Issue

**Title:** Bump ruff from 0.12.7 to 0.12.11

## Description

Bumps [ruff](https://github.com/astral-sh/ruff) from 0.12.7 to 0.12.11.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/releases">ruff's releases</a>.</em></p>
<blockquote>
<h2>0.12.11</h2>
<h2>Release Notes</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Extend <code>AIR311</code> and <code>AIR312</code> rules (<a href="">#20082</a>)</li>
<li>[<code>airflow</code>] Replace wrong path <code>airflow.io.storage</code> with <code>airflow.io.store</code> (<code>AIR311</code>) (<a href="">#20081</a>)</li>
<li>[<code>flake8-async</code>] Implement <code>blocking-http-call-httpx-in-async-function</code> (<code>ASYNC212</code>) (<a href="">#20091</a>)</li>
<li>[<code>flake8-logging-format</code>] Add auto-fix for f-string logging calls (<code>G004</code>) (<a href="">#19303</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Add autofix for <code>PTH211</code> (<a href="">#20009</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Make <code>PTH100</code> fix unsafe because it can change behavior (<a href="">#20100</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>pyflakes</code>, <code>pylint</code>] Fix false positives caused by <code>__class__</code> cell handling (<code>F841</code>, <code>PLE0117</code>) (<a href="">#20048</a>)</li>
<li>[<code>pyflakes</code>] Fix <code>allowed-unused-imports</code> matching for top-level modules (<code>F401</code>) (<a href="">#20115</a>)</li>
<li>[<code>ruff</code>] Fix false positive for t-strings in <code>default-factory-kwarg</code> (<code>RUF026</code>) (<a href="">#20032</a>)</li>
<li>[<code>ruff</code>] Preserve relative whitespace in multi-line expressions (<code>RUF033</code>) (<a href="">#19647</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>[<code>ruff</code>] Handle empty t-strings in <code>unnecessary-empty-iterable-within-deque-call</code> (<code>RUF037</code>) (<a href="">#20045</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix incorrect <code>D413</code> links in docstrings convention FAQ (<a href="">#20089</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Update links to the table showing the correspondence between <code>os</code> and <code>pathlib</code> (<a href="">#20103</a>)</li>
</ul>
<h2>Contributors</h2>
<ul>
<li><a href="https://github.com/AlexWaygood"><code>@​AlexWaygood</code></a></li>
<li><a href="https://github.com/Avasam"><code>@​Avasam</code></a></li>
<li><a href="https://github.com/BurntSushi"><code>@​BurntSushi</code></a></li>
<li><a href="https://github.com/Gankra"><code>@​Gankra</code></a></li>
<li><a href="https://github.com/Glyphack"><code>@​Glyphack</code></a></li>
<li><a href="https://github.com/JelleZijlstra"><code>@​JelleZijlstra</code></a></li>
<li><a href="https://github.com/Lee-W"><code>@​Lee-W</code></a></li>
<li><a href="https://github.com/MatthewMckee4"><code>@​MatthewMckee4</code></a></li>
<li><a href="https://github.com/MichaReiser"><code>@​MichaReiser</code></a></li>
<li><a href="https://github.com/PrettyWood"><code>@​PrettyWood</code></a></li>
<li><a href="https://github.com/Renkai"><code>@​Renkai</code></a></li>
<li><a href="https://github.com/TaKO8Ki"><code>@​TaKO8Ki</code></a></li>
<li><a href="https://github.com/amyreese"><code>@​amyreese</code></a></li>
<li><a href="https://github.com/carljm"><code>@​carljm</code></a></li>
<li><a href="https://github.com/chirizxc"><code>@​chirizxc</code></a></li>
<li><a href="https://github.com/danparizher"><code>@​danparizher</code></a></li>
<li><a href="https://github.com/dhruvmanila"><code>@​dhruvmanila</code></a></li>
<li><a href="https://github.com/dylwil3"><code>@​dylwil3</code></a></li>
<li><a href="https://github.com/github-actions"><code>@​github-actions</code></a></li>
<li><a href="https://github.com/hamirmahal"><code>@​hamirmahal</code></a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/blob/main/CHANGELOG.md">ruff's changelog</a>.</em></p>
<blockquote>
<h2>0.12.11</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Extend <code>AIR311</code> and <code>AIR312</code> rules (<a href="">#20082</a>)</li>
<li>[<code>airflow</code>] Replace wrong path <code>airflow.io.storage</code> with <code>airflow.io.store</code> (<code>AIR311</code>) (<a href="">#20081</a>)</li>
<li>[<code>flake8-async</code>] Implement <code>blocking-http-call-httpx-in-async-function</code> (<code>ASYNC212</code>) (<a href="">#20091</a>)</li>
<li>[<code>flake8-logging-format</code>] Add auto-fix for f-string logging calls (<code>G004</code>) (<a href="">#19303</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Add autofix for <code>PTH211</code> (<a href="">#20009</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Make <code>PTH100</code> fix unsafe because it can change behavior (<a href="">#20100</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>pyflakes</code>, <code>pylint</code>] Fix false positives caused by <code>__class__</code> cell handling (<code>F841</code>, <code>PLE0117</code>) (<a href="">#20048</a>)</li>
<li>[<code>pyflakes</code>] Fix <code>allowed-unused-imports</code> matching for top-level modules (<code>F401</code>) (<a href="">#20115</a>)</li>
<li>[<code>ruff</code>] Fix false positive for t-strings in <code>default-factory-kwarg</code> (<code>RUF026</code>) (<a href="">#20032</a>)</li>
<li>[<code>ruff</code>] Preserve relative whitespace in multi-line expressions (<code>RUF033</code>) (<a href="">#19647</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>[<code>ruff</code>] Handle empty t-strings in <code>unnecessary-empty-iterable-within-deque-call</code> (<code>RUF037</code>) (<a href="">#20045</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix incorrect <code>D413</code> links in docstrings convention FAQ (<a href="">#20089</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Update links to the table showing the correspondence between <code>os</code> and <code>pathlib</code> (<a href="">#20103</a>)</li>
</ul>
<h2>0.12.10</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>flake8-simplify</code>] Implement fix for <code>maxsplit</code> without separator (<code>SIM905</code>) (<a href="">#19851</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Add fixes for <code>PTH102</code> and <code>PTH103</code> (<a href="">#19514</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>isort</code>] Handle multiple continuation lines after module docstring (<code>I002</code>) (<a href="">#19818</a>)</li>
<li>[<code>pyupgrade</code>] Avoid reporting <code>__future__</code> features as unnecessary when they are used (<code>UP010</code>) (<a href="">#19769</a>)</li>
<li>[<code>pyupgrade</code>] Handle nested <code>Optional</code>s (<code>UP045</code>) (<a href="">#19770</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>[<code>pycodestyle</code>] Make <code>E731</code> fix unsafe instead of display-only for class assignments (<a href="">#19700</a>)</li>
<li>[<code>pyflakes</code>] Add secondary annotation showing previous definition (<code>F811</code>) (<a href="">#19900</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix description of global config file discovery strategy (<a href="">#19188</a>)</li>
<li>Update outdated links to <a href="https://typing.python.org/en/latest/source/stubs.html">https://typing.python.org/en/latest/source/stubs.html</a> (<a href="">#19992</a>)</li>
<li>[<code>flake8-annotations</code>] Remove unused import in example (<code>ANN401</code>) (<a href="">#20000</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c2bc15b</code></a> Bump 0.12.11 (<a href="">#20136</a>)</li>
<li><a href=""><code>e586f6d</code></a> [ty] Benchmarks for problematic implicit instance attributes cases (<a href="">#20133</a>)</li>
<li><a href=""><code>76a6b7e</code></a> [<code>pyflakes</code>] Fix <code>allowed-unused-imports</code> matching for top-level modules (`F4...</li>
<li><a href=""><code>1ce6571</code></a> Move GitLab output rendering to <code>ruff_db</code> (<a href="">#20117</a>)</li>
<li><a href=""><code>d9aaacd</code></a> [ty] Evaluate reachability of non-definitely-bound to Ambiguous (<a href="">#19579</a>)</li>
<li><a href=""><code>18eaa65</code></a> [ty] Introduce a representation for the top/bottom materialization of an inva...</li>
<li><a href=""><code>af259fa</code></a> [<code>flake8-async</code>] Implement <code>blocking-http-call-httpx</code> (<code>ASYNC212</code>) (<a href="">#20091</a>)</li>
<li><a href=""><code>d75ef38</code></a> [ty] print diagnostics with fully qualified name to disambiguate some cases (...</li>
<li><a href=""><code>89ca493</code></a> [<code>ruff</code>] Preserve relative whitespace in multi-line expressions (<code>RUF033</code>) (#...</li>
<li><a href=""><code>4b80f5f</code></a> [ty] Optimize TDD atom ordering (<a href="">#20098</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/ruff/compare/0.12.7...0.12.11">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruff&package-manager=pip&previous-version=0.12.7&new-version=0.12.11)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a3db29ad59d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
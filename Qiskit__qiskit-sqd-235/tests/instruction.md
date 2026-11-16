# Issue

**Title:** Bump ruff from 0.12.1 to 0.12.7

## Description

Bumps [ruff](https://github.com/astral-sh/ruff) from 0.12.1 to 0.12.7.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/releases">ruff's releases</a>.</em></p>
<blockquote>
<h2>0.12.7</h2>
<h2>Release Notes</h2>
<p>This is a follow-up release to 0.12.6. Because of an issue in the package metadata, 0.12.6 failed to publish fully to PyPI and has been yanked. Similarly, there is no GitHub release or Git tag for 0.12.6. The contents of the 0.12.7 release are identical to 0.12.6, except for the updated metadata.</p>
<h2>0.12.6 Release Notes</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>flake8-commas</code>] Add support for trailing comma checks in type parameter lists (<code>COM812</code>, <code>COM819</code>) (<a href="">#19390</a>)</li>
<li>[<code>pylint</code>] Implement auto-fix for <code>missing-maxsplit-arg</code> (<code>PLC0207</code>) (<a href="">#19387</a>)</li>
<li>[<code>ruff</code>] Offer fixes for <code>RUF039</code> in more cases (<a href="">#19065</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Support <code>.pyi</code> files in ruff analyze graph (<a href="">#19611</a>)</li>
<li>[<code>flake8-pyi</code>] Preserve inline comment in ellipsis removal (<code>PYI013</code>) (<a href="">#19399</a>)</li>
<li>[<code>perflint</code>] Ignore rule if target is <code>global</code> or <code>nonlocal</code> (<code>PERF401</code>) (<a href="">#19539</a>)</li>
<li>[<code>pyupgrade</code>] Fix <code>UP030</code> to avoid modifying double curly braces in format strings (<a href="">#19378</a>)</li>
<li>[<code>refurb</code>] Ignore decorated functions for <code>FURB118</code> (<a href="">#19339</a>)</li>
<li>[<code>refurb</code>] Mark <code>int</code> and <code>bool</code> cases for <code>Decimal.from_float</code> as safe fixes (<code>FURB164</code>) (<a href="">#19468</a>)</li>
<li>[<code>ruff</code>] Fix <code>RUF033</code> for named default expressions (<a href="">#19115</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>[<code>flake8-blind-except</code>] Change <code>BLE001</code> to permit <code>logging.critical(..., exc_info=True)</code> (<a href="">#19520</a>)</li>
</ul>
<h3>Performance</h3>
<ul>
<li>Add support for specifying minimum dots in detected string imports (<a href="">#19538</a>)</li>
</ul>
<h2>Contributors</h2>
<ul>
<li><a href="https://github.com/AlexWaygood"><code>@​AlexWaygood</code></a></li>
<li><a href="https://github.com/BurntSushi"><code>@​BurntSushi</code></a></li>
<li><a href="https://github.com/CodeMan62"><code>@​CodeMan62</code></a></li>
<li><a href="https://github.com/DimitriPapadopoulos"><code>@​DimitriPapadopoulos</code></a></li>
<li><a href="https://github.com/IDrokin117"><code>@​IDrokin117</code></a></li>
<li><a href="https://github.com/Luunynliny"><code>@​Luunynliny</code></a></li>
<li><a href="https://github.com/MichaReiser"><code>@​MichaReiser</code></a></li>
<li><a href="https://github.com/UnboundVariable"><code>@​UnboundVariable</code></a></li>
<li><a href="https://github.com/carljm"><code>@​carljm</code></a></li>
<li><a href="https://github.com/charliermarsh"><code>@​charliermarsh</code></a></li>
<li><a href="https://github.com/clockback"><code>@​clockback</code></a></li>
<li><a href="https://github.com/danparizher"><code>@​danparizher</code></a></li>
<li><a href="https://github.com/dcreager"><code>@​dcreager</code></a></li>
<li><a href="https://github.com/dhruvmanila"><code>@​dhruvmanila</code></a></li>
<li><a href="https://github.com/dylwil3"><code>@​dylwil3</code></a></li>
<li><a href="https://github.com/github-actions"><code>@​github-actions</code></a></li>
<li><a href="https://github.com/junhsonjb"><code>@​junhsonjb</code></a></li>
<li><a href="https://github.com/mtshiba"><code>@​mtshiba</code></a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/blob/main/CHANGELOG.md">ruff's changelog</a>.</em></p>
<blockquote>
<h2>0.12.7</h2>
<p>This is a follow-up release to 0.12.6. Because of an issue in the package metadata, 0.12.6 failed to publish fully to PyPI and has been yanked. Similarly, there is no GitHub release or Git tag for 0.12.6. The contents of the 0.12.7 release are identical to 0.12.6, except for the updated metadata.</p>
<h2>0.12.6</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>flake8-commas</code>] Add support for trailing comma checks in type parameter lists (<code>COM812</code>, <code>COM819</code>) (<a href="">#19390</a>)</li>
<li>[<code>pylint</code>] Implement auto-fix for <code>missing-maxsplit-arg</code> (<code>PLC0207</code>) (<a href="">#19387</a>)</li>
<li>[<code>ruff</code>] Offer fixes for <code>RUF039</code> in more cases (<a href="">#19065</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Support <code>.pyi</code> files in ruff analyze graph (<a href="">#19611</a>)</li>
<li>[<code>flake8-pyi</code>] Preserve inline comment in ellipsis removal (<code>PYI013</code>) (<a href="">#19399</a>)</li>
<li>[<code>perflint</code>] Ignore rule if target is <code>global</code> or <code>nonlocal</code> (<code>PERF401</code>) (<a href="">#19539</a>)</li>
<li>[<code>pyupgrade</code>] Fix <code>UP030</code> to avoid modifying double curly braces in format strings (<a href="">#19378</a>)</li>
<li>[<code>refurb</code>] Ignore decorated functions for <code>FURB118</code> (<a href="">#19339</a>)</li>
<li>[<code>refurb</code>] Mark <code>int</code> and <code>bool</code> cases for <code>Decimal.from_float</code> as safe fixes (<code>FURB164</code>) (<a href="">#19468</a>)</li>
<li>[<code>ruff</code>] Fix <code>RUF033</code> for named default expressions (<a href="">#19115</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>[<code>flake8-blind-except</code>] Change <code>BLE001</code> to permit <code>logging.critical(..., exc_info=True)</code> (<a href="">#19520</a>)</li>
</ul>
<h3>Performance</h3>
<ul>
<li>Add support for specifying minimum dots in detected string imports (<a href="">#19538</a>)</li>
</ul>
<h2>0.12.5</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>flake8-use-pathlib</code>] Add autofix for <code>PTH101</code>, <code>PTH104</code>, <code>PTH105</code>, <code>PTH121</code> (<a href="">#19404</a>)</li>
<li>[<code>ruff</code>] Support byte strings (<code>RUF055</code>) (<a href="">#18926</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Fix <code>unreachable</code> panic in parser (<a href="">#19183</a>)</li>
<li>[<code>flake8-pyi</code>] Skip fix if all <code>Union</code> members are <code>None</code> (<code>PYI016</code>) (<a href="">#19416</a>)</li>
<li>[<code>perflint</code>] Parenthesize generator expressions (<code>PERF401</code>) (<a href="">#19325</a>)</li>
<li>[<code>pylint</code>] Handle empty comments after line continuation (<code>PLR2044</code>) (<a href="">#19405</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>[<code>pep8-naming</code>] Fix <code>N802</code> false positives for <code>CGIHTTPRequestHandler</code> and <code>SimpleHTTPRequestHandler</code> (<a href="">#19432</a>)</li>
</ul>
<h2>0.12.4</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c5ac998</code></a> Bump 0.12.7 (<a href="">#19627</a>)</li>
<li><a href=""><code>04a8f64</code></a> Revert <code>license</code> and <code>license-files</code> changes in <code>pyproject.toml</code> (<a href="">#19624</a>)</li>
<li><a href=""><code>6e00adf</code></a> Bump 0.12.6 (<a href="">#19622</a>)</li>
<li><a href=""><code>864196b</code></a> Add <code>Checker::context</code> method, deduplicate Unicode checks (<a href="">#19609</a>)</li>
<li><a href=""><code>ae26fa0</code></a> [<code>flake8-pyi</code>] Preserve inline comment in ellipsis removal (<code>PYI013</code>) (<a href="">#19399</a>)</li>
<li><a href=""><code>88a6799</code></a> [ty] Add flow diagram for import resolution</li>
<li><a href=""><code>941be52</code></a> [ty] Add comments to some core resolver functions</li>
<li><a href=""><code>13624ce</code></a> [ty] Add missing ticks and use consistent quoting</li>
<li><a href=""><code>edb2f8e</code></a> [ty] Reflow some long lines</li>
<li><a href=""><code>5e6ad84</code></a> [ty] Unexport helper function</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/ruff/compare/0.12.1...0.12.7">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruff&package-manager=pip&previous-version=0.12.1&new-version=0.12.7)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad72b860cb91`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
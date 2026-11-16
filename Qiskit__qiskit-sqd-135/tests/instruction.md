# Issue

**Title:** Bump ruff from 0.8.4 to 0.9.4

## Description

Bumps [ruff](https://github.com/astral-sh/ruff) from 0.8.4 to 0.9.4.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/releases">ruff's releases</a>.</em></p>
<blockquote>
<h2>0.9.4</h2>
<h2>Release Notes</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Extend airflow context parameter check for <code>BaseOperator.execute</code> (<code>AIR302</code>) (<a href="">#15713</a>)</li>
<li>[<code>airflow</code>] Update <code>AIR302</code> to check for deprecated context keys (<a href="">#15144</a>)</li>
<li>[<code>flake8-bandit</code>] Permit suspicious imports within stub files (<code>S4</code>) (<a href="">#15822</a>)</li>
<li>[<code>pylint</code>] Do not trigger <code>PLR6201</code> on empty collections (<a href="">#15732</a>)</li>
<li>[<code>refurb</code>] Do not emit diagnostic when loop variables are used outside loop body (<code>FURB122</code>) (<a href="">#15757</a>)</li>
<li>[<code>ruff</code>] Add support for more <code>re</code> patterns (<code>RUF055</code>) (<a href="">#15764</a>)</li>
<li>[<code>ruff</code>] Check for shadowed <code>map</code> before suggesting fix (<code>RUF058</code>) (<a href="">#15790</a>)</li>
<li>[<code>ruff</code>] Do not emit diagnostic when all arguments to <code>zip()</code> are variadic (<code>RUF058</code>) (<a href="">#15744</a>)</li>
<li>[<code>ruff</code>] Parenthesize fix when argument spans multiple lines for <code>unnecessary-round</code> (<code>RUF057</code>) (<a href="">#15703</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>Preserve quote style in generated code (<a href="">#15726</a>, <a href="">#15778</a>, <a href="">#15794</a>)</li>
<li>[<code>flake8-bugbear</code>] Exempt <code>NewType</code> calls where the original type is immutable (<code>B008</code>) (<a href="">#15765</a>)</li>
<li>[<code>pylint</code>] Honor banned top-level imports by <code>TID253</code> in <code>PLC0415</code>. (<a href="">#15628</a>)</li>
<li>[<code>pyupgrade</code>] Ignore <code>is_typeddict</code> and <code>TypedDict</code> for <code>deprecated-import</code> (<code>UP035</code>) (<a href="">#15800</a>)</li>
</ul>
<h3>CLI</h3>
<ul>
<li>Fix formatter warning message for <code>flake8-quotes</code> option (<a href="">#15788</a>)</li>
<li>Implement tab autocomplete for <code>ruff config</code> (<a href="">#15603</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>flake8-comprehensions</code>] Do not emit <code>unnecessary-map</code> diagnostic when lambda has different arity (<code>C417</code>) (<a href="">#15802</a>)</li>
<li>[<code>flake8-comprehensions</code>] Parenthesize <code>sorted</code> when needed for <code>unnecessary-call-around-sorted</code> (<code>C413</code>) (<a href="">#15825</a>)</li>
<li>[<code>pyupgrade</code>] Handle end-of-line comments for <code>quoted-annotation</code> (<code>UP037</code>) (<a href="">#15824</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Add missing config docstrings (<a href="">#15803</a>)</li>
<li>Add references to <code>trio.run_process</code> and <code>anyio.run_process</code> (<a href="">#15761</a>)</li>
<li>Use <code>uv init --lib</code> in tutorial (<a href="">#15718</a>)</li>
</ul>
<h2>Contributors</h2>
<ul>
<li><a href="https://github.com/AlexWaygood"><code>@​AlexWaygood</code></a></li>
<li><a href="https://github.com/Garrett-R"><code>@​Garrett-R</code></a></li>
<li><a href="https://github.com/InSyncWithFoo"><code>@​InSyncWithFoo</code></a></li>
<li><a href="https://github.com/JelleZijlstra"><code>@​JelleZijlstra</code></a></li>
<li><a href="https://github.com/Lee-W"><code>@​Lee-W</code></a></li>
<li><a href="https://github.com/MichaReiser"><code>@​MichaReiser</code></a></li>
<li><a href="https://github.com/charliermarsh"><code>@​charliermarsh</code></a></li>
<li><a href="https://github.com/dcreager"><code>@​dcreager</code></a></li>
<li><a href="https://github.com/dhruvmanila"><code>@​dhruvmanila</code></a></li>
<li><a href="https://github.com/dylwil3"><code>@​dylwil3</code></a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/blob/main/CHANGELOG.md">ruff's changelog</a>.</em></p>
<blockquote>
<h2>0.9.4</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Extend airflow context parameter check for <code>BaseOperator.execute</code> (<code>AIR302</code>) (<a href="">#15713</a>)</li>
<li>[<code>airflow</code>] Update <code>AIR302</code> to check for deprecated context keys (<a href="">#15144</a>)</li>
<li>[<code>flake8-bandit</code>] Permit suspicious imports within stub files (<code>S4</code>) (<a href="">#15822</a>)</li>
<li>[<code>pylint</code>] Do not trigger <code>PLR6201</code> on empty collections (<a href="">#15732</a>)</li>
<li>[<code>refurb</code>] Do not emit diagnostic when loop variables are used outside loop body (<code>FURB122</code>) (<a href="">#15757</a>)</li>
<li>[<code>ruff</code>] Add support for more <code>re</code> patterns (<code>RUF055</code>) (<a href="">#15764</a>)</li>
<li>[<code>ruff</code>] Check for shadowed <code>map</code> before suggesting fix (<code>RUF058</code>) (<a href="">#15790</a>)</li>
<li>[<code>ruff</code>] Do not emit diagnostic when all arguments to <code>zip()</code> are variadic (<code>RUF058</code>) (<a href="">#15744</a>)</li>
<li>[<code>ruff</code>] Parenthesize fix when argument spans multiple lines for <code>unnecessary-round</code> (<code>RUF057</code>) (<a href="">#15703</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>Preserve quote style in generated code (<a href="">#15726</a>, <a href="">#15778</a>, <a href="">#15794</a>)</li>
<li>[<code>flake8-bugbear</code>] Exempt <code>NewType</code> calls where the original type is immutable (<code>B008</code>) (<a href="">#15765</a>)</li>
<li>[<code>pylint</code>] Honor banned top-level imports by <code>TID253</code> in <code>PLC0415</code>. (<a href="">#15628</a>)</li>
<li>[<code>pyupgrade</code>] Ignore <code>is_typeddict</code> and <code>TypedDict</code> for <code>deprecated-import</code> (<code>UP035</code>) (<a href="">#15800</a>)</li>
</ul>
<h3>CLI</h3>
<ul>
<li>Fix formatter warning message for <code>flake8-quotes</code> option (<a href="">#15788</a>)</li>
<li>Implement tab autocomplete for <code>ruff config</code> (<a href="">#15603</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>flake8-comprehensions</code>] Do not emit <code>unnecessary-map</code> diagnostic when lambda has different arity (<code>C417</code>) (<a href="">#15802</a>)</li>
<li>[<code>flake8-comprehensions</code>] Parenthesize <code>sorted</code> when needed for <code>unnecessary-call-around-sorted</code> (<code>C413</code>) (<a href="">#15825</a>)</li>
<li>[<code>pyupgrade</code>] Handle end-of-line comments for <code>quoted-annotation</code> (<code>UP037</code>) (<a href="">#15824</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Add missing config docstrings (<a href="">#15803</a>)</li>
<li>Add references to <code>trio.run_process</code> and <code>anyio.run_process</code> (<a href="">#15761</a>)</li>
<li>Use <code>uv init --lib</code> in tutorial (<a href="">#15718</a>)</li>
</ul>
<h2>0.9.3</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Argument <code>fail_stop</code> in DAG has been renamed as <code>fail_fast</code> (<code>AIR302</code>) (<a href="">#15633</a>)</li>
<li>[<code>airflow</code>] Extend <code>AIR303</code> with more symbols (<a href="">#15611</a>)</li>
<li>[<code>flake8-bandit</code>] Report all references to suspicious functions (<code>S3</code>) (<a href="">#15541</a>)</li>
<li>[<code>flake8-pytest-style</code>] Do not emit diagnostics for empty <code>for</code> loops (<code>PT012</code>, <code>PT031</code>) (<a href="">#15542</a>)</li>
<li>[<code>flake8-simplify</code>] Avoid double negations (<code>SIM103</code>) (<a href="">#15562</a>)</li>
<li>[<code>pyflakes</code>] Fix infinite loop with unused local import in <code>__init__.py</code> (<code>F401</code>) (<a href="">#15517</a>)</li>
<li>[<code>pylint</code>] Do not report methods with only one <code>EM101</code>-compatible <code>raise</code> (<code>PLR6301</code>) (<a href="">#15507</a>)</li>
<li>[<code>pylint</code>] Implement <code>redefined-slots-in-subclass</code> (<code>W0244</code>) (<a href="">#9640</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>854ab03</code></a> Bump version to 0.9.4 (<a href="">#15831</a>)</li>
<li><a href=""><code>b0b8b06</code></a> Remove semicolon after TypeScript interface definition (<a href="">#15827</a>)</li>
<li><a href=""><code>451f251</code></a> [red-knot] Clarify behavior when redeclaring base class attributes (<a href="">#15826</a>)</li>
<li><a href=""><code>13cf3e6</code></a> [<code>flake8-comprehensions</code>] Parenthesize <code>sorted</code> when needed for `unnecessary-...</li>
<li><a href=""><code>56f956a</code></a> [<code>pyupgrade</code>] Handle end-of-line comments for <code>quoted-annotation</code> (<code>UP037</code>) (...</li>
<li><a href=""><code>7a10a40</code></a> [<code>flake8-bandit</code>] Permit suspicious imports within stub files (<code>S4</code>) (<a href="">#15822</a>)</li>
<li><a href=""><code>3125332</code></a> [red-knot] Format mdtest snippets with the latest version of black (<a href="">#15819</a>)</li>
<li><a href=""><code>15d886a</code></a> [red-knot] Consider all definitions after terminal statements unreachable (<a href="">#1</a>...</li>
<li><a href=""><code>e1c9d10</code></a> [<code>flake8-comprehensions</code>] Do not emit <code>unnecessary-map</code> diagnostic when lambd...</li>
<li><a href=""><code>23c9884</code></a> Preserve quotes in generated f-strings (<a href="">#15794</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/ruff/compare/0.8.4...0.9.4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruff&package-manager=pip&previous-version=0.8.4&new-version=0.9.4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae91b99a7149`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
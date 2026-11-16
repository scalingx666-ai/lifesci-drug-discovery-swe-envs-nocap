# Issue

**Title:** Bump ruff from 0.11.2 to 0.11.8

## Description

Bumps [ruff](https://github.com/astral-sh/ruff) from 0.11.2 to 0.11.8.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/releases">ruff's releases</a>.</em></p>
<blockquote>
<h2>0.11.8</h2>
<h2>Release Notes</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Apply auto fixes to cases where the names have changed in Airflow 3 (<code>AIR302</code>, <code>AIR311</code>) (<a href="">#17553</a>, <a href="">#17570</a>, <a href="">#17571</a>)</li>
<li>[<code>airflow</code>] Extend <code>AIR301</code> rule (<a href="">#17598</a>)</li>
<li>[<code>airflow</code>] Update existing <code>AIR302</code> rules with better suggestions (<a href="">#17542</a>)</li>
<li>[<code>refurb</code>] Mark fix as safe for <code>readlines-in-for</code> (<code>FURB129</code>) (<a href="">#17644</a>)</li>
<li>[syntax-errors] <code>nonlocal</code> declaration at module level (<a href="">#17559</a>)</li>
<li>[syntax-errors] Detect single starred expression assignment <code>x = *y</code> (<a href="">#17624</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>flake8-pyi</code>] Ensure <code>Literal[None,] | Literal[None,]</code> is not autofixed to <code>None | None</code> (<code>PYI061</code>) (<a href="">#17659</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Avoid suggesting <code>Path.iterdir()</code> for <code>os.listdir</code> with file descriptor (<code>PTH208</code>) (<a href="">#17715</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Fix <code>PTH104</code> false positive when <code>rename</code> is passed a file descriptor (<a href="">#17712</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Fix <code>PTH116</code> false positive when <code>stat</code> is passed a file descriptor (<a href="">#17709</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Fix <code>PTH123</code> false positive when <code>open</code> is passed a file descriptor from a function call (<a href="">#17705</a>)</li>
<li>[<code>pycodestyle</code>] Fix duplicated diagnostic in <code>E712</code> (<a href="">#17651</a>)</li>
<li>[<code>pylint</code>] Detect <code>global</code> declarations in module scope (<code>PLE0118</code>) (<a href="">#17411</a>)</li>
<li>[syntax-errors] Make <code>async-comprehension-in-sync-comprehension</code> more specific (<a href="">#17460</a>)</li>
</ul>
<h3>Configuration</h3>
<ul>
<li>Add option to disable <code>typing_extensions</code> imports (<a href="">#17611</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix example syntax for the <code>lint.pydocstyle.ignore-var-parameters</code> option (<a href="">#17740</a>)</li>
<li>Add fix safety sections (<code>ASYNC116</code>, <code>FLY002</code>, <code>D200</code>, <code>RUF005</code>, <code>RUF017</code>, <code>RUF027</code>, <code>RUF028</code>, <code>RUF057</code>) (<a href="">#17497</a>, <a href="">#17496</a>, <a href="">#17502</a>, <a href="">#17484</a>, <a href="">#17480</a>, <a href="">#17485</a>, <a href="">#17722</a>, <a href="">#17483</a>)</li>
</ul>
<h3>Other changes</h3>
<ul>
<li>Add Python 3.14 to configuration options (<a href="">#17647</a>)</li>
<li>Make syntax error for unparenthesized except tuples version specific to before 3.14 (<a href="">#17660</a>)</li>
</ul>
<h2>Contributors</h2>
<ul>
<li><a href="https://github.com/AlexWaygood"><code>@​AlexWaygood</code></a></li>
<li><a href="https://github.com/BurntSushi"><code>@​BurntSushi</code></a></li>
<li><a href="https://github.com/Jie211"><code>@​Jie211</code></a></li>
<li><a href="https://github.com/Kalmaegi"><code>@​Kalmaegi</code></a></li>
<li><a href="https://github.com/LaBatata101"><code>@​LaBatata101</code></a></li>
<li><a href="https://github.com/Lee-W"><code>@​Lee-W</code></a></li>
<li><a href="https://github.com/MichaReiser"><code>@​MichaReiser</code></a></li>
<li><a href="https://github.com/VascoSch92"><code>@​VascoSch92</code></a></li>
<li><a href="https://github.com/abhijeetbodas2001"><code>@​abhijeetbodas2001</code></a></li>
<li><a href="https://github.com/brendancooley"><code>@​brendancooley</code></a></li>
<li><a href="https://github.com/carljm"><code>@​carljm</code></a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/blob/main/CHANGELOG.md">ruff's changelog</a>.</em></p>
<blockquote>
<h2>0.11.8</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Apply auto fixes to cases where the names have changed in Airflow 3 (<code>AIR302</code>, <code>AIR311</code>) (<a href="">#17553</a>, <a href="">#17570</a>, <a href="">#17571</a>)</li>
<li>[<code>airflow</code>] Extend <code>AIR301</code> rule (<a href="">#17598</a>)</li>
<li>[<code>airflow</code>] Update existing <code>AIR302</code> rules with better suggestions (<a href="">#17542</a>)</li>
<li>[<code>refurb</code>] Mark fix as safe for <code>readlines-in-for</code> (<code>FURB129</code>) (<a href="">#17644</a>)</li>
<li>[syntax-errors] <code>nonlocal</code> declaration at module level (<a href="">#17559</a>)</li>
<li>[syntax-errors] Detect single starred expression assignment <code>x = *y</code> (<a href="">#17624</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>flake8-pyi</code>] Ensure <code>Literal[None,] | Literal[None,]</code> is not autofixed to <code>None | None</code> (<code>PYI061</code>) (<a href="">#17659</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Avoid suggesting <code>Path.iterdir()</code> for <code>os.listdir</code> with file descriptor (<code>PTH208</code>) (<a href="">#17715</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Fix <code>PTH104</code> false positive when <code>rename</code> is passed a file descriptor (<a href="">#17712</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Fix <code>PTH116</code> false positive when <code>stat</code> is passed a file descriptor (<a href="">#17709</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Fix <code>PTH123</code> false positive when <code>open</code> is passed a file descriptor from a function call (<a href="">#17705</a>)</li>
<li>[<code>pycodestyle</code>] Fix duplicated diagnostic in <code>E712</code> (<a href="">#17651</a>)</li>
<li>[<code>pylint</code>] Detect <code>global</code> declarations in module scope (<code>PLE0118</code>) (<a href="">#17411</a>)</li>
<li>[syntax-errors] Make <code>async-comprehension-in-sync-comprehension</code> more specific (<a href="">#17460</a>)</li>
</ul>
<h3>Configuration</h3>
<ul>
<li>Add option to disable <code>typing_extensions</code> imports (<a href="">#17611</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix example syntax for the <code>lint.pydocstyle.ignore-var-parameters</code> option (<a href="">#17740</a>)</li>
<li>Add fix safety sections (<code>ASYNC116</code>, <code>FLY002</code>, <code>D200</code>, <code>RUF005</code>, <code>RUF017</code>, <code>RUF027</code>, <code>RUF028</code>, <code>RUF057</code>) (<a href="">#17497</a>, <a href="">#17496</a>, <a href="">#17502</a>, <a href="">#17484</a>, <a href="">#17480</a>, <a href="">#17485</a>, <a href="">#17722</a>, <a href="">#17483</a>)</li>
</ul>
<h3>Other changes</h3>
<ul>
<li>Add Python 3.14 to configuration options (<a href="">#17647</a>)</li>
<li>Make syntax error for unparenthesized except tuples version specific to before 3.14 (<a href="">#17660</a>)</li>
</ul>
<h2>0.11.7</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Apply auto fixes to cases where the names have changed in Airflow 3 (<code>AIR301</code>) (<a href="">#17355</a>)</li>
<li>[<code>perflint</code>] Implement fix for <code>manual-dict-comprehension</code> (<code>PERF403</code>) (<a href="">#16719</a>)</li>
<li>[syntax-errors] Make duplicate parameter names a semantic error (<a href="">#17131</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>airflow</code>] Fix typos in provider package names (<code>AIR302</code>, <code>AIR312</code>) (<a href="">#17574</a>)</li>
<li>[<code>flake8-type-checking</code>] Visit keyword arguments in checks involving <code>typing.cast</code>/<code>typing.NewType</code> arguments (<a href="">#17538</a>)</li>
<li>[<code>pyupgrade</code>] Preserve parenthesis when fixing native literals containing newlines (<code>UP018</code>) (<a href="">#17220</a>)</li>
<li>[<code>refurb</code>] Mark the <code>FURB161</code> fix unsafe except for integers and booleans (<a href="">#17240</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>75effb8</code></a> Bump 0.11.8 (<a href="">#17766</a>)</li>
<li><a href=""><code>3353d07</code></a> [<code>flake8-use-pathlib</code>] Fix <code>PTH104</code>false positive when <code>rename</code> is passed a f...</li>
<li><a href=""><code>41f3f21</code></a> Improve messages outputted by py-fuzzer (<a href="">#17764</a>)</li>
<li><a href=""><code>76ec64d</code></a> [<code>red-knot</code>] Allow subclasses of Any to be assignable to Callable types (<a href="">#17717</a>)</li>
<li><a href=""><code>b7e69ec</code></a> [red-knot] Increase durability of read-only <code>File</code> fields (<a href="">#17757</a>)</li>
<li><a href=""><code>9c57862</code></a> [red-knot] Cache source type during semanic index building (<a href="">#17756</a>)</li>
<li><a href=""><code>67ef370</code></a> [<code>flake8-use-pathlib</code>] Fix <code>PTH116</code> false positive when <code>stat</code> is passed a fi...</li>
<li><a href=""><code>e17e1e8</code></a> Sync vendored typeshed stubs (<a href="">#17753</a>)</li>
<li><a href=""><code>03d8679</code></a> [red-knot] Preliminary <code>NamedTuple</code> support (<a href="">#17738</a>)</li>
<li><a href=""><code>d33a503</code></a> [red-knot] Add tests for classes that have incompatible <code>__new__</code> and `__init...</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/ruff/compare/0.11.2...0.11.8">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruff&package-manager=pip&previous-version=0.11.2&new-version=0.11.8)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7bd72dafa958`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
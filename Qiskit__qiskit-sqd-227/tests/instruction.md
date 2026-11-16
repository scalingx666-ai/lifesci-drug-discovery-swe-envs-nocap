# Issue

**Title:** Bump ruff from 0.11.12 to 0.12.1

## Description

Bumps [ruff](https://github.com/astral-sh/ruff) from 0.11.12 to 0.12.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/releases">ruff's releases</a>.</em></p>
<blockquote>
<h2>0.12.1</h2>
<h2>Release Notes</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>flake8-errmsg</code>] Extend <code>EM101</code> to support byte strings (<a href="">#18867</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Add autofix for <code>PTH202</code> (<a href="">#18763</a>)</li>
<li>[<code>pygrep-hooks</code>] Add <code>AsyncMock</code> methods to <code>invalid-mock-access</code> (<code>PGH005</code>) (<a href="">#18547</a>)</li>
<li>[<code>pylint</code>] Ignore <code>__init__.py</code> files in (<code>PLC0414</code>) (<a href="">#18400</a>)</li>
<li>[<code>ruff</code>] Trigger <code>RUF037</code> for empty string and byte strings (<a href="">#18862</a>)</li>
<li>[formatter] Fix missing blank lines before decorated classes in <code>.pyi</code> files (<a href="">#18888</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Avoid generating diagnostics with per-file ignores (<a href="">#18801</a>)</li>
<li>Handle parenthesized arguments in <code>remove_argument</code> (<a href="">#18805</a>)</li>
<li>[<code>flake8-logging</code>] Avoid false positive for <code>exc_info=True</code> outside <code>logger.exception</code> (<code>LOG014</code>) (<a href="">#18737</a>)</li>
<li>[<code>flake8-pytest-style</code>] Enforce <code>pytest</code> import for decorators (<a href="">#18779</a>)</li>
<li>[<code>flake8-pytest-style</code>] Mark autofix for <code>PT001</code> and <code>PT023</code> as unsafe if there's comments in the decorator (<a href="">#18792</a>)</li>
<li>[<code>flake8-pytest-style</code>] <code>PT001</code>/<code>PT023</code> fix makes syntax error on parenthesized decorator (<a href="">#18782</a>)</li>
<li>[<code>flake8-raise</code>] Make fix unsafe if it deletes comments (<code>RSE102</code>) (<a href="">#18788</a>)</li>
<li>[<code>flake8-simplify</code>] Fix <code>SIM911</code> autofix creating a syntax error (<a href="">#18793</a>)</li>
<li>[<code>flake8-simplify</code>] Fix false negatives for shadowed bindings (<code>SIM910</code>, <code>SIM911</code>) (<a href="">#18794</a>)</li>
<li>[<code>flake8-simplify</code>] Preserve original behavior for <code>except ()</code> and bare <code>except</code> (<code>SIM105</code>) (<a href="">#18213</a>)</li>
<li>[<code>flake8-pyi</code>] Fix <code>PYI041</code>'s fix causing <code>TypeError</code> with <code>None | None | ...</code> (<a href="">#18637</a>)</li>
<li>[<code>perflint</code>] Fix <code>PERF101</code> autofix creating a syntax error and mark autofix as unsafe if there are comments in the <code>list</code> call expr (<a href="">#18803</a>)</li>
<li>[<code>perflint</code>] Fix false negative in <code>PERF401</code> (<a href="">#18866</a>)</li>
<li>[<code>pylint</code>] Avoid flattening nested <code>min</code>/<code>max</code> when outer call has single argument (<code>PLW3301</code>) (<a href="">#16885</a>)</li>
<li>[<code>pylint</code>] Fix <code>PLC2801</code> autofix creating a syntax error (<a href="">#18857</a>)</li>
<li>[<code>pylint</code>] Mark <code>PLE0241</code> autofix as unsafe if there's comments in the base classes (<a href="">#18832</a>)</li>
<li>[<code>pylint</code>] Suppress <code>PLE2510</code>/<code>PLE2512</code>/<code>PLE2513</code>/<code>PLE2514</code>/<code>PLE2515</code> autofix if the text contains an odd number of backslashes (<a href="">#18856</a>)</li>
<li>[<code>refurb</code>] Detect more exotic float literals in <code>FURB164</code> (<a href="">#18925</a>)</li>
<li>[<code>refurb</code>] Fix <code>FURB163</code> autofix creating a syntax error for <code>yield</code> expressions (<a href="">#18756</a>)</li>
<li>[<code>refurb</code>] Mark <code>FURB129</code> autofix as unsafe if there's comments in the <code>readlines</code> call (<a href="">#18858</a>)</li>
<li>[<code>ruff</code>] Fix false positives and negatives in <code>RUF010</code> (<a href="">#18690</a>)</li>
<li>Fix casing of <code>analyze.direction</code> variant names (<a href="">#18892</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>Fix f-string interpolation escaping in generated fixes (<a href="">#18882</a>)</li>
<li>[<code>flake8-return</code>] Mark <code>RET501</code> fix unsafe if comments are inside (<a href="">#18780</a>)</li>
<li>[<code>flake8-async</code>] Fix detection for large integer sleep durations in <code>ASYNC116</code> rule (<a href="">#18767</a>)</li>
<li>[<code>flake8-async</code>] Mark autofix for <code>ASYNC115</code> as unsafe if the call expression contains comments (<a href="">#18753</a>)</li>
<li>[<code>flake8-bugbear</code>] Mark autofix for <code>B004</code> as unsafe if the <code>hasattr</code> call expr contains comments (<a href="">#18755</a>)</li>
<li>[<code>flake8-comprehension</code>] Mark autofix for <code>C420</code> as unsafe if there's comments inside the dict comprehension (<a href="">#18768</a>)</li>
<li>[<code>flake8-comprehensions</code>] Handle template strings for comprehension fixes (<a href="">#18710</a>)</li>
<li>[<code>flake8-future-annotations</code>] Add autofix (<code>FA100</code>) (<a href="">#18903</a>)</li>
<li>[<code>pyflakes</code>] Mark <code>F504</code>/<code>F522</code>/<code>F523</code> autofix as unsafe if there's a call with side effect (<a href="">#18839</a>)</li>
<li>[<code>pylint</code>] Allow fix with comments and document performance implications (<code>PLW3301</code>) (<a href="">#18936</a>)</li>
<li>[<code>pylint</code>] Detect more exotic <code>NaN</code> literals in <code>PLW0177</code> (<a href="">#18630</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/blob/main/CHANGELOG.md">ruff's changelog</a>.</em></p>
<blockquote>
<h2>0.12.1</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>flake8-errmsg</code>] Extend <code>EM101</code> to support byte strings (<a href="">#18867</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Add autofix for <code>PTH202</code> (<a href="">#18763</a>)</li>
<li>[<code>pygrep-hooks</code>] Add <code>AsyncMock</code> methods to <code>invalid-mock-access</code> (<code>PGH005</code>) (<a href="">#18547</a>)</li>
<li>[<code>pylint</code>] Ignore <code>__init__.py</code> files in (<code>PLC0414</code>) (<a href="">#18400</a>)</li>
<li>[<code>ruff</code>] Trigger <code>RUF037</code> for empty string and byte strings (<a href="">#18862</a>)</li>
<li>[formatter] Fix missing blank lines before decorated classes in <code>.pyi</code> files (<a href="">#18888</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Avoid generating diagnostics with per-file ignores (<a href="">#18801</a>)</li>
<li>Handle parenthesized arguments in <code>remove_argument</code> (<a href="">#18805</a>)</li>
<li>[<code>flake8-logging</code>] Avoid false positive for <code>exc_info=True</code> outside <code>logger.exception</code> (<code>LOG014</code>) (<a href="">#18737</a>)</li>
<li>[<code>flake8-pytest-style</code>] Enforce <code>pytest</code> import for decorators (<a href="">#18779</a>)</li>
<li>[<code>flake8-pytest-style</code>] Mark autofix for <code>PT001</code> and <code>PT023</code> as unsafe if there's comments in the decorator (<a href="">#18792</a>)</li>
<li>[<code>flake8-pytest-style</code>] <code>PT001</code>/<code>PT023</code> fix makes syntax error on parenthesized decorator (<a href="">#18782</a>)</li>
<li>[<code>flake8-raise</code>] Make fix unsafe if it deletes comments (<code>RSE102</code>) (<a href="">#18788</a>)</li>
<li>[<code>flake8-simplify</code>] Fix <code>SIM911</code> autofix creating a syntax error (<a href="">#18793</a>)</li>
<li>[<code>flake8-simplify</code>] Fix false negatives for shadowed bindings (<code>SIM910</code>, <code>SIM911</code>) (<a href="">#18794</a>)</li>
<li>[<code>flake8-simplify</code>] Preserve original behavior for <code>except ()</code> and bare <code>except</code> (<code>SIM105</code>) (<a href="">#18213</a>)</li>
<li>[<code>flake8-pyi</code>] Fix <code>PYI041</code>'s fix causing <code>TypeError</code> with <code>None | None | ...</code> (<a href="">#18637</a>)</li>
<li>[<code>perflint</code>] Fix <code>PERF101</code> autofix creating a syntax error and mark autofix as unsafe if there are comments in the <code>list</code> call expr (<a href="">#18803</a>)</li>
<li>[<code>perflint</code>] Fix false negative in <code>PERF401</code> (<a href="">#18866</a>)</li>
<li>[<code>pylint</code>] Avoid flattening nested <code>min</code>/<code>max</code> when outer call has single argument (<code>PLW3301</code>) (<a href="">#16885</a>)</li>
<li>[<code>pylint</code>] Fix <code>PLC2801</code> autofix creating a syntax error (<a href="">#18857</a>)</li>
<li>[<code>pylint</code>] Mark <code>PLE0241</code> autofix as unsafe if there's comments in the base classes (<a href="">#18832</a>)</li>
<li>[<code>pylint</code>] Suppress <code>PLE2510</code>/<code>PLE2512</code>/<code>PLE2513</code>/<code>PLE2514</code>/<code>PLE2515</code> autofix if the text contains an odd number of backslashes (<a href="">#18856</a>)</li>
<li>[<code>refurb</code>] Detect more exotic float literals in <code>FURB164</code> (<a href="">#18925</a>)</li>
<li>[<code>refurb</code>] Fix <code>FURB163</code> autofix creating a syntax error for <code>yield</code> expressions (<a href="">#18756</a>)</li>
<li>[<code>refurb</code>] Mark <code>FURB129</code> autofix as unsafe if there's comments in the <code>readlines</code> call (<a href="">#18858</a>)</li>
<li>[<code>ruff</code>] Fix false positives and negatives in <code>RUF010</code> (<a href="">#18690</a>)</li>
<li>Fix casing of <code>analyze.direction</code> variant names (<a href="">#18892</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>Fix f-string interpolation escaping in generated fixes (<a href="">#18882</a>)</li>
<li>[<code>flake8-return</code>] Mark <code>RET501</code> fix unsafe if comments are inside (<a href="">#18780</a>)</li>
<li>[<code>flake8-async</code>] Fix detection for large integer sleep durations in <code>ASYNC116</code> rule (<a href="">#18767</a>)</li>
<li>[<code>flake8-async</code>] Mark autofix for <code>ASYNC115</code> as unsafe if the call expression contains comments (<a href="">#18753</a>)</li>
<li>[<code>flake8-bugbear</code>] Mark autofix for <code>B004</code> as unsafe if the <code>hasattr</code> call expr contains comments (<a href="">#18755</a>)</li>
<li>[<code>flake8-comprehension</code>] Mark autofix for <code>C420</code> as unsafe if there's comments inside the dict comprehension (<a href="">#18768</a>)</li>
<li>[<code>flake8-comprehensions</code>] Handle template strings for comprehension fixes (<a href="">#18710</a>)</li>
<li>[<code>flake8-future-annotations</code>] Add autofix (<code>FA100</code>) (<a href="">#18903</a>)</li>
<li>[<code>pyflakes</code>] Mark <code>F504</code>/<code>F522</code>/<code>F523</code> autofix as unsafe if there's a call with side effect (<a href="">#18839</a>)</li>
<li>[<code>pylint</code>] Allow fix with comments and document performance implications (<code>PLW3301</code>) (<a href="">#18936</a>)</li>
<li>[<code>pylint</code>] Detect more exotic <code>NaN</code> literals in <code>PLW0177</code> (<a href="">#18630</a>)</li>
<li>[<code>pylint</code>] Fix <code>PLC1802</code> autofix creating a syntax error and mark autofix as unsafe if there's comments in the <code>len</code> call (<a href="">#18836</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>32c5418</code></a> Bump 0.12.1 (<a href="">#18969</a>)</li>
<li><a href=""><code>b85c219</code></a> [<code>FastAPI</code>] Add fix safety section to <code>FAST002</code> (<a href="">#18940</a>)</li>
<li><a href=""><code>b1d1cf1</code></a> [ty] Add regression test for leading tab mis-alignment in diagnostic renderin...</li>
<li><a href=""><code>1dcdf7f</code></a> [ty] Resolve python environment in <code>Options::to_program_settings</code> (<a href="">#18960</a>)</li>
<li><a href=""><code>d006976</code></a> [<code>ruff</code>] Fix false positives and negatives in <code>RUF010</code> (<a href="">#18690</a>)</li>
<li><a href=""><code>76619b9</code></a> [ty] Fix rendering of long lines that are indented with tabs</li>
<li><a href=""><code>6e25cfb</code></a> [ty] Add regression test for diagnostic rendering panic</li>
<li><a href=""><code>7638729</code></a> [ty] Move venv and conda env discovery to <code>SearchPath::from_settings</code> (<a href="">#18938</a>)</li>
<li><a href=""><code>d04e63a</code></a> [ty] Add regression-benchmark for attribute-assignment hang (<a href="">#18957</a>)</li>
<li><a href=""><code>86fd9b6</code></a> [ty] Format conflicting types as an enumeration (<a href="">#18956</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/ruff/compare/0.11.12...0.12.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruff&package-manager=pip&previous-version=0.11.12&new-version=0.12.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bca9a8021bd9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
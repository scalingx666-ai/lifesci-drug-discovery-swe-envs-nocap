# Issue

**Title:** Bump ruff from 0.11.8 to 0.11.12

## Description

Bumps [ruff](https://github.com/astral-sh/ruff) from 0.11.8 to 0.11.12.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/releases">ruff's releases</a>.</em></p>
<blockquote>
<h2>0.11.12</h2>
<h2>Release Notes</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Revise fix titles (<code>AIR3</code>) (<a href="">#18215</a>)</li>
<li>[<code>pylint</code>] Implement <code>missing-maxsplit-arg</code> (<code>PLC0207</code>) (<a href="">#17454</a>)</li>
<li>[<code>pyupgrade</code>] New rule <code>UP050</code> (<code>useless-class-metaclass-type</code>) (<a href="">#18334</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Replace <code>os.symlink</code> with <code>Path.symlink_to</code> (<code>PTH211</code>) (<a href="">#18337</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>flake8-bugbear</code>] Ignore <code>__debug__</code> attribute in <code>B010</code> (<a href="">#18357</a>)</li>
<li>[<code>flake8-async</code>] Fix <code>anyio.sleep</code> argument name (<code>ASYNC115</code>, <code>ASYNC116</code>) (<a href="">#18262</a>)</li>
<li>[<code>refurb</code>] Fix <code>FURB129</code> autofix generating invalid syntax (<a href="">#18235</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>[<code>flake8-implicit-str-concat</code>] Add autofix for <code>ISC003</code> (<a href="">#18256</a>)</li>
<li>[<code>pycodestyle</code>] Improve the diagnostic message for <code>E712</code> (<a href="">#18328</a>)</li>
<li>[<code>flake8-2020</code>] Fix diagnostic message for <code>!=</code> comparisons (<code>YTT201</code>) (<a href="">#18293</a>)</li>
<li>[<code>pyupgrade</code>] Make fix unsafe if it deletes comments (<code>UP010</code>) (<a href="">#18291</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Simplify rules table to improve readability (<a href="">#18297</a>)</li>
<li>Update editor integrations link in README (<a href="">#17977</a>)</li>
<li>[<code>flake8-bugbear</code>] Add fix safety section (<code>B006</code>) (<a href="">#17652</a>)</li>
</ul>
<h2>Contributors</h2>
<ul>
<li><a href="https://github.com/AlexWaygood"><code>@​AlexWaygood</code></a></li>
<li><a href="https://github.com/CodeMan62"><code>@​CodeMan62</code></a></li>
<li><a href="https://github.com/InSyncWithFoo"><code>@​InSyncWithFoo</code></a></li>
<li><a href="https://github.com/Kalmaegi"><code>@​Kalmaegi</code></a></li>
<li><a href="https://github.com/LaBatata101"><code>@​LaBatata101</code></a></li>
<li><a href="https://github.com/Lee-W"><code>@​Lee-W</code></a></li>
<li><a href="https://github.com/MaddyGuthridge"><code>@​MaddyGuthridge</code></a></li>
<li><a href="https://github.com/MatthewMckee4"><code>@​MatthewMckee4</code></a></li>
<li><a href="https://github.com/MichaReiser"><code>@​MichaReiser</code></a></li>
<li><a href="https://github.com/Vasanth-96"><code>@​Vasanth-96</code></a></li>
<li><a href="https://github.com/carljm"><code>@​carljm</code></a></li>
<li><a href="https://github.com/charliermarsh"><code>@​charliermarsh</code></a></li>
<li><a href="https://github.com/chirizxc"><code>@​chirizxc</code></a></li>
<li><a href="https://github.com/dcreager"><code>@​dcreager</code></a></li>
<li><a href="https://github.com/dhruvmanila"><code>@​dhruvmanila</code></a></li>
<li><a href="https://github.com/dsherret"><code>@​dsherret</code></a></li>
<li><a href="https://github.com/dylwil3"><code>@​dylwil3</code></a></li>
<li><a href="https://github.com/felixscherz"><code>@​felixscherz</code></a></li>
<li><a href="https://github.com/fennr"><code>@​fennr</code></a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff/blob/main/CHANGELOG.md">ruff's changelog</a>.</em></p>
<blockquote>
<h2>0.11.12</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Revise fix titles (<code>AIR3</code>) (<a href="">#18215</a>)</li>
<li>[<code>pylint</code>] Implement <code>missing-maxsplit-arg</code> (<code>PLC0207</code>) (<a href="">#17454</a>)</li>
<li>[<code>pyupgrade</code>] New rule <code>UP050</code> (<code>useless-class-metaclass-type</code>) (<a href="">#18334</a>)</li>
<li>[<code>flake8-use-pathlib</code>] Replace <code>os.symlink</code> with <code>Path.symlink_to</code> (<code>PTH211</code>) (<a href="">#18337</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>[<code>flake8-bugbear</code>] Ignore <code>__debug__</code> attribute in <code>B010</code> (<a href="">#18357</a>)</li>
<li>[<code>flake8-async</code>] Fix <code>anyio.sleep</code> argument name (<code>ASYNC115</code>, <code>ASYNC116</code>) (<a href="">#18262</a>)</li>
<li>[<code>refurb</code>] Fix <code>FURB129</code> autofix generating invalid syntax (<a href="">#18235</a>)</li>
</ul>
<h3>Rule changes</h3>
<ul>
<li>[<code>flake8-implicit-str-concat</code>] Add autofix for <code>ISC003</code> (<a href="">#18256</a>)</li>
<li>[<code>pycodestyle</code>] Improve the diagnostic message for <code>E712</code> (<a href="">#18328</a>)</li>
<li>[<code>flake8-2020</code>] Fix diagnostic message for <code>!=</code> comparisons (<code>YTT201</code>) (<a href="">#18293</a>)</li>
<li>[<code>pyupgrade</code>] Make fix unsafe if it deletes comments (<code>UP010</code>) (<a href="">#18291</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Simplify rules table to improve readability (<a href="">#18297</a>)</li>
<li>Update editor integrations link in README (<a href="">#17977</a>)</li>
<li>[<code>flake8-bugbear</code>] Add fix safety section (<code>B006</code>) (<a href="">#17652</a>)</li>
</ul>
<h2>0.11.11</h2>
<h3>Preview features</h3>
<ul>
<li>[<code>airflow</code>] Add autofixes for <code>AIR302</code> and <code>AIR312</code> (<a href="">#17942</a>)</li>
<li>[<code>airflow</code>] Move rules from <code>AIR312</code> to <code>AIR302</code> (<a href="">#17940</a>)</li>
<li>[<code>airflow</code>] Update <code>AIR301</code> and <code>AIR311</code> with the latest Airflow implementations (<a href="">#17985</a>)</li>
<li>[<code>flake8-simplify</code>] Enable fix in preview mode (<code>SIM117</code>) (<a href="">#18208</a>)</li>
</ul>
<h3>Bug fixes</h3>
<ul>
<li>Fix inconsistent formatting of match-case on <code>[]</code> and <code>_</code> (<a href="">#18147</a>)</li>
<li>[<code>pylint</code>] Fix <code>PLW1514</code> not recognizing the <code>encoding</code> positional argument of <code>codecs.open</code> (<a href="">#18109</a>)</li>
</ul>
<h3>CLI</h3>
<ul>
<li>Add full option name in formatter warning (<a href="">#18217</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix rendering of admonition in docs (<a href="">#18163</a>)</li>
<li>[<code>flake8-print</code>] Improve print/pprint docs for <code>T201</code> and <code>T203</code> (<a href="">#18130</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>aee3af0</code></a> Bump 0.11.12 (<a href="">#18369</a>)</li>
<li><a href=""><code>04dc48e</code></a> [<code>refurb</code>] Fix <code>FURB129</code> autofix generating invalid syntax (<a href="">#18235</a>)</li>
<li><a href=""><code>27743ef</code></a> [<code>pylint</code>] Implement <code>missing-maxsplit-arg</code> (<code>PLC0207</code>) (<a href="">#17454</a>)</li>
<li><a href=""><code>c60b4d7</code></a> [ty] Add subtyping between Callable types and class literals with <code>__init__</code> ...</li>
<li><a href=""><code>16621fa</code></a> [<code>flake8-bugbear </code>] Add fix safety section (<code>B006</code>)  (<a href="">#17652</a>)</li>
<li><a href=""><code>e23d4ea</code></a> [<code>flake8-bugbear</code>] Ignore <code>__debug__</code> attribute in <code>B010</code> (<a href="">#18357</a>)</li>
<li><a href=""><code>452f992</code></a> [ty] Simplify signature types, use them in <code>CallableType</code> (<a href="">#18344</a>)</li>
<li><a href=""><code>a5ebb3f</code></a> [ty] Support ephemeral uv virtual environments (<a href="">#18335</a>)</li>
<li><a href=""><code>9925910</code></a> Add a <code>ViolationMetadata::rule</code> method (<a href="">#18234</a>)</li>
<li><a href=""><code>a3ee6bb</code></a> Return <code>DiagnosticGuard</code> from <code>Checker::report_diagnostic</code> (<a href="">#18232</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/ruff/compare/0.11.8...0.11.12">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ruff&package-manager=pip&previous-version=0.11.8&new-version=0.11.12)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad90961b5b49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
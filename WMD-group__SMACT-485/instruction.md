# Issue

**Title:** Bump dash from 3.0.2 to 3.3.0

## Description

Bumps [dash](https://github.com/plotly/dash) from 3.0.2 to 3.3.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/plotly/dash/releases">dash's releases</a>.</em></p>
<blockquote>
<h2>Dash Version 3.3.0</h2>
<h2>Added</h2>
<ul>
<li><a href="">#3395</a> Add position argument to hooks.devtool</li>
<li><a href="">#3403</a> Add app_context to get_app, allowing to get the current app in routes.</li>
<li><a href="">#3407</a> Add <code>hidden</code> to callback arguments, hiding the callback from appearing in the devtool callback graph.</li>
<li><a href="">#3397</a> Add optional callbacks, suppressing callback warning for missing component ids for a single callback.</li>
<li><a href="">#3424</a> Adds support for <code>Patch</code> on clientside callbacks class <code>dash_clientside.Patch</code>, as well as supporting side updates, eg: (Running, SetProps).</li>
<li><a href="">#3347</a> Added 'api_endpoint' to <code>callback</code> to expose api endpoints at the provided path for use to be executed directly without dash.</li>
<li><a href="">#3445</a> Added API to reverse direction of slider component.</li>
<li><a href="">#3460</a> Add <code>/health</code> endpoint for server monitoring and health checks.</li>
<li><a href="">#3465</a> Plotly cloud integrations, add devtool API, placeholder plotly cloud CLI &amp; publish button, <code>dash[cloud]</code> extra dependencies.</li>
</ul>
<h2>Fixed</h2>
<ul>
<li><a href="">#3490</a> Fix stack overflow when circular callbacks are displayed on the devtool callback</li>
<li><a href="">#3395</a> Fix Components added through set_props() cannot trigger related callback functions. Fix <a href="">#3316</a></li>
<li><a href="">#3415</a> Fix the error triggered when only a single no_update is returned for client-side callback functions with multiple Outputs. Fix <a href="">#3366</a></li>
<li><a href="">#3416</a> Fix DeprecationWarning in dash/_jupyter.py by migrating from deprecated ipykernel.comm.Comm to comm module</li>
<li><a href="">#3488</a> Fix pkgutil.find_loader removal in Python 3.14</li>
</ul>
<h2>Deprecated</h2>
<ul>
<li><a href="">#3482</a> Deprecate dash_table.DataTable with replacement from <code>dash[ag-grid]</code> extra requirement.</li>
</ul>
<h2>Dash Version 3.3.0rc2</h2>
<ul>
<li>Remove placeholde publish button when on workspace</li>
</ul>
<h2>Dash Version 3.3.0rc1</h2>
<ul>
<li>Add placeholder plotly CLI</li>
<li>Add dash[cloud] optional dependency.</li>
<li>Add placeholder plotly cloud publish button in the devtools.</li>
</ul>
<h2>Dash Version 3.3.0rc0</h2>
<h2>Added</h2>
<ul>
<li><a href="">#3395</a> Add position argument to hooks.devtool</li>
<li><a href="">#3403</a> Add app_context to get_app, allowing to get the current app in routes.</li>
<li><a href="">#3407</a> Add <code>hidden</code> to callback arguments, hiding the callback from appearing in the devtool callback graph.</li>
<li><a href="">#3424</a> Adds support for <code>Patch</code> on clientside callbacks class <code>dash_clientside.Patch</code>, as well as supporting side updates, eg: (Running, SetProps).</li>
<li><a href="">#3347</a> Added 'api_endpoint' to <code>callback</code> to expose api endpoints at the provided path for use to be executed directly without dash.</li>
</ul>
<h2>Fixed</h2>
<ul>
<li><a href="">#3395</a> Fix Components added through set_props() cannot trigger related callback functions. Fix <a href="">#3316</a></li>
<li><a href="">#3397</a> Add optional callbacks, suppressing callback warning for missing component ids for a single callback.</li>
<li><a href="">#3415</a> Fix the error triggered when only a single no_update is returned for client-side callback functions with multiple Outputs. Fix <a href="">#3366</a></li>
<li><a href="">#3416</a> Fix DeprecationWarning in dash/_jupyter.py by migrating from deprecated ipykernel.comm.Comm to comm module</li>
</ul>
<h2>Dash v3.2.0</h2>
<h2>Added</h2>
<ul>
<li><a href="">#3369</a> Expose <code>dash.NoUpdate</code> type</li>
<li><a href="">#3371</a> Add devtool hook to add components to the devtool bar ui.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/plotly/dash/blob/dev/CHANGELOG.md">dash's changelog</a>.</em></p>
<blockquote>
<h2>[3.3.0] - 2025-11-12</h2>
<h2>Added</h2>
<ul>
<li><a href="">#3395</a> Add position argument to hooks.devtool</li>
<li><a href="">#3403</a> Add app_context to get_app, allowing to get the current app in routes.</li>
<li><a href="">#3407</a> Add <code>hidden</code> to callback arguments, hiding the callback from appearing in the devtool callback graph.</li>
<li><a href="">#3397</a> Add optional callbacks, suppressing callback warning for missing component ids for a single callback.</li>
<li><a href="">#3424</a> Adds support for <code>Patch</code> on clientside callbacks class <code>dash_clientside.Patch</code>, as well as supporting side updates, eg: (Running, SetProps).</li>
<li><a href="">#3347</a> Added 'api_endpoint' to <code>callback</code> to expose api endpoints at the provided path for use to be executed directly without dash.</li>
<li><a href="">#3445</a> Added API to reverse direction of slider component.</li>
<li><a href="">#3460</a> Add <code>/health</code> endpoint for server monitoring and health checks.</li>
<li><a href="">#3465</a> Plotly cloud integrations, add devtool API, placeholder plotly cloud CLI &amp; publish button, <code>dash[cloud]</code> extra dependencies.</li>
</ul>
<h2>Fixed</h2>
<ul>
<li><a href="">#3490</a> Fix stack overflow when circular callbacks are displayed on the devtool callback</li>
<li><a href="">#3395</a> Fix Components added through set_props() cannot trigger related callback functions. Fix <a href="">#3316</a></li>
<li><a href="">#3415</a> Fix the error triggered when only a single no_update is returned for client-side callback functions with multiple Outputs. Fix <a href="">#3366</a></li>
<li><a href="">#3416</a> Fix DeprecationWarning in dash/_jupyter.py by migrating from deprecated ipykernel.comm.Comm to comm module</li>
<li><a href="">#3488</a> Fix pkgutil.find_loader removal in Python 3.14</li>
<li><a href="">#3496</a> Fix dcc.Graph infinite resize loop</li>
</ul>
<h2>Deprecated</h2>
<ul>
<li><a href="">#3482</a> Deprecate dash_table.DataTable with replacement from <code>dash[ag-grid]</code> extra requirement.</li>
</ul>
<h2>[3.2.0] - 2025-07-31</h2>
<h2>Added</h2>
<ul>
<li><a href="">#3369</a> Expose <code>dash.NoUpdate</code> type</li>
<li><a href="">#3371</a> Add devtool hook to add components to the devtool bar ui.</li>
</ul>
<h2>Fixed</h2>
<ul>
<li><a href="">#3353</a> Support pattern-matching/dict ids in <code>dcc.Loading</code> <code>target_components</code></li>
<li><a href="">#3371</a> Fix allow_optional triggering a warning for not found input.</li>
<li><a href="">#3379</a> Fix dcc.Graph backward compatibility with dash 2.0 for ddk.Graph</li>
<li><a href="">#3373</a> Fix layout as list and persistence.</li>
</ul>
<h1>Changed</h1>
<ul>
<li><a href="">#3365</a> Warn if dcc.Slider has more than 500 marks and use default instead.</li>
</ul>
<h1>[3.1.1] - 2025-06-29</h1>
<h2>Fixed</h2>
<p><a href="">#3351</a> Fix multi-page app with <code>suppress_callback_exceptions=True</code></p>
<h2>[3.1.0] - 2025-06-27</h2>
<h2>Fixed</h2>
<ul>
<li><a href="">#3341</a> Fixed query string parsing regression introduced in 2.18.2 where values containing unencoded <code>&amp;</code> characters were being truncated. <a href="">#3106</a></li>
<li><a href="">#3279</a> Fix an issue where persisted values were incorrectly pruned when updated via callback. Now, callback returned values are correctly stored in the persistence storage. Fix <a href="">#2678</a></li>
<li><a href="">#3298</a> Fix dev_only resources filtering.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>68d598f</code></a> updated bundles</li>
<li><a href=""><code>7fda6ba</code></a> Merge pull request <a href="">#3507</a> from plotly/master-3.3.0</li>
<li><a href=""><code>3bdbc40</code></a> Version 3.3.0 build artifacts</li>
<li><a href=""><code>6166c51</code></a> Merge branch 'dev' into master-3.3.0</li>
<li><a href=""><code>d468260</code></a> Merge pull request <a href="">#3505</a> from plotly/version-3.3.0</li>
<li><a href=""><code>3541ab5</code></a> Version 3.3.0</li>
<li><a href=""><code>a82e198</code></a> update build deps</li>
<li><a href=""><code>2308f19</code></a> Merge pull request <a href="">#3490</a> from Aaron-Wrote-This/bugfix/callback_graph_recursio...</li>
<li><a href=""><code>038b882</code></a> Bugfix callback graph with circular callbacks by adding visited markers</li>
<li><a href=""><code>b3b148c</code></a> Merge pull request <a href="">#3482</a> from plotly/deprecate-dash-table</li>
<li>Additional commits viewable in <a href="https://github.com/plotly/dash/compare/v3.0.2...v3.3.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=dash&package-manager=pip&previous-version=3.0.2&new-version=3.3.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24d5a26abea1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
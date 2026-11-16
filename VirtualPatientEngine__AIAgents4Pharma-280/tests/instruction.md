# Issue

**Title:** deps(deps): bump plotly from 5.24.1 to 6.3.0

## Description

Bumps [plotly](https://github.com/plotly/plotly.py) from 5.24.1 to 6.3.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/plotly/plotly.py/releases">plotly's releases</a>.</em></p>
<blockquote>
<h2>v6.3.0</h2>
<h3>Updated</h3>
<ul>
<li>Updated Plotly.js from version 3.0.1 to version 3.1.0. See the plotly.js <a href="https://github.com/plotly/plotly.js/releases">release notes</a> for more information. [<a href="">#5318</a>]</li>
</ul>
<h3>Added</h3>
<ul>
<li>Exposed <code>plotly.io.get_chrome()</code> as a function which can be called from within a Python script. [<a href="">#5282</a>]</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>Resolved issue causing extraneous engine deprecation warnings [<a href="">#5287</a>], with thanks to <a href="https://github.com/jdbeel"><code>@​jdbeel</code></a> for the contribution!</li>
</ul>
<h2>v6.2.0</h2>
<h3>Added</h3>
<ul>
<li>Add SRI (Subresource Integrity) hash support for CDN script tags when using <code>include_plotlyjs='cdn'</code>. This enhances security by ensuring browser verification of CDN-served plotly.js files [<a href="">#5165</a>] (with thanks to <a href="https://github.com/ddworken"><code>@​ddworken</code></a>)</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>Allow setting Plotly.js path via <code>pio.defaults</code> [<a href="">#5207</a>]</li>
</ul>
<h3>Changed</h3>
<ul>
<li>Refactor validation code to reduce bundle size [<a href="">#5214</a>] (with thanks to <a href="https://github.com/bmaranville"><code>@​bmaranville</code></a>)</li>
<li>Add deprecation warnings when using Kaleido v0 or deprecated image export features [<a href="">#5177</a>]</li>
</ul>
<h2>v6.1.2</h2>
<h3>Fixed</h3>
<ul>
<li>Fix type checking and code highlighting for <code>graph_objects</code> classes [<a href="">#5199</a>]</li>
</ul>
<h2>v6.1.1</h2>
<h3>Fixed</h3>
<ul>
<li>Prevent swallowing of <code>ValueError</code> when creating a figure with subplots [<a href="">#3888</a>]</li>
<li>Fix issue causing <code>fig.write_image()</code> to not generate an image [<a href="">#5193</a>]</li>
</ul>
<h2>v6.1.0</h2>
<h3>Updated</h3>
<ul>
<li>Add support for Kaleido&gt;=v1.0.0 for image generation [<a href="">#5062</a>, <a href="">#5177</a>]</li>
<li>Reduce package bundle size by 18-24% via changes to code generation [<a href="">#4978</a>]</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>Fix third-party widget display issues in v6 [<a href="">#5102</a>]</li>
<li>Add handling for case where <code>jupyterlab</code> or <code>notebook</code> is not installed [<a href="">#5104</a>]</li>
<li>Fix issue causing Plotly.js script to be embedded multiple times in Jupyter notebooks [<a href="">#5112</a>]</li>
<li>Re-add MIME renderer JupyterLab extension with JupyterLab 4 support to reduce file sizes for offline notebooks [<a href="">#5096</a>]</li>
<li>Fix issue preventing plots from rendering in HTML notebook export when using 'vscode+notebook' renderer [<a href="">#5154</a>]</li>
</ul>
<h2>v6.1.0rc0</h2>
<h3>Updated</h3>
<ul>
<li>Add support for Kaleido&gt;=v1.0.0 for image generation, and deprecate support for Kaleido&lt;1 and Orca [<a href="">#5062</a>]</li>
<li>Reduce package bundle size by 18-24% via changes to code generation [<a href="">#4978</a>]</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>Fix third-party widget display issues in v6 [<a href="">#5102</a>]</li>
<li>Add handling for case where <code>jupyterlab</code> or <code>notebook</code> is not installed [<a href="">#5104</a>]</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/plotly/plotly.py/blob/main/CHANGELOG.md">plotly's changelog</a>.</em></p>
<blockquote>
<h2>[6.3.0] - 2025-08-12</h2>
<h3>Updated</h3>
<ul>
<li>Updated Plotly.js from version 3.0.1 to version 3.1.0. See the plotly.js <a href="https://github.com/plotly/plotly.js/releases">release notes</a> for more information. [<a href="">#5318</a>]</li>
</ul>
<h3>Added</h3>
<ul>
<li>Exposed <code>plotly.io.get_chrome()</code> as a function which can be called from within a Python script. [<a href="">#5282</a>]</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>Resolved issue causing extraneous engine deprecation warnings [<a href="">#5287</a>], with thanks to <a href="https://github.com/jdbeel"><code>@​jdbeel</code></a> for the contribution!</li>
</ul>
<h2>[6.2.0] - 2025-06-26</h2>
<h3>Added</h3>
<ul>
<li>Add SRI (Subresource Integrity) hash support for CDN script tags when using <code>include_plotlyjs='cdn'</code>. This enhances security by ensuring browser verification of CDN-served plotly.js files [<a href="">#5165</a>] (with thanks to <a href="https://github.com/ddworken"><code>@​ddworken</code></a>)</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>Allow setting Plotly.js path via <code>pio.defaults</code> [<a href="">#5207</a>]</li>
</ul>
<h3>Changed</h3>
<ul>
<li>Refactor validation code to reduce bundle size [<a href="">#5214</a>] (with thanks to <a href="https://github.com/bmaranville"><code>@​bmaranville</code></a>)</li>
<li>Add deprecation warnings when using Kaleido v0 or deprecated image export features [<a href="">#5177</a>]</li>
</ul>
<h2>[6.1.2] - 2025-05-27</h2>
<h3>Fixed</h3>
<ul>
<li>Fix type checking and code highlighting for <code>graph_objects</code> classes [<a href="">#5199</a>]</li>
</ul>
<h2>[6.1.1] - 2025-05-20</h2>
<h3>Fixed</h3>
<ul>
<li>Prevent swallowing of <code>ValueError</code> when creating a figure with subplots [<a href="">#3888</a>]</li>
<li>Fix issue causing <code>fig.write_image()</code> to not generate an image [<a href="">#5193</a>]</li>
</ul>
<h2>[6.1.0] - 2025-05-15</h2>
<h3>Updated</h3>
<ul>
<li>Add support for Kaleido&gt;=v1.0.0 for image generation [<a href="">#5062</a>, <a href="">#5177</a>]</li>
<li>Reduce package bundle size by 18-24% via changes to code generation [<a href="">#4978</a>]</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>Fix third-party widget display issues in v6 [<a href="">#5102</a>]</li>
<li>Add handling for case where <code>jupyterlab</code> or <code>notebook</code> is not installed [<a href="">#5104</a>]</li>
<li>Fix issue causing Plotly.js script to be embedded multiple times in Jupyter notebooks [<a href="">#5112</a>]</li>
<li>Re-add MIME renderer JupyterLab extension with JupyterLab 4 support to reduce file sizes for offline notebooks [<a href="">#5096</a>]</li>
<li>Fix issue preventing plots from rendering in HTML notebook export when using 'vscode+notebook' renderer [<a href="">#5154</a>]</li>
</ul>
<h2>[6.0.1] - 2025-03-14</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>53572f6</code></a> Update uv lock file</li>
<li><a href=""><code>3b5a65f</code></a> version changes for v6.3.0</li>
<li><a href=""><code>6b7565b</code></a> Merge pull request <a href="">#5318</a> from plotly/update-plotlyjs-3.1.0</li>
<li><a href=""><code>c2225b7</code></a> add DeprecationWarning for upcoming change in locationmode 'country names'</li>
<li><a href=""><code>deef7a3</code></a> update plotly/labextension</li>
<li><a href=""><code>0589b22</code></a> upgrade plotly.js to 3.1.0</li>
<li><a href=""><code>694b036</code></a> Merge pull request <a href="">#5308</a> from plotly/update-doc-string</li>
<li><a href=""><code>480a1af</code></a> Merge pull request <a href="">#5287</a> from jdbeel/update-external-renderer-default</li>
<li><a href=""><code>c07de25</code></a> Merge branch 'main' into update-external-renderer-default</li>
<li><a href=""><code>9f4b774</code></a> Update _json.py</li>
<li>Additional commits viewable in <a href="https://github.com/plotly/plotly.py/compare/v5.24.1...v6.3.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=plotly&package-manager=uv&previous-version=5.24.1&new-version=6.3.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a25f90579aa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
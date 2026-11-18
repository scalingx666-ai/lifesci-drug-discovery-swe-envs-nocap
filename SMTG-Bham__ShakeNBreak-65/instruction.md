# Issue

**Title:** Bump the python-packages group with 1 update

## Description

Bumps the python-packages group with 1 update: [pytest-mpl](https://github.com/matplotlib/pytest-mpl).

Updates `pytest-mpl` from 0.16.1 to 0.17.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/matplotlib/pytest-mpl/releases">pytest-mpl's releases</a>.</em></p>
<blockquote>
<h2>v0.17.0</h2>
<!-- raw HTML omitted -->
<h2>What's Changed</h2>
<h3>Fixes</h3>
<ul>
<li>Improve Logging Configuration: don't modify root logger by <a href="https://github.com/theOehrly"><code>@​theOehrly</code></a> in <a href="">matplotlib/pytest-mpl#182</a></li>
<li>Improve error reporting when test raises an exception by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#193</a></li>
<li>MNT: Compat with pytest 8.1 by <a href="https://github.com/pllim"><code>@​pllim</code></a> in <a href="">matplotlib/pytest-mpl#219</a></li>
</ul>
<h3>Exciting New Features 🎉</h3>
<ul>
<li>Added support for EPS, PDF, and SVG image comparison by <a href="https://github.com/astrofrog"><code>@​astrofrog</code></a> in <a href="">matplotlib/pytest-mpl#194</a></li>
<li>Started implementing support for deterministic figure output by <a href="https://github.com/astrofrog"><code>@​astrofrog</code></a> in <a href="">matplotlib/pytest-mpl#196</a></li>
<li>Add missing CLI and INI options for a consistent API by <a href="https://github.com/astrofrog"><code>@​astrofrog</code></a> in <a href="">matplotlib/pytest-mpl#181</a></li>
<li>Avoid using <code>py.path</code> by <a href="https://github.com/eerovaher"><code>@​eerovaher</code></a> in <a href="">matplotlib/pytest-mpl#207</a></li>
<li>Allow using <code>-p no:legacypath</code> with <code>pytest</code> &gt;= 7 by <a href="https://github.com/eerovaher"><code>@​eerovaher</code></a> in <a href="">matplotlib/pytest-mpl#213</a></li>
</ul>
<h3>Other Changes</h3>
<ul>
<li>Add initial Sphinx docs by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#174</a></li>
<li>Add documentation on avoiding <code>PytestReturnNotNoneWarning</code> by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#185</a></li>
<li>Add RTD config by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#195</a></li>
<li>Migrate docs from <code>README.rst</code> to website by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#199</a></li>
<li>Set deterministic to True for vector graphics and warn about change to True in future for PNG by <a href="https://github.com/astrofrog"><code>@​astrofrog</code></a> in <a href="">matplotlib/pytest-mpl#197</a></li>
</ul>
<h3>Infrastructure Changes</h3>
<ul>
<li>Verify class-based testing configurations produce the expected results by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#175</a></li>
<li>Update testing and CI for Matplotlib v3.6 by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#184</a></li>
<li>Upgrade for tox 4 by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#191</a></li>
<li>Upgrade CI package versions by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#215</a></li>
<li>Test wheel with 3.11 until <code>python-dateutil</code> is updated for 3.12 by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#217</a></li>
<li>Fix unclosed test files by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#222</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/theOehrly"><code>@​theOehrly</code></a> made their first contribution in <a href="">matplotlib/pytest-mpl#182</a></li>
<li><a href="https://github.com/eerovaher"><code>@​eerovaher</code></a> made their first contribution in <a href="">matplotlib/pytest-mpl#207</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/matplotlib/pytest-mpl/compare/v0.16.1...v0.17.0">https://github.com/matplotlib/pytest-mpl/compare/v0.16.1...v0.17.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/matplotlib/pytest-mpl/blob/main/CHANGES.md">pytest-mpl's changelog</a>.</em></p>
<blockquote>
<h2>v0.17.0 - 2024-02-14</h2>
<!-- raw HTML omitted -->
<h3>What's Changed</h3>
<h4>Fixes</h4>
<ul>
<li>Improve Logging Configuration: don't modify root logger by <a href="https://github.com/theOehrly"><code>@​theOehrly</code></a> in <a href="">matplotlib/pytest-mpl#182</a></li>
<li>Improve error reporting when test raises an exception by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#193</a></li>
<li>MNT: Compat with pytest 8.1 by <a href="https://github.com/pllim"><code>@​pllim</code></a> in <a href="">matplotlib/pytest-mpl#219</a></li>
</ul>
<h4>Exciting New Features 🎉</h4>
<ul>
<li>Added support for EPS, PDF, and SVG image comparison by <a href="https://github.com/astrofrog"><code>@​astrofrog</code></a> in <a href="">matplotlib/pytest-mpl#194</a></li>
<li>Started implementing support for deterministic figure output by <a href="https://github.com/astrofrog"><code>@​astrofrog</code></a> in <a href="">matplotlib/pytest-mpl#196</a></li>
<li>Add missing CLI and INI options for a consistent API by <a href="https://github.com/astrofrog"><code>@​astrofrog</code></a> in <a href="">matplotlib/pytest-mpl#181</a></li>
<li>Avoid using <code>py.path</code> by <a href="https://github.com/eerovaher"><code>@​eerovaher</code></a> in <a href="">matplotlib/pytest-mpl#207</a></li>
<li>Allow using <code>-p no:legacypath</code> with <code>pytest</code> &gt;= 7 by <a href="https://github.com/eerovaher"><code>@​eerovaher</code></a> in <a href="">matplotlib/pytest-mpl#213</a></li>
</ul>
<h4>Other Changes</h4>
<ul>
<li>Add initial Sphinx docs by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#174</a></li>
<li>Add documentation on avoiding <code>PytestReturnNotNoneWarning</code> by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#185</a></li>
<li>Add RTD config by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#195</a></li>
<li>Migrate docs from <code>README.rst</code> to website by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#199</a></li>
<li>Set deterministic to True for vector graphics and warn about change to True in future for PNG by <a href="https://github.com/astrofrog"><code>@​astrofrog</code></a> in <a href="">matplotlib/pytest-mpl#197</a></li>
</ul>
<h4>Infrastructure Changes</h4>
<ul>
<li>Verify class-based testing configurations produce the expected results by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#175</a></li>
<li>Update testing and CI for Matplotlib v3.6 by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#184</a></li>
<li>Upgrade for tox 4 by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#191</a></li>
<li>Upgrade CI package versions by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#215</a></li>
<li>Test wheel with 3.11 until <code>python-dateutil</code> is updated for 3.12 by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#217</a></li>
<li>Fix unclosed test files by <a href="https://github.com/ConorMacBride"><code>@​ConorMacBride</code></a> in <a href="">matplotlib/pytest-mpl#222</a></li>
</ul>
<h3>New Contributors</h3>
<ul>
<li><a href="https://github.com/theOehrly"><code>@​theOehrly</code></a> made their first contribution in <a href="">matplotlib/pytest-mpl#182</a></li>
<li><a href="https://github.com/eerovaher"><code>@​eerovaher</code></a> made their first contribution in <a href="">matplotlib/pytest-mpl#207</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/matplotlib/pytest-mpl/compare/v0.16.1...v0.17.0">https://github.com/matplotlib/pytest-mpl/compare/v0.16.1...v0.17.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>2b1b8d7</code></a> Merge pull request <a href="">#222</a> from ConorMacBride/fix-unclosed-test-files</li>
<li><a href=""><code>a9713dc</code></a> Fix unclosed test files</li>
<li><a href=""><code>3bd3703</code></a> Merge pull request <a href="">#197</a> from astrofrog/deterministic-default</li>
<li><a href=""><code>db0ea36</code></a> Merge pull request <a href="">#219</a> from pllim/patch-1</li>
<li><a href=""><code>32da10a</code></a> Auto-cancel duplicate CI</li>
<li><a href=""><code>e57d11e</code></a> Remove args from pytest_report_header</li>
<li><a href=""><code>2cdaba0</code></a> Reverts bd7b5c61863170c809c182c9a3bcd81697b52f1a</li>
<li><a href=""><code>267114a</code></a> Fix version comparison</li>
<li><a href=""><code>8d330ec</code></a> MNT: Compat with pytest 8.1</li>
<li><a href=""><code>a6b1319</code></a> Merge pull request <a href="">#220</a> from matplotlib/pre-commit-ci-update-config</li>
<li>Additional commits viewable in <a href="https://github.com/matplotlib/pytest-mpl/compare/v0.16.1...v0.17.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pytest-mpl&package-manager=pip&previous-version=0.16.1&new-version=0.17.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot ignore <dependency name> major version` will close this group update PR and stop Dependabot creating any more for the specific dependency's major version (unless you unignore this specific dependency's major version or upgrade to it yourself)
- `@dependabot ignore <dependency name> minor version` will close this group update PR and stop Dependabot creating any more for the specific dependency's minor version (unless you unignore this specific dependency's minor version or upgrade to it yourself)
- `@dependabot ignore <dependency name>` will close this group update PR and stop Dependabot creating any more for the specific dependency (unless you unignore this specific dependency or upgrade to it yourself)
- `@dependabot unignore <dependency name>` will remove all of the ignore conditions of the specified dependency
- `@dependabot unignore <dependency name> <ignore condition>` will remove the ignore condition of the specified dependency and ignore conditions

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `25a283880d69`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
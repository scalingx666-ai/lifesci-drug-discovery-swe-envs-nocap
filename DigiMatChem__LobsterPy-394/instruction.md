# Issue

**Title:** Bump sphinx-toolbox from 3.10.0 to 4.0.0

## Description

Bumps [sphinx-toolbox](https://github.com/sphinx-toolbox/sphinx-toolbox) from 3.10.0 to 4.0.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/sphinx-toolbox/sphinx-toolbox/releases">sphinx-toolbox's releases</a>.</em></p>
<blockquote>
<h2>Version 4.0.0</h2>
<p>Automatically copied from <a href="https://pypi.org/project/sphinx-toolbox/4.0.0">PyPI</a>.</p>
<hr />
<p>Powered by OctoCheese<br />
<a href="https://octocheese.readthedocs.io">📝 docs</a> | <a href="https://github.com/domdfcoding/octocheese">:octocat: repo</a> | <a href="https://github.com/domdfcoding/octocheese/issues">🙋 issues</a> | <a href="https://github.com/marketplace/octocheese">🏪 marketplace</a></p>
<!-- raw HTML omitted -->
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/sphinx-toolbox/sphinx-toolbox/blob/master/doc-source/changelog.rst">sphinx-toolbox's changelog</a>.</em></p>
<blockquote>
<h2>4.0.0</h2>
<p>The :mod:<code>sphinx_toolbox.source</code> module no longer enables the :mod:<code>sphinx_toolbox.github</code> extension automatically.
If you have :confval:<code>source_link_target</code> set to <code>'GitHub'</code> you may need to enable the extension manually.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d1750cf</code></a> Bump version v3.10.0 -&gt; v4.0.0</li>
<li><a href=""><code>d66f7ad</code></a> Update warningsfilter for newer click pending new consolekit.</li>
<li><a href=""><code>adf42cc</code></a> Updated files with 'repo_helper'. (<a href="">#186</a>)</li>
<li><a href=""><code>c9ad057</code></a> Don't enable the <code>sphinx_toolbox.github</code> extension as part of the ``source`...</li>
<li>See full diff in <a href="https://github.com/sphinx-toolbox/sphinx-toolbox/compare/v3.10.0...v4.0.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=sphinx-toolbox&package-manager=pip&previous-version=3.10.0&new-version=4.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c461aa9fea14`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
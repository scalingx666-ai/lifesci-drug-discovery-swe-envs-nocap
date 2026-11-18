# Issue

**Title:** Bump sphinx-toolbox from 4.1.2 to 4.2.0

## Description

Bumps [sphinx-toolbox](https://github.com/sphinx-toolbox/sphinx-toolbox) from 4.1.2 to 4.2.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/sphinx-toolbox/sphinx-toolbox/releases">sphinx-toolbox's releases</a>.</em></p>
<blockquote>
<h2>Version 4.2.0</h2>
<p>Automatically copied from <a href="https://pypi.org/project/sphinx-toolbox/4.2.0">PyPI</a>.</p>
<hr />
<p>Powered by OctoCheese<br />
<a href="https://octocheese.readthedocs.io">📝 docs</a> | <a href="https://github.com/domdfcoding/octocheese">:octocat: repo</a> | <a href="https://github.com/domdfcoding/octocheese/issues">🙋 issues</a> | <a href="https://github.com/marketplace/octocheese">🏪 marketplace</a></p>
<!-- raw HTML omitted -->
<h2>Version 4.2.0rc1</h2>
<p>Automatically copied from <a href="https://pypi.org/project/sphinx-toolbox/4.2.0rc1">PyPI</a>.</p>
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
<h2>4.2.0</h2>
<ul>
<li>Remove cap on <code>ruamel.yaml</code> (:pr:<code>214</code>)</li>
<li>Updates to <code>more_autodoc</code> for Sphinx 9 compatibility.</li>
</ul>
<h2>4.1.0</h2>
<p>General compatibility updates</p>
<h2>4.0.0</h2>
<p>The :mod:<code>sphinx_toolbox.source</code> module no longer enables the :mod:<code>sphinx_toolbox.github</code> extension automatically.
If you have :confval:<code>source_link_target</code> set to <code>'GitHub'</code> you may need to enable the extension manually.</p>
<h2>3.10.0</h2>
<p>Allow GitHub branch to be specified for :rst:dir:<code>installation</code> directive.</p>
<h2>3.9.0</h2>
<p>Improved support for Sphinx 8.1+</p>
<h2>3.8.2</h2>
<p>(BUG) Fix GitHub issue title parsing.</p>
<h2>3.8.0</h2>
<p>Improved support for Sphinx 7.3+</p>
<h2>3.7.0</h2>
<ul>
<li>Add :class:<code>sphinx_toolbox.more_autodoc.variables.PropertyDocumenter</code>.</li>
<li>Use sphinx's <code>HTML5Translator</code> over <code>HTMLTranslator</code>.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9fc6751</code></a> Bump version v4.2.0rc1 -&gt; v4.2.0</li>
<li><a href=""><code>c170d52</code></a> Update changelog.</li>
<li><a href=""><code>15d16d3</code></a> [repo-helper] Configuration Update (<a href="">#215</a>)</li>
<li><a href=""><code>b9f205a</code></a> Update for latest dict2css</li>
<li><a href=""><code>be904f9</code></a> Bump version v4.1.2 -&gt; v4.2.0rc1</li>
<li><a href=""><code>22e881c</code></a> Remove cap on ruamel.yaml (<a href="">#214</a>)</li>
<li><a href=""><code>6289fd2</code></a> Skip Sphinx 9.1 on Python 3.11 as unsupported.</li>
<li><a href=""><code>e0bc43a</code></a> Lint</li>
<li><a href=""><code>065ca07</code></a> Update generic_bases.py for Sphinx 9</li>
<li><a href=""><code>701d248</code></a> Use config-inited to setup overload documenters.</li>
<li>Additional commits viewable in <a href="https://github.com/sphinx-toolbox/sphinx-toolbox/compare/v4.1.2...v4.2.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=sphinx-toolbox&package-manager=pip&previous-version=4.1.2&new-version=4.2.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f799ee340ff0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
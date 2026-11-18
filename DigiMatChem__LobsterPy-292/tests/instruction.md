# Issue

**Title:** Bump sphinx-design from 0.5.0 to 0.6.0

## Description

Bumps [sphinx-design](https://github.com/executablebooks/sphinx-design) from 0.5.0 to 0.6.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/executablebooks/sphinx-design/releases">sphinx-design's releases</a>.</em></p>
<blockquote>
<h2>v0.6.0</h2>
<h2>What's Changed</h2>
<h3>Dependencies</h3>
<ul>
<li>⬆️ Python v3.9-3.12 by <a href="https://github.com/chrisjsewell"><code>@​chrisjsewell</code></a> in <a href="">executablebooks/sphinx-design#186</a></li>
<li>⬆️ Octicon icons to v19.8.0 by <a href="https://github.com/ffvpor"><code>@​ffvpor</code></a> in <a href="">executablebooks/sphinx-design#171</a></li>
</ul>
<h3>New</h3>
<h4>✨ Create custom directives</h4>
<p>You can use the <code>sd_custom_directives</code> configuration option in your <code>conf.py</code> to add custom directives, with default option values:</p>
<pre lang="python"><code>sd_custom_directives = {
  &quot;dropdown-syntax&quot;: {
    &quot;inherit&quot;: &quot;dropdown&quot;,
    &quot;argument&quot;: &quot;Syntax&quot;,
    &quot;options&quot;: {
      &quot;color&quot;: &quot;primary&quot;,
      &quot;icon&quot;: &quot;code&quot;,
    },
  }
}
</code></pre>
<p>The key is the new directive name to add, and the value is a dictionary with the following keys:</p>
<ul>
<li><code>inherit</code>: The directive to inherit from (e.g. <code>dropdown</code>)</li>
<li><code>argument</code>: The default argument (optional, only for directives that take a single argument)</li>
<li><code>options</code>: A dictionary of default options for the directive (optional)</li>
</ul>
<p>by <a href="https://github.com/chrisjsewell"><code>@​chrisjsewell</code></a> in <a href="">executablebooks/sphinx-design#194</a></p>
<h4>✨ sync tabs by URL query parameters</h4>
<p>Synchronised tabs can now be selected by adding a query parameter to the URL, for that sync-group, such as <code>?code=python</code> for</p>
<pre lang="restructuredtext"><code>.. tab-set-code::
<pre><code>.. literalinclude:: snippet.py
    :language: python

.. literalinclude:: snippet.js
    :language: javascript
</code></pre>
<p></code></pre></p>
<p>The last selected tab key, per group, is also persisted <code>SessionStorage</code></p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/executablebooks/sphinx-design/blob/main/CHANGELOG.md">sphinx-design's changelog</a>.</em></p>
<blockquote>
<h2>0.6.0 - 2024-05-23</h2>
<h3>Dependencies</h3>
<ul>
<li>⬆️ Python v3.9-3.12 by {user}<code>chrisjsewell</code> in {pr}<code>186</code></li>
<li>⬆️ Octicon icons to v19.8.0 by {user}<code>ffvpor</code> in {pr}<code>171</code></li>
</ul>
<h3>New</h3>
<h4>✨ Create custom directives</h4>
<p>You can use the <code>sd_custom_directives</code> configuration option in your <code>conf.py</code> to add custom directives, with default option values:</p>
<pre lang="python"><code>sd_custom_directives = {
  &quot;dropdown-syntax&quot;: {
    &quot;inherit&quot;: &quot;dropdown&quot;,
    &quot;argument&quot;: &quot;Syntax&quot;,
    &quot;options&quot;: {
      &quot;color&quot;: &quot;primary&quot;,
      &quot;icon&quot;: &quot;code&quot;,
    },
  }
}
</code></pre>
<p>The key is the new directive name to add, and the value is a dictionary with the following keys:</p>
<ul>
<li><code>inherit</code>: The directive to inherit from (e.g. <code>dropdown</code>)</li>
<li><code>argument</code>: The default argument (optional, only for directives that take a single argument)</li>
<li><code>options</code>: A dictionary of default options for the directive (optional)</li>
</ul>
<p>by {user}<code>chrisjsewell</code> in {pr}<code>194</code></p>
<h4>✨ sync tabs by URL query parameters</h4>
<p>Synchronised tabs can now be selected by adding a query parameter to the URL, for that sync-group, such as <code>?code=python</code> for</p>
<pre lang="restructuredtext"><code>.. tab-set-code::
<pre><code>.. literalinclude:: snippet.py
    :language: python

.. literalinclude:: snippet.js
    :language: javascript
</code></pre>
<p></code></pre></p>
<p>The last selected tab key, per group, is also persisted to <code>SessionStorage</code></p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>16af1dc</code></a> 🚀 Release v0.6.0 (<a href="">#197</a>)</li>
<li><a href=""><code>f1427ce</code></a> ✨ NEW: sync tabs by URL query parameters (<a href="">#196</a>)</li>
<li><a href=""><code>a6f97b8</code></a> 🐛 FIX: do not close <code>input</code> tag (<a href="">#195</a>)</li>
<li><a href=""><code>e258b45</code></a> 👌 Use reference name by default for internal link cards (<a href="">#183</a>)</li>
<li><a href=""><code>3374383</code></a> ✨ NEW: Create custom directives (<a href="">#194</a>)</li>
<li><a href=""><code>af64472</code></a> 🔧 Add FIPS compliant flag to md5 call (<a href="">#162</a>)</li>
<li><a href=""><code>074f21f</code></a> 👌 Remove duplicate CSS hashing for sphinx &gt;= 7.1 (<a href="">#193</a>)</li>
<li><a href=""><code>be1b85d</code></a> 🐛 Fix tab-item label with nested syntax (<a href="">#135</a>)</li>
<li><a href=""><code>89aaa26</code></a> 👌 Improve dropdown title bar (<a href="">#192</a>)</li>
<li><a href=""><code>169c09d</code></a> 📚 Change syntax dropdown color (<a href="">#191</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/executablebooks/sphinx-design/compare/v0.5.0...v0.6.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=sphinx-design&package-manager=pip&previous-version=0.5.0&new-version=0.6.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d3000ca94cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
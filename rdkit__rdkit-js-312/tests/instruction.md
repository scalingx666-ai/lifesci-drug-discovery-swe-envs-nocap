# Issue

**Title:** Bump typedoc from 0.23.21 to 0.23.26

## Description

Bumps [typedoc](https://github.com/TypeStrong/TypeDoc) from 0.23.21 to 0.23.26.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/TypeDoc/releases">typedoc's releases</a>.</em></p>
<blockquote>
<h2>v0.23.26</h2>
<h3>Features</h3>
<ul>
<li>Added <code>Application.EVENT_VALIDATE_PROJECT</code> event for plugins which implement custom validation, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2183">#2183</a>.</li>
<li>Plugins may now return an object from external symbol resolvers, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2066">#2066</a>.</li>
<li>Expose <code>Comment.displayPartsToMarkdown</code> on for themes overwriting the <code>comment</code> helper, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2115">#2115</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Fix crash when converting <code>export default undefined</code>, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2175">#2175</a>.</li>
<li>Fix error in console when clicking on headings in the readme, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2170">#2170</a>.</li>
<li>TypeDoc will now ignore parameters of callback parameters when validating that all parameters have documentation, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2154">#2154</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/captain-torch"><code>@​captain-torch</code></a></li>
<li><a href="https://github.com/loopingz"><code>@​loopingz</code></a></li>
<li><a href="https://github.com/RebeccaStevens"><code>@​RebeccaStevens</code></a></li>
</ul>
<h2>v0.23.25</h2>
<h3>Breaking Changes</h3>
<ul>
<li>Upgraded Shiki, if your highlight theme was set to <code>material-&lt;theme&gt;</code>, the value will need to be changed to
<code>material-theme-&lt;theme&gt;</code>, see the <a href="https://github.com/shikijs/shiki/blob/main/CHANGELOG.md#0130--2023-01-27">Shiki release notes</a>.</li>
</ul>
<h3>Features</h3>
<ul>
<li>Added new <code>excludeNotDocumentedKinds</code> variable to control which reflection types can be removed
by the <code>excludeNotDocumented</code> option, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2162">#2162</a>.</li>
<li>Added <code>typedoc.jsonc</code>, <code>typedoc.config.js</code>, <code>typedoc.config.cjs</code>, <code>typedoc.cjs</code> to the list of files
which TypeDoc will automatically use as configuration files.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Entry points under <code>node_modules</code> will no longer be ignored, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2151">#2151</a>.</li>
<li>Corrected behavior of <code>excludeNotDocumented</code> on arrow function-variables, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2156">#2156</a>.</li>
<li>Added <code>package.json</code> to exports declaration.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/boneskull"><code>@​boneskull</code></a></li>
<li><a href="https://github.com/Mikkal24"><code>@​Mikkal24</code></a></li>
<li><a href="https://github.com/zamiell"><code>@​zamiell</code></a></li>
</ul>
<h2>v0.23.24</h2>
<h3>Bug Fixes</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/TypeStrong/typedoc/blob/master/CHANGELOG.md">typedoc's changelog</a>.</em></p>
<blockquote>
<h2>v0.23.26 (2023-02-26)</h2>
<h3>Features</h3>
<ul>
<li>Added <code>Application.EVENT_VALIDATE_PROJECT</code> event for plugins which implement custom validation, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2183">#2183</a>.</li>
<li>Plugins may now return an object from external symbol resolvers, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2066">#2066</a>.</li>
<li>Expose <code>Comment.displayPartsToMarkdown</code> on for themes overwriting the <code>comment</code> helper, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2115">#2115</a>.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Fix crash when converting <code>export default undefined</code>, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2175">#2175</a>.</li>
<li>Fix error in console when clicking on headings in the readme, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2170">#2170</a>.</li>
<li>TypeDoc will now ignore parameters of callback parameters when validating that all parameters have documentation, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2154">#2154</a>.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/captain-torch"><code>@​captain-torch</code></a></li>
<li><a href="https://github.com/loopingz"><code>@​loopingz</code></a></li>
<li><a href="https://github.com/RebeccaStevens"><code>@​RebeccaStevens</code></a></li>
</ul>
<h2>v0.23.25 (2023-02-11)</h2>
<h3>Breaking Changes</h3>
<ul>
<li>Upgraded Shiki, if your highlight theme was set to <code>material-&lt;theme&gt;</code>, the value will need to be changed to
<code>material-theme-&lt;theme&gt;</code>, see the <a href="https://github.com/shikijs/shiki/blob/main/CHANGELOG.md#0130--2023-01-27">Shiki release notes</a>.</li>
</ul>
<h3>Features</h3>
<ul>
<li>Added new <code>excludeNotDocumentedKinds</code> variable to control which reflection types can be removed
by the <code>excludeNotDocumented</code> option, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2162">#2162</a>.</li>
<li>Added <code>typedoc.jsonc</code>, <code>typedoc.config.js</code>, <code>typedoc.config.cjs</code>, <code>typedoc.cjs</code> to the list of files
which TypeDoc will automatically use as configuration files.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Entry points under <code>node_modules</code> will no longer be ignored, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2151">#2151</a>.</li>
<li>Corrected behavior of <code>excludeNotDocumented</code> on arrow function-variables, <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2156">#2156</a>.</li>
<li>Added <code>package.json</code> to exports declaration.</li>
</ul>
<h3>Thanks!</h3>
<ul>
<li><a href="https://github.com/boneskull"><code>@​boneskull</code></a></li>
<li><a href="https://github.com/Mikkal24"><code>@​Mikkal24</code></a></li>
<li><a href="https://github.com/zamiell"><code>@​zamiell</code></a></li>
</ul>
<h2>v0.23.24 (2023-01-07)</h2>
<h3>Bug Fixes</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c75f44f</code></a> Update changelog for release</li>
<li><a href=""><code>67355f2</code></a> Bump version to 0.23.26</li>
<li><a href=""><code>86da0f3</code></a> Fix lint</li>
<li><a href=""><code>54c86d8</code></a> Expose displayPartsToMarkdown</li>
<li><a href=""><code>37fe883</code></a> Ignore parameters of parameters</li>
<li><a href=""><code>0a52e74</code></a> Fix <a href="https://github-redirect.dependabot.com/TypeStrong/TypeDoc/issues/2170">#2170</a></li>
<li><a href=""><code>7a48a17</code></a> Document additional changes</li>
<li><a href=""><code>3343cc4</code></a> Fix crash when converting undefined default export</li>
<li><a href=""><code>6ee136a</code></a> feat: add validator run event to allow plugins to perform custom validation (...</li>
<li><a href=""><code>1d4922c</code></a> Update minimatch to avoid type hackery</li>
<li>Additional commits viewable in <a href="https://github.com/TypeStrong/TypeDoc/compare/v0.23.21...v0.23.26">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typedoc&package-manager=npm_and_yarn&previous-version=0.23.21&new-version=0.23.26)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3cd282d865c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
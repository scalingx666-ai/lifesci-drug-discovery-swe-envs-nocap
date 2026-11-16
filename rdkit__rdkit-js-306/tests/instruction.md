# Issue

**Title:** Bump prettier from 2.8.0 to 2.8.4

## Description

Bumps [prettier](https://github.com/prettier/prettier) from 2.8.0 to 2.8.4.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/prettier/prettier/releases">prettier's releases</a>.</em></p>
<blockquote>
<h2>2.8.4</h2>
<p>🔗 <a href="https://github.com/prettier/prettier/blob/main/CHANGELOG.md#284">Changelog</a></p>
<h2>2.8.3</h2>
<p>Support Angular 15.1</p>
<p>🔗 <a href="https://github.com/prettier/prettier/blob/main/CHANGELOG.md#283">Changelog</a></p>
<h2>2.8.2</h2>
<p>🔗 <a href="https://github.com/prettier/prettier/blob/main/CHANGELOG.md#282">Changelog</a></p>
<h2>2.8.1</h2>
<p>🔗 <a href="https://github.com/prettier/prettier/blob/main/CHANGELOG.md#281">Changelog</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/prettier/prettier/blob/main/CHANGELOG.md">prettier's changelog</a>.</em></p>
<blockquote>
<h1>2.8.4</h1>
<p><a href="https://github.com/prettier/prettier/compare/2.8.3...2.8.4">diff</a></p>
<h4>Fix leading comments in mapped types with <code>readonly</code> (<a href="https://github-redirect.dependabot.com/prettier/prettier/pull/13427">#13427</a> by <a href="https://github.com/thorn0"><code>@​thorn0</code></a>, <a href="https://github.com/sosukesuzuki"><code>@​sosukesuzuki</code></a>)</h4>
<!-- raw HTML omitted -->
<pre lang="tsx"><code>// Input
type Type = {
  // comment
  readonly [key in Foo];
};
<p>// Prettier 2.8.3
type Type = {
readonly // comment
[key in Foo];
};</p>
<p>// Prettier 2.8.4
type Type = {
// comment
readonly [key in Foo];
};
</code></pre></p>
<h4>Group params in opening block statements (<a href="https://github-redirect.dependabot.com/prettier/prettier/pull/14067">#14067</a> by <a href="https://github.com/jamescdavis"><code>@​jamescdavis</code></a>)</h4>
<p>This is a follow-up to <a href="https://github-redirect.dependabot.com/prettier/prettier/issues/13930">#13930</a> to establish wrapping consistency between opening block statements and else blocks by
grouping params in opening blocks. This causes params to break to a new line together and not be split across lines
unless the length of params exceeds the print width. This also updates the else block wrapping to behave exactly the
same as opening blocks.</p>
<!-- raw HTML omitted -->
<pre lang="hbs"><code>{{! Input }}
{{#block param param param param param param param param param param as |blockParam|}}
  Hello
{{else block param param param param param param param param param param as |blockParam|}}
  There
{{/block}}
<p>{{! Prettier 2.8.3 }}
{{#block
param
param
param
param
param
&lt;/tr&gt;&lt;/table&gt;
</code></pre></p>
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e681edb</code></a> Release 2.8.4</li>
<li><a href=""><code>6bb24b2</code></a> Fix leading comments in mapped types with <code>readonly</code> (Cherry-pick <a href="https://github-redirect.dependabot.com/prettier/prettier/issues/13427">#13427</a>) (<a href="https://github-redirect.dependabot.com/prettier/prettier/issues/1">#1</a>...</li>
<li><a href=""><code>399f2fa</code></a> Add changelog for <a href="https://github-redirect.dependabot.com/prettier/prettier/issues/14206">#14206</a> (<a href="https://github-redirect.dependabot.com/prettier/prettier/issues/14311">#14311</a>)</li>
<li><a href=""><code>9842b29</code></a> Recognize <code>@satisfies</code> in Closure-style type casts (<a href="https://github-redirect.dependabot.com/prettier/prettier/issues/14262">#14262</a>)</li>
<li><a href=""><code>bc18fa4</code></a> Fix incorrect removal of parentheses when using an <code>infer</code> with a constraint ...</li>
<li><a href=""><code>f602be5</code></a> Update <code>embeddedLanguageFormatting</code> option documentation (<a href="https://github-redirect.dependabot.com/prettier/prettier/issues/14048">#14048</a>)</li>
<li><a href=""><code>37fb53a</code></a> [handlebars] group params in opening block statements (<a href="https://github-redirect.dependabot.com/prettier/prettier/issues/14067">#14067</a>)</li>
<li><a href=""><code>310a5b1</code></a> Handlebars: Improve HTML void element check (<a href="https://github-redirect.dependabot.com/prettier/prettier/issues/14110">#14110</a>)</li>
<li><a href=""><code>62195dd</code></a> Add .sl to the list of silentlyIgnoredDirs (<a href="https://github-redirect.dependabot.com/prettier/prettier/issues/14206">#14206</a>)</li>
<li><a href=""><code>bf406f7</code></a> Clean changelog</li>
<li>Additional commits viewable in <a href="https://github.com/prettier/prettier/compare/2.8.0...2.8.4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=prettier&package-manager=npm_and_yarn&previous-version=2.8.0&new-version=2.8.4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `693961fbd6f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
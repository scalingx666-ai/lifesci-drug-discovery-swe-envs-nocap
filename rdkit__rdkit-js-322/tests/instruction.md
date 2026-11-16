# Issue

**Title:** Bump prettier from 2.8.4 to 2.8.7

## Description

Bumps [prettier](https://github.com/prettier/prettier) from 2.8.4 to 2.8.7.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/prettier/prettier/releases">prettier's releases</a>.</em></p>
<blockquote>
<h2>2.8.7</h2>
<ul>
<li>Allow multiple decorators on same getter/setter</li>
</ul>
<p>🔗 <a href="https://github.com/prettier/prettier/blob/main/CHANGELOG.md#287">Changelog</a></p>
<h2>2.8.6</h2>
<ul>
<li>Allow decorators on private members and class expressions</li>
</ul>
<p>🔗 <a href="https://github.com/prettier/prettier/blob/main/CHANGELOG.md#286">Changelog</a></p>
<h2>2.8.5</h2>
<ul>
<li>Support TypeScript 5.0</li>
</ul>
<p>🔗 <a href="https://github.com/prettier/prettier/blob/main/CHANGELOG.md#285">Changelog</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/prettier/prettier/blob/main/CHANGELOG.md">prettier's changelog</a>.</em></p>
<blockquote>
<h1>2.8.7</h1>
<p><a href="https://github.com/prettier/prettier/compare/2.8.6...2.8.7">diff</a></p>
<h4>Allow multiple decorators on same getter/setter (<a href="">#14584</a> by <a href="https://github.com/fisker"><code>@​fisker</code></a>)</h4>
<!-- raw HTML omitted -->
<pre lang="ts"><code>// Input
class A {
  @decorator()
  get foo () {}
<p><a href="https://github.com/decorator"><code>@​decorator</code></a>()
set foo (value) {}
}</p>
<p>// Prettier 2.8.6
SyntaxError: Decorators cannot be applied to multiple get/set accessors of the same name. (5:3)
3 |   get foo () {}
4 |<br />
&gt; 5 |   <a href="https://github.com/decorator"><code>@​decorator</code></a>()
|   ^^^^^^^^^^^^
6 |   set foo (value) {}
7 | }</p>
<p>// Prettier 2.8.7
class A {
<a href="https://github.com/decorator"><code>@​decorator</code></a>()
get foo() {}</p>
<p><a href="https://github.com/decorator"><code>@​decorator</code></a>()
set foo(value) {}
}
</code></pre></p>
<h1>2.8.6</h1>
<p><a href="https://github.com/prettier/prettier/compare/2.8.5...2.8.6">diff</a></p>
<h4>Allow decorators on private members and class expressions (<a href="">#14548</a> by <a href="https://github.com/fisker"><code>@​fisker</code></a>)</h4>
<!-- raw HTML omitted -->
<pre lang="ts"><code>// Input
class A {
  @decorator()
  #privateMethod () {}
}
<p>&lt;/tr&gt;&lt;/table&gt;
</code></pre></p>
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>543a9d7</code></a> Release 2.8.7</li>
<li><a href=""><code>f9fae7f</code></a> Allow multiple decorators on same getter/setter (<a href="">#14584</a>)</li>
<li><a href=""><code>10fe1ed</code></a> Release 2.8.6</li>
<li><a href=""><code>44aef0b</code></a> Allow decorator on private members and class expressions (<a href="">#14548</a>)</li>
<li><a href=""><code>ddf3b43</code></a> Clean changelog</li>
<li><a href=""><code>71ba29f</code></a> Git blame ignore 2.8.5</li>
<li><a href=""><code>c1808e8</code></a> Bump Prettier dependency to 2.8.5</li>
<li><a href=""><code>0a79535</code></a> Release 2.8.5</li>
<li><a href=""><code>019ebe5</code></a> Support TypeScript 5 (backport <a href="">#14391</a> and <a href="">#13819</a>) (<a href="">#14512</a>)</li>
<li><a href=""><code>e7b383b</code></a> Support <code>max_line_length=off</code> when parsing <code>.editorconfig</code> (<a href="">#14516</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/prettier/prettier/compare/2.8.4...2.8.7">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=prettier&package-manager=npm_and_yarn&previous-version=2.8.4&new-version=2.8.7)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `575ca10b6b01`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Bump react-dom from 18.1.0 to 18.2.0

## Description

Bumps [react-dom](https://github.com/facebook/react/tree/HEAD/packages/react-dom) from 18.1.0 to 18.2.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/facebook/react/releases">react-dom's releases</a>.</em></p>
<blockquote>
<h2>18.2.0 (June 14, 2022)</h2>
<h3>React DOM</h3>
<ul>
<li>Provide a component stack as a second argument to <code>onRecoverableError</code>. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24591">#24591</a>)</li>
<li>Fix hydrating into <code>document</code> causing a blank page on mismatch. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24523">#24523</a>)</li>
<li>Fix false positive hydration errors with Suspense. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24480">#24480</a> and  <a href="https://github.com/acdlite"><code>@​acdlite</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24532">#24532</a>)</li>
<li>Fix ignored <code>setState</code> in Safari when adding an iframe. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24459">#24459</a>)</li>
</ul>
<h3>React DOM Server</h3>
<ul>
<li>Pass information about server errors to the client. (<a href="https://github.com/salazarm"><code>@​salazarm</code></a> and <a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24551">#24551</a> and <a href="https://github-redirect.dependabot.com/facebook/react/pull/24591">#24591</a>)</li>
<li>Allow to provide a reason when aborting the HTML stream. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24680">#24680</a>)</li>
<li>Eliminate extraneous text separators in the HTML where possible. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24630">#24630</a>)</li>
<li>Disallow complex children inside <code>&lt;title&gt;</code> elements to match the browser constraints. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24679">#24679</a>)</li>
<li>Fix buffering in some worker environments by explicitly setting <code>highWaterMark</code> to <code>0</code>. (<a href="https://github.com/jplhomer"><code>@​jplhomer</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24641">#24641</a>)</li>
</ul>
<h3>Server Components (Experimental)</h3>
<ul>
<li>Add support for <code>useId()</code> inside Server Components. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a>) in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24172">#24172</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/facebook/react/blob/main/CHANGELOG.md">react-dom's changelog</a>.</em></p>
<blockquote>
<h2>18.2.0 (June 14, 2022)</h2>
<h3>React DOM</h3>
<ul>
<li>Provide a component stack as a second argument to <code>onRecoverableError</code>. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24591">#24591</a>)</li>
<li>Fix hydrating into <code>document</code> causing a blank page on mismatch. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24523">#24523</a>)</li>
<li>Fix false positive hydration errors with Suspense. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24480">#24480</a> and  <a href="https://github.com/acdlite"><code>@​acdlite</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24532">#24532</a>)</li>
<li>Fix ignored <code>setState</code> in Safari when adding an iframe. (<a href="https://github.com/gaearon"><code>@​gaearon</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24459">#24459</a>)</li>
</ul>
<h3>React DOM Server</h3>
<ul>
<li>Pass information about server errors to the client. (<a href="https://github.com/salazarm"><code>@​salazarm</code></a> and <a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24551">#24551</a> and <a href="https://github-redirect.dependabot.com/facebook/react/pull/24591">#24591</a>)</li>
<li>Allow to provide a reason when aborting the HTML stream. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24680">#24680</a>)</li>
<li>Eliminate extraneous text separators in the HTML where possible. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24630">#24630</a>)</li>
<li>Disallow complex children inside <code>&lt;title&gt;</code> elements to match the browser constraints. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24679">#24679</a>)</li>
<li>Fix buffering in some worker environments by explicitly setting <code>highWaterMark</code> to <code>0</code>. (<a href="https://github.com/jplhomer"><code>@​jplhomer</code></a> in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24641">#24641</a>)</li>
</ul>
<h3>Server Components (Experimental)</h3>
<ul>
<li>Add support for <code>useId()</code> inside Server Components. (<a href="https://github.com/gnoff"><code>@​gnoff</code></a>) in <a href="https://github-redirect.dependabot.com/facebook/react/pull/24172">#24172</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b345523</code></a> [Fizz] Support abort reasons (<a href="">#24680</a>)</li>
<li><a href=""><code>bcbeb52</code></a> [Fizz] Disallow complex children in &lt;title&gt; elements (<a href="">#24679</a>)</li>
<li><a href=""><code>4f29ba1</code></a> support errorInfo in onRecoverableError (<a href="">#24591</a>)</li>
<li><a href=""><code>26a5b3c</code></a> Explicitly set <code>highWaterMark</code> to 0 for <code>ReadableStream</code> (<a href="">#24641</a>)</li>
<li><a href=""><code>aec5759</code></a> [Fizz] Send errors down to client (<a href="">#24551</a>)</li>
<li><a href=""><code>a276638</code></a> [Fizz] Improve text separator byte efficiency (<a href="">#24630</a>)</li>
<li><a href=""><code>05c34de</code></a> [Test] Outer boundary should not report errors from an inner boundary (<a href="">#24618</a>)</li>
<li><a href=""><code>82c64e1</code></a> Match Preact behavior for boolean props on custom elements (<a href="">#24541</a>)</li>
<li><a href=""><code>2c8a145</code></a> Fix ignored setState in Safari when iframe is touched (<a href="">#24459</a>)</li>
<li><a href=""><code>8197c73</code></a> Support document rendering (<a href="">#24523</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/facebook/react/commits/v18.2.0/packages/react-dom">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~gnoff">gnoff</a>, a new releaser for react-dom since your current version.</p>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=react-dom&package-manager=npm_and_yarn&previous-version=18.1.0&new-version=18.2.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a69214ead5e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Bump shell-quote from 1.10.0 to 1.12.0 in /utils/indigo-service/frontend/ui

## Description

Bumps [shell-quote](https://github.com/ljharb/shell-quote) from 1.10.0 to 1.12.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/ljharb/shell-quote/blob/main/CHANGELOG.md">shell-quote's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/ljharb/shell-quote/compare/v1.11.0...v1.12.0">v1.12.0</a> - 2026-10-02</h2>
<h3>Fixed</h3>
<ul>
<li>[New] <code>parse</code>: support here-documents (<code>&amp;lt;&amp;lt;</code>) <a href=""><code></code></a></li>
</ul>
<h3>Commits</h3>
<ul>
<li>[New] <code>parse</code>: support tab-stripping here-documents (<code>&amp;lt;&amp;lt;-</code>) <a href=""><code>dbfac37</code></a></li>
<li>[New] <code>parse</code>: support output process substitution (<code>&amp;gt;(</code>) <a href=""><code>2053315</code></a></li>
<li>[New] <code>parse</code>: support the <code>case</code> test-next terminator (<code>;;&amp;</code>) <a href=""><code>7d688b9</code></a></li>
<li>[New] <code>parse</code>: support the <code>case</code> fall-through terminator (<code>;&amp;</code>) <a href=""><code>f27010e</code></a></li>
<li>[New] <code>parse</code>: support redirecting output despite <code>noclobber</code> (<code>&amp;gt;|</code>) <a href=""><code>b78d19c</code></a></li>
<li>[New] <code>parse</code>: support opening a file for reading and writing (<code>&amp;lt;&amp;gt;</code>) <a href=""><code>21cc333</code></a></li>
<li>[New] <code>parse</code>: support redirecting stdout and stderr (<code>&amp;&amp;gt;</code>) <a href=""><code>6ad6cd2</code></a></li>
<li>[New] <code>parse</code>: support appending stdout and stderr (<code>&amp;&amp;gt;&amp;gt;</code>) <a href=""><code>90cde9c</code></a></li>
<li>[Dev Deps] update <code>@ljharb/eslint-config</code> <a href=""><code>3a7b4ae</code></a></li>
</ul>
<h2><a href="https://github.com/ljharb/shell-quote/compare/v1.10.0...v1.11.0">v1.11.0</a> - 2026-09-29</h2>
<h3>Fixed</h3>
<ul>
<li>[Refactor] <code>quote</code>: drop a replace that can never match in the single-quote branch <a href=""><code></code></a></li>
<li>[New] <code>parse</code>: support bash ANSI-C quoting (<code>$'...'</code>) <a href=""><code></code></a></li>
</ul>
<h3>Commits</h3>
<ul>
<li>[Fix] <code>quote</code>: reject line terminators in tokens after a <code>comment</code> <a href=""><code>6002b2e</code></a></li>
<li>[Fix] <code>parse</code>: preserve text after special shell parameters <a href=""><code>81b08a5</code></a></li>
<li>[Fix] <code>parse</code>: an escaped backslash does not escape the character after it <a href=""><code>d708019</code></a></li>
<li>[Fix] <code>quote</code>: preserve <code>!</code> in arguments that also contain <code>'</code> <a href=""><code>ad39927</code></a></li>
<li>[Fix] <code>parse</code>: treat <code>$_name</code> as a variable name, not <code>$_</code> followed by text <a href=""><code>28f88cd</code></a></li>
<li>[Fix] <code>quote</code>: preserve empty glob patterns <a href=""><code>35c9b97</code></a></li>
<li>[Fix] <code>quote</code>: escape <code>~</code> in glob patterns to prevent shell tilde-expansion <a href=""><code>239d49c</code></a></li>
<li>[Dev Deps] update <code>@ljharb/eslint-config</code>, <code>auto-changelog</code>, <code>eslint</code>, <code>evalmd</code> <a href=""><code>b1e406e</code></a></li>
<li>[meta] npmignore some files <a href=""><code>ebfc308</code></a></li>
<li>[actions] add permissions <a href=""><code>3429b0d</code></a></li>
<li>[actions] set least-privilege <code>cache-mode</code> <a href=""><code>36f2394</code></a></li>
<li>[Dev Deps] update <code>eslint</code> <a href=""><code>6de9a41</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6ecb8aa</code></a> v1.12.0</li>
<li><a href=""><code>3a7b4ae</code></a> [Dev Deps] update <code>@ljharb/eslint-config</code></li>
<li><a href=""><code>7d688b9</code></a> [New] <code>parse</code>: support the <code>case</code> test-next terminator (<code>;;&amp;</code>)</li>
<li><a href=""><code>f27010e</code></a> [New] <code>parse</code>: support the <code>case</code> fall-through terminator (<code>;&amp;</code>)</li>
<li><a href=""><code>90cde9c</code></a> [New] <code>parse</code>: support appending stdout and stderr (<code>&amp;&gt;&gt;</code>)</li>
<li><a href=""><code>6ad6cd2</code></a> [New] <code>parse</code>: support redirecting stdout and stderr (<code>&amp;&gt;</code>)</li>
<li><a href=""><code>2053315</code></a> [New] <code>parse</code>: support output process substitution (<code>&gt;(</code>)</li>
<li><a href=""><code>b78d19c</code></a> [New] <code>parse</code>: support redirecting output despite <code>noclobber</code> (<code>&gt;|</code>)</li>
<li><a href=""><code>21cc333</code></a> [New] <code>parse</code>: support opening a file for reading and writing (<code>\&lt;&gt;</code>)</li>
<li><a href=""><code>dbfac37</code></a> [New] <code>parse</code>: support tab-stripping here-documents (<code>&lt;&lt;-</code>)</li>
<li>Additional commits viewable in <a href="https://github.com/ljharb/shell-quote/compare/v1.10.0...v1.12.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=shell-quote&package-manager=npm_and_yarn&previous-version=1.10.0&new-version=1.12.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/epam/Indigo/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `293860adb2d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
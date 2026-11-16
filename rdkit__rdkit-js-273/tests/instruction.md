# Issue

**Title:** Bump highlight.js from 11.6.0 to 11.7.0

## Description

Bumps [highlight.js](https://github.com/highlightjs/highlight.js) from 11.6.0 to 11.7.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/highlightjs/highlight.js/releases">highlight.js's releases</a>.</em></p>
<blockquote>
<h2>11.7.0 - &quot;Gobble Gobble&quot; Thanksgiving Edition</h2>
<h2>Version 11.7.0</h2>
<p>New Grammars:</p>
<ul>
<li>added 3rd party LookML grammar to SUPPORTED_LANGUAGES <a href="https://github.com/joshtemple">Josh Temple</a></li>
<li>added 3rd party FunC grammar to SUPPORTED_LANGUAGES [Nikita Sobolev][]</li>
<li>Added 3rd party Flix grammar to SUPPORTED_LANGUAGES <a href="https://github.com/flix">The Flix Organisation</a></li>
<li>Added 3rd party RVT grammar to SUPPORTED_LANGUAGES <a href="https://github.com/Sopitive">Sopitive</a></li>
</ul>
<p>Grammars:</p>
<ul>
<li>enh(scheme) add <code>scm</code> alias for Scheme <a href="https://github.com/matyklug18">matyklug18</a></li>
<li>fix(typescript) patterns like <code>&lt;T =</code> are not JSX <a href="https://github.com/joshgoebel">Josh Goebel</a></li>
<li>fix(bash) recognize the <code>((</code> keyword <a href="https://github.com/uplime">Nick Chambers</a></li>
<li>enh(Ruby) misc improvements (kws, class names, etc)  <a href="https://github.com/joshgoebel">Josh Goebel</a></li>
<li>fix(js) do not flag <code>import()</code> as a function, rather a keyword <a href="https://github.com/nathnolt">nathnolt</a></li>
<li>fix(bash) recognize the <code>((</code> keyword <a href="https://github.com/uplime">Nick Chambers</a></li>
<li>fix(nix) support escaped dollar signs in strings <a href="https://github.com/h7x4">h7x4</a></li>
<li>enh(cmake) support bracket comments <a href="https://github.com/Hirse">Hirse</a></li>
<li>enh(java) add yield keyword to java <a href="https://github.com/MBoegers">MBoegers</a></li>
<li>enh(java) add permits keyword to java <a href="https://github.com/MBoegers">MBoegers</a></li>
<li>fix(javascript/typescript) correct identifier matching when using numbers <a href="https://github.com/lachieh">Lachlan Heywood</a></li>
</ul>
<p>Improvements:</p>
<ul>
<li>Documentation typo fix by <a href="https://github.com/eddymens">Eddymens</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/highlightjs/highlight.js/blob/main/CHANGES.md">highlight.js's changelog</a>.</em></p>
<blockquote>
<h2>Version 11.7.0</h2>
<p>New Grammars:</p>
<ul>
<li>added 3rd party LookML grammar to SUPPORTED_LANGUAGES <a href="https://github.com/joshtemple">Josh Temple</a></li>
<li>added 3rd party FunC grammar to SUPPORTED_LANGUAGES [Nikita Sobolev][]</li>
<li>Added 3rd party Flix grammar to SUPPORTED_LANGUAGES <a href="https://github.com/flix">The Flix Organisation</a></li>
<li>Added 3rd party RVT grammar to SUPPORTED_LANGUAGES <a href="https://github.com/Sopitive">Sopitive</a></li>
</ul>
<p>Grammars:</p>
<ul>
<li>enh(scheme) add <code>scm</code> alias for Scheme <a href="https://github.com/matyklug18">matyklug18</a></li>
<li>fix(typescript) patterns like <code>&lt;T =</code> are not JSX <a href="https://github.com/joshgoebel">Josh Goebel</a></li>
<li>fix(bash) recognize the <code>((</code> keyword <a href="https://github.com/uplime">Nick Chambers</a></li>
<li>enh(Ruby) misc improvements (kws, class names, etc)  <a href="https://github.com/joshgoebel">Josh Goebel</a></li>
<li>fix(js) do not flag <code>import()</code> as a function, rather a keyword <a href="https://github.com/nathnolt">nathnolt</a></li>
<li>fix(bash) recognize the <code>((</code> keyword <a href="https://github.com/uplime">Nick Chambers</a></li>
<li>fix(nix) support escaped dollar signs in strings <a href="https://github.com/h7x4">h7x4</a></li>
<li>enh(cmake) support bracket comments <a href="https://github.com/Hirse">Hirse</a></li>
<li>enh(java) add yield keyword to java <a href="https://github.com/MBoegers">MBoegers</a></li>
<li>enh(java) add permits keyword to java <a href="https://github.com/MBoegers">MBoegers</a></li>
<li>fix(javascript/typescript) correct identifier matching when using numbers <a href="https://github.com/lachieh">Lachlan Heywood</a></li>
</ul>
<p>Improvements:</p>
<ul>
<li>Documentation typo fix by <a href="https://github.com/eddymens">Eddymens</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>82688fa</code></a> (release) bump 11.7.0</li>
<li><a href=""><code>e57bf13</code></a> (docs) add RVT Script to SUPPORTED_LANGUAGES (<a href="https://github-redirect.dependabot.com/highlightjs/highlight.js/issues/3666">#3666</a>)</li>
<li><a href=""><code>526d339</code></a> (docs) fixed typo  (<a href="https://github-redirect.dependabot.com/highlightjs/highlight.js/issues/3660">#3660</a>)</li>
<li><a href=""><code>3997c9b</code></a> (end) Added <code>scm</code> alias to scheme (<a href="https://github-redirect.dependabot.com/highlightjs/highlight.js/issues/3654">#3654</a>)</li>
<li><a href=""><code>4f5b769</code></a> fix(js/ts) prevent <code>$[number]</code> variables as false positives as numeric (<a href="https://github-redirect.dependabot.com/highlightjs/highlight.js/issues/3648">#3648</a>)</li>
<li><a href=""><code>e0f7577</code></a> Add Flix to SUPPORTED_LANGUAGES.md (<a href="https://github-redirect.dependabot.com/highlightjs/highlight.js/issues/3637">#3637</a>)</li>
<li><a href=""><code>14b550d</code></a> (docs) Add tsx alias (<a href="https://github-redirect.dependabot.com/highlightjs/highlight.js/issues/3651">#3651</a>)</li>
<li><a href=""><code>bc88ed5</code></a> (java) add Java 14 switch expression keyword <code>yield</code> (<a href="https://github-redirect.dependabot.com/highlightjs/highlight.js/issues/3650">#3650</a>)</li>
<li><a href=""><code>f035aab</code></a> (java) add <code>permits</code> keyword (<a href="https://github-redirect.dependabot.com/highlightjs/highlight.js/issues/3649">#3649</a>)</li>
<li><a href=""><code>abcb53d</code></a> enh(cmake) support bracket comments (<a href="https://github-redirect.dependabot.com/highlightjs/highlight.js/issues/3644">#3644</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/highlightjs/highlight.js/compare/11.6.0...11.7.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=highlight.js&package-manager=npm_and_yarn&previous-version=11.6.0&new-version=11.7.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f3666cbabe9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
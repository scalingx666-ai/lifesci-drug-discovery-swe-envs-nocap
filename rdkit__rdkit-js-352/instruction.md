# Issue

**Title:** Bump highlight.js from 11.7.0 to 11.8.0

## Description

Bumps [highlight.js](https://github.com/highlightjs/highlight.js) from 11.7.0 to 11.8.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/highlightjs/highlight.js/releases">highlight.js's releases</a>.</em></p>
<blockquote>
<h2>11.8.0 &quot;Spring has arrived&quot; Edition</h2>
<h2>Changelog</h2>
<p>Parser engine:</p>
<ul>
<li>added a function to default export to generate a fresh highlighter instance to be used by extensions <a href="https://github.com/wisammechano">WisamMechano</a></li>
<li>added BETA <code>__emitTokens</code> key to grammars to allow then to direct their own parsing, only using Highlight.js for the HTML rendering <a href="https://github.com/joshgoebel">Josh Goebel</a></li>
<li>(enh) add <code>removePlugin</code> api <a href="https://github.com/faga295">faga295</a></li>
<li>(fix) typo in language name of <code>JavaScript</code> <a href="https://github.com/CyrusKao">Cyrus Kao</a></li>
</ul>
<p>New Grammars:</p>
<ul>
<li>added 3rd party Lang grammar to SUPPORTED_LANGUAGES <a href="https://github.com/AdamRaichu">AdamRaichu</a></li>
<li>added 3rd party C3 grammar to SUPPORTED_LANGUAGES <a href="https://github.com/aliaegik">aliaegik</a></li>
</ul>
<p>Core Grammars:</p>
<ul>
<li>enh(sql) support <code>_</code> in variable names [joshgoebel][]</li>
<li>enh(mathematica) update keywords list to 13.2.1 <a href="https://github.com/arnoudbuzing">arnoudbuzing</a></li>
<li>enh(protobuf) add <code>proto</code> alias for Protobuf [dimitropoulos][]</li>
<li>enh(sqf)  latest changes in Arma 3 v2.11 <a href="https://github.com/Leopard20/">Leopard20</a></li>
<li>enh(js/ts) Added support for GraphQL tagged template strings <a href="https://github.com/ali">Ali Ukani</a></li>
<li>enh(javascript) add sessionStorage to list of built-in variables <a href="https://github.com/morinel">Jeroen van Vianen</a></li>
<li>enh(http) Add supporxt for HTTP/3 <a href="https://github.com/rijenkii">Rijenkii</a></li>
<li>added 3rd party Motoko grammar to SUPPORTED_LANGUAGES <a href="https://github.com/rvanasa">rvanasa</a></li>
<li>added 3rd party Candid grammar to SUPPORTED_LANGUAGES <a href="https://github.com/rvanasa">rvanasa</a></li>
<li>fix(haskell) Added support for characters <a href="https://github.com/CrystalSplitter">CrystalSplitter</a></li>
<li>enh(dart) Add <code>base</code>, <code>interface</code>, <code>sealed</code>, and <code>when</code> keywords <a href="https://github.com/srawlins">Sam Rawlins</a></li>
<li>enh(php) detect newer more flexible NOWdoc syntax (<a href="">#3679</a>) <a href="https://github.com/doiftrue">Timur Kamaev</a></li>
<li>enh(python) improve autodetection of code with type hinting any function's return type (making the <code>-&gt;</code> operator legal) <a href="https://github.com/Keyacom">Keyacom</a></li>
<li>enh(bash) add <code>select</code> and <code>until</code> as keywords</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/highlightjs/highlight.js/blob/main/CHANGES.md">highlight.js's changelog</a>.</em></p>
<blockquote>
<h2>Version 11.8.0</h2>
<p>Parser engine:</p>
<ul>
<li>added a function to default export to generate a fresh highlighter instance to be used by extensions <a href="https://github.com/wisammechano">WisamMechano</a></li>
<li>added BETA <code>__emitTokens</code> key to grammars to allow then to direct their own parsing, only using Highlight.js for the HTML rendering <a href="https://github.com/joshgoebel">Josh Goebel</a></li>
<li>(enh) add <code>removePlugin</code> api <a href="https://github.com/faga295">faga295</a></li>
<li>(fix) typo in language name of <code>JavaScript</code> <a href="https://github.com/CyrusKao">Cyrus Kao</a></li>
</ul>
<p>New Grammars:</p>
<ul>
<li>added 3rd party Lang grammar to SUPPORTED_LANGUAGES <a href="https://github.com/AdamRaichu">AdamRaichu</a></li>
<li>added 3rd party C3 grammar to SUPPORTED_LANGUAGES <a href="https://github.com/aliaegik">aliaegik</a></li>
</ul>
<p>Core Grammars:</p>
<ul>
<li>enh(sql) support <code>_</code> in variable names [joshgoebel][]</li>
<li>enh(mathematica) update keywords list to 13.2.1 <a href="https://github.com/arnoudbuzing">arnoudbuzing</a></li>
<li>enh(protobuf) add <code>proto</code> alias for Protobuf [dimitropoulos][]</li>
<li>enh(sqf)  latest changes in Arma 3 v2.11 <a href="https://github.com/Leopard20/">Leopard20</a></li>
<li>enh(js/ts) Added support for GraphQL tagged template strings <a href="https://github.com/ali">Ali Ukani</a></li>
<li>enh(javascript) add sessionStorage to list of built-in variables <a href="https://github.com/morinel">Jeroen van Vianen</a></li>
<li>enh(http) Add support for HTTP/3 <a href="https://github.com/rijenkii">Rijenkii</a></li>
<li>added 3rd party Motoko grammar to SUPPORTED_LANGUAGES <a href="https://github.com/rvanasa">rvanasa</a></li>
<li>added 3rd party Candid grammar to SUPPORTED_LANGUAGES <a href="https://github.com/rvanasa">rvanasa</a></li>
<li>fix(haskell) Added support for characters <a href="https://github.com/CrystalSplitter">CrystalSplitter</a></li>
<li>enh(dart) Add <code>base</code>, <code>interface</code>, <code>sealed</code>, and <code>when</code> keywords <a href="https://github.com/srawlins">Sam Rawlins</a></li>
<li>enh(php) detect newer more flexible NOWdoc syntax (<a href="">#3679</a>) <a href="https://github.com/doiftrue">Timur Kamaev</a></li>
<li>enh(python) improve autodetection of code with type hinting any function's return type (making the <code>-&gt;</code> operator legal) <a href="https://github.com/Keyacom">Keyacom</a></li>
<li>enh(bash) add <code>select</code> and <code>until</code> as keywords</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>65687a9</code></a> (release) 11.8.0</li>
<li><a href=""><code>381c492</code></a> (chore) update deps</li>
<li><a href=""><code>4e480d6</code></a> (chore) clean up changelog for release</li>
<li><a href=""><code>2fa5786</code></a> enh(sql) support <code>_</code> in variable names</li>
<li><a href=""><code>1bb4afe</code></a> Bump JS-DevTools/npm-publish from 1 to 2 (<a href="">#3763</a>)</li>
<li><a href=""><code>ec66e02</code></a> Add Mint Programming Language to <code>SUPPORTED_LANGUAGES.md</code> (<a href="">#3759</a>)</li>
<li><a href=""><code>a8bcfce</code></a> (docs) add SFZ to SUPPORTED_LANGUAGES.md (<a href="">#3760</a>)</li>
<li><a href=""><code>4f9cd3b</code></a> fix typo in language name of JavaScript (<a href="">#3758</a>)</li>
<li><a href=""><code>fc2a3e1</code></a> enh(bash) add &quot;until&quot; and &quot;select&quot; as keywords (<a href="">#3756</a>)</li>
<li><a href=""><code>48b5ced</code></a> enh(mathematica) update keywords list to 13.2.1  (<a href="">#3750</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/highlightjs/highlight.js/compare/11.7.0...11.8.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=highlight.js&package-manager=npm_and_yarn&previous-version=11.7.0&new-version=11.8.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ecfa8dfd081`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
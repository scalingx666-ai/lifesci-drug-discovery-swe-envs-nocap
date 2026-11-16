# Issue

**Title:** Bump eslint from 8.29.0 to 8.34.0

## Description

Bumps [eslint](https://github.com/eslint/eslint) from 8.29.0 to 8.34.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/eslint/eslint/releases">eslint's releases</a>.</em></p>
<blockquote>
<h2>v8.34.0</h2>
<h2>Features</h2>
<ul>
<li><a href=""><code>9b2fcf7</code></a> feat: <code>array-callback-return</code> supports <code>Array.prototype.toSorted</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16845">#16845</a>) (SUZUKI Sosuke)</li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li><a href=""><code>923f61d</code></a> fix: false positive with assignment in <code>no-extra-parens</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16872">#16872</a>) (Francesco Trotta)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li><a href=""><code>f0a9883</code></a> docs: split rules documentation (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16797">#16797</a>) (Ben Perlmutter)</li>
<li><a href=""><code>67aa37b</code></a> docs: fix typo in command-line-interface.md (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16871">#16871</a>) (Kevin Rouchut)</li>
<li><a href=""><code>337f7ed</code></a> docs: fix width of language input (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16849">#16849</a>) (Tanuj Kanti)</li>
<li><a href=""><code>71349a1</code></a> docs: Configure a Parser page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16803">#16803</a>) (Ben Perlmutter)</li>
<li><a href=""><code>de7e925</code></a> docs: remove extra line numbers in example (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16848">#16848</a>) (jonz94)</li>
<li><a href=""><code>ad38d77</code></a> docs: Update README (GitHub Actions Bot)</li>
</ul>
<h2>Chores</h2>
<ul>
<li><a href=""><code>9dbe06d</code></a> chore: add <code>type</code> property to array-element-newline schema (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16877">#16877</a>) (MHO)</li>
<li><a href=""><code>a061527</code></a> chore: Remove unused functions (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16868">#16868</a>) (Nicholas C. Zakas)</li>
</ul>
<h2>v8.33.0</h2>
<h2>Features</h2>
<ul>
<li><a href=""><code>2cc7954</code></a> feat: add <code>restrictDefaultExports</code> option to no-restricted-exports rule (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16785">#16785</a>) (Nitin Kumar)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li><a href=""><code>17f4be2</code></a> docs: Fix examples in no-multiple-empty-lines rule (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16835">#16835</a>) (jonz94)</li>
<li><a href=""><code>9c7cfe3</code></a> docs: 'Source Code' content in 'Set up Development Environment' page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16780">#16780</a>) (Ben Perlmutter)</li>
<li><a href=""><code>ede5c64</code></a> docs: Custom processors page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16802">#16802</a>) (Ben Perlmutter)</li>
<li><a href=""><code>2620614</code></a> docs: Code of Conduct page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16781">#16781</a>) (Ben Perlmutter)</li>
<li><a href=""><code>50a8efd</code></a> docs: report a sec vulnerability page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16808">#16808</a>) (Ben Perlmutter)</li>
<li><a href=""><code>ed60afd</code></a> docs: Update page titles, section landing pages, and side TOC (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16760">#16760</a>) (Ben Perlmutter)</li>
<li><a href=""><code>333c712</code></a> docs: add background to code-path-diagrams for dark-mode (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16822">#16822</a>) (Tanuj Kanti)</li>
<li><a href=""><code>f5f7b9b</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>2aa4f5f</code></a> docs: no-constant-condition: Add multi-comparison example (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16776">#16776</a>) (Sebastian Simon)</li>
<li><a href=""><code>40287db</code></a> docs: Remove Google Group icon (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16779">#16779</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>ea10ca5</code></a> docs: 'a .eslint' -&gt; 'an .eslint' for consistency (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16809">#16809</a>) (Ben Perlmutter)</li>
<li><a href=""><code>3be0748</code></a> docs: add example for nodejs lintText api (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16789">#16789</a>) (Siva K)</li>
<li><a href=""><code>ce4f5ff</code></a> docs: Replace removed related rules with a valid rule (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16800">#16800</a>) (Ville Saalo)</li>
</ul>
<h2>v8.32.0</h2>
<h2>Features</h2>
<ul>
<li><a href=""><code>fc20f24</code></a> feat: add suggestions for redundant wrapping in prefer-regex-literals (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16658">#16658</a>) (YeonJuan)</li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li><a href=""><code>b4f8329</code></a> fix: ignore directives for no-fallthrough (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16757">#16757</a>) (gfyoung)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li><a href=""><code>17b65ad</code></a> docs: IA Update page URL move (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16665">#16665</a>) (Ben Perlmutter)</li>
<li><a href=""><code>5981296</code></a> docs: fix theme switcher button (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16752">#16752</a>) (Sam Chen)</li>
<li><a href=""><code>6669413</code></a> docs: deploy prerelease docs under the <code>/docs/next/</code> path (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16541">#16541</a>) (Nitin Kumar)</li>
<li><a href=""><code>78ecfe0</code></a> docs: use inline code for rule options name (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16768">#16768</a>) (Percy Ma)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/eslint/eslint/blob/main/CHANGELOG.md">eslint's changelog</a>.</em></p>
<blockquote>
<p>v8.34.0 - February 10, 2023</p>
<ul>
<li><a href=""><code>f0a9883</code></a> docs: split rules documentation (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16797">#16797</a>) (Ben Perlmutter)</li>
<li><a href=""><code>923f61d</code></a> fix: false positive with assignment in <code>no-extra-parens</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16872">#16872</a>) (Francesco Trotta)</li>
<li><a href=""><code>9dbe06d</code></a> chore: add <code>type</code> property to array-element-newline schema (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16877">#16877</a>) (MHO)</li>
<li><a href=""><code>a061527</code></a> chore: Remove unused functions (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16868">#16868</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>67aa37b</code></a> docs: fix typo in command-line-interface.md (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16871">#16871</a>) (Kevin Rouchut)</li>
<li><a href=""><code>337f7ed</code></a> docs: fix width of language input (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16849">#16849</a>) (Tanuj Kanti)</li>
<li><a href=""><code>9b2fcf7</code></a> feat: <code>array-callback-return</code> supports <code>Array.prototype.toSorted</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16845">#16845</a>) (SUZUKI Sosuke)</li>
<li><a href=""><code>71349a1</code></a> docs: Configure a Parser page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16803">#16803</a>) (Ben Perlmutter)</li>
<li><a href=""><code>de7e925</code></a> docs: remove extra line numbers in example (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16848">#16848</a>) (jonz94)</li>
<li><a href=""><code>ad38d77</code></a> docs: Update README (GitHub Actions Bot)</li>
</ul>
<p>v8.33.0 - January 28, 2023</p>
<ul>
<li><a href=""><code>17f4be2</code></a> docs: Fix examples in no-multiple-empty-lines rule (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16835">#16835</a>) (jonz94)</li>
<li><a href=""><code>9c7cfe3</code></a> docs: 'Source Code' content in 'Set up Development Environment' page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16780">#16780</a>) (Ben Perlmutter)</li>
<li><a href=""><code>ede5c64</code></a> docs: Custom processors page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16802">#16802</a>) (Ben Perlmutter)</li>
<li><a href=""><code>2620614</code></a> docs: Code of Conduct page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16781">#16781</a>) (Ben Perlmutter)</li>
<li><a href=""><code>50a8efd</code></a> docs: report a sec vulnerability page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16808">#16808</a>) (Ben Perlmutter)</li>
<li><a href=""><code>2cc7954</code></a> feat: add <code>restrictDefaultExports</code> option to no-restricted-exports rule (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16785">#16785</a>) (Nitin Kumar)</li>
<li><a href=""><code>ed60afd</code></a> docs: Update page titles, section landing pages, and side TOC (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16760">#16760</a>) (Ben Perlmutter)</li>
<li><a href=""><code>333c712</code></a> docs: add background to code-path-diagrams for dark-mode (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16822">#16822</a>) (Tanuj Kanti)</li>
<li><a href=""><code>f5f7b9b</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>2aa4f5f</code></a> docs: no-constant-condition: Add multi-comparison example (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16776">#16776</a>) (Sebastian Simon)</li>
<li><a href=""><code>40287db</code></a> docs: Remove Google Group icon (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16779">#16779</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>ea10ca5</code></a> docs: 'a .eslint' -&gt; 'an .eslint' for consistency (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16809">#16809</a>) (Ben Perlmutter)</li>
<li><a href=""><code>3be0748</code></a> docs: add example for nodejs lintText api (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16789">#16789</a>) (Siva K)</li>
<li><a href=""><code>ce4f5ff</code></a> docs: Replace removed related rules with a valid rule (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16800">#16800</a>) (Ville Saalo)</li>
</ul>
<p>v8.32.0 - January 14, 2023</p>
<ul>
<li><a href=""><code>17b65ad</code></a> docs: IA Update page URL move (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16665">#16665</a>) (Ben Perlmutter)</li>
<li><a href=""><code>b4f8329</code></a> fix: ignore directives for no-fallthrough (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16757">#16757</a>) (gfyoung)</li>
<li><a href=""><code>5981296</code></a> docs: fix theme switcher button (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16752">#16752</a>) (Sam Chen)</li>
<li><a href=""><code>6669413</code></a> docs: deploy prerelease docs under the <code>/docs/next/</code> path (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16541">#16541</a>) (Nitin Kumar)</li>
<li><a href=""><code>2952d6e</code></a> chore: sync templates/*.md files with issue templates (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16758">#16758</a>) (gfyoung)</li>
<li><a href=""><code>78ecfe0</code></a> docs: use inline code for rule options name (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16768">#16768</a>) (Percy Ma)</li>
<li><a href=""><code>3e34418</code></a> chore: Add new issues to triage project (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16740">#16740</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>fc2ea59</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>fc20f24</code></a> feat: add suggestions for redundant wrapping in prefer-regex-literals (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16658">#16658</a>) (YeonJuan)</li>
<li><a href=""><code>762a872</code></a> docs: Update README (GitHub Actions Bot)</li>
</ul>
<p>v8.31.0 - December 31, 2022</p>
<ul>
<li><a href=""><code>65d4e24</code></a> chore: Upgrade <code>@​eslint/eslintrc</code><a href="https://github.com/1"><code>@​1</code></a>.4.1 (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16729">#16729</a>) (Brandon Mills)</li>
<li><a href=""><code>35439f1</code></a> fix: correct syntax error in <code>prefer-arrow-callback</code> autofix (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16722">#16722</a>) (Francesco Trotta)</li>
<li><a href=""><code>87b2470</code></a> fix: new instance of FlatESLint should load latest config file version (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16608">#16608</a>) (Milos Djermanovic)</li>
<li><a href=""><code>8d93081</code></a> chore: fix CI failure (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16721">#16721</a>) (Sam Chen)</li>
<li><a href=""><code>4339dc4</code></a> docs: Update README (GitHub Actions Bot)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5c2a198</code></a> 8.34.0</li>
<li><a href=""><code>18212bb</code></a> Build: changelog update for 8.34.0</li>
<li><a href=""><code>f0a9883</code></a> docs: split rules documentation (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16797">#16797</a>)</li>
<li><a href=""><code>923f61d</code></a> fix: false positive with assignment in <code>no-extra-parens</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16872">#16872</a>)</li>
<li><a href=""><code>9dbe06d</code></a> chore: add <code>type</code> property to array-element-newline schema (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16877">#16877</a>)</li>
<li><a href=""><code>a061527</code></a> chore: Remove unused functions (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16868">#16868</a>)</li>
<li><a href=""><code>67aa37b</code></a> docs: fix typo in command-line-interface.md (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16871">#16871</a>)</li>
<li><a href=""><code>337f7ed</code></a> docs: fix width of language input (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16849">#16849</a>)</li>
<li><a href=""><code>9b2fcf7</code></a> feat: <code>array-callback-return</code> supports <code>Array.prototype.toSorted</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16845">#16845</a>)</li>
<li><a href=""><code>71349a1</code></a> docs: Configure a Parser page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16803">#16803</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/eslint/eslint/compare/v8.29.0...v8.34.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=eslint&package-manager=npm_and_yarn&previous-version=8.29.0&new-version=8.34.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
# Issue

**Title:** Bump eslint from 8.37.0 to 8.39.0

## Description

Bumps [eslint](https://github.com/eslint/eslint) from 8.37.0 to 8.39.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/eslint/eslint/releases">eslint's releases</a>.</em></p>
<blockquote>
<h2>v8.39.0</h2>
<h2>Features</h2>
<ul>
<li><a href=""><code>3f7af9f</code></a> feat: Implement <code>SourceCode#markVariableAsUsed()</code> (<a href="">#17086</a>) (Nicholas C. Zakas)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li><a href=""><code>6987dc5</code></a> docs: Fix formatting in Custom Rules docs (<a href="">#17097</a>) (Milos Djermanovic)</li>
<li><a href=""><code>4ee92e5</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>d8e9887</code></a> docs: Custom Rules cleanup/expansion (<a href="">#16906</a>) (Ben Perlmutter)</li>
<li><a href=""><code>1fea279</code></a> docs: Clarify how to add to tsc agenda (<a href="">#17084</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>970ef1c</code></a> docs: Update triage board location (Nicholas C. Zakas)</li>
<li><a href=""><code>6d8bffd</code></a> docs: Update README (GitHub Actions Bot)</li>
</ul>
<h2>Chores</h2>
<ul>
<li><a href=""><code>60a6f26</code></a> chore: upgrade <code>@​eslint/js</code><a href="https://github.com/8"><code>@​8</code></a>.39.0 (<a href="">#17102</a>) (Milos Djermanovic)</li>
<li><a href=""><code>d5ba5c0</code></a> chore: package.json update for <code>@​eslint/js</code> release (ESLint Jenkins)</li>
<li><a href=""><code>f57eff2</code></a> ci: run tests on Node.js v20 (<a href="">#17093</a>) (Nitin Kumar)</li>
<li><a href=""><code>9d1b8fc</code></a> perf: Binary search in token store <code>utils.search</code> (<a href="">#17066</a>) (Francesco Trotta)</li>
<li><a href=""><code>07a4435</code></a> chore: Add request for minimal repro to bug report (<a href="">#17081</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>eac4943</code></a> refactor: remove unnecessary use of <code>SourceCode#getAncestors</code> in rules (<a href="">#17075</a>) (Milos Djermanovic)</li>
<li><a href=""><code>0a7b60a</code></a> chore: update description of <code>SourceCode#getDeclaredVariables</code> (<a href="">#17072</a>) (Milos Djermanovic)</li>
<li><a href=""><code>6e2df71</code></a> chore: remove unnecessary references to the LICENSE file (<a href="">#17071</a>) (Milos Djermanovic)</li>
</ul>
<h2>v8.38.0</h2>
<h2>Features</h2>
<ul>
<li><a href=""><code>a1d561d</code></a> feat: Move getDeclaredVariables and getAncestors to SourceCode (<a href="">#17059</a>) (Nicholas C. Zakas)</li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li><a href=""><code>1c1ece2</code></a> fix: do not report on <code>RegExp(...args)</code> in <code>require-unicode-regexp</code> (<a href="">#17037</a>) (Francesco Trotta)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li><a href=""><code>7162d34</code></a> docs: Mention new config system is complete (<a href="">#17068</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>0fd6bb2</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>c83531c</code></a> docs: Update/remove external links, eg. point to <code>eslint-community</code> (<a href="">#17061</a>) (Pelle Wessman)</li>
<li><a href=""><code>a3aa6f5</code></a> docs: Clarify <code>no-div-regex</code> rule docs (<a href="">#17051</a>) (Francesco Trotta)</li>
<li><a href=""><code>b0f11cf</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>da8d52a</code></a> docs: Update the second object instance for the &quot;no-new&quot; rule (<a href="">#17020</a>) (Ahmadou Waly NDIAYE)</li>
<li><a href=""><code>518130a</code></a> docs: switch language based on current path (<a href="">#16687</a>) (Percy Ma)</li>
<li><a href=""><code>24206c4</code></a> docs: Update README (GitHub Actions Bot)</li>
</ul>
<h2>Chores</h2>
<ul>
<li><a href=""><code>59ed060</code></a> chore: upgrade <code>@​eslint/js</code><a href="https://github.com/8"><code>@​8</code></a>.38.0 (<a href="">#17069</a>) (Milos Djermanovic)</li>
<li><a href=""><code>88c0898</code></a> chore: package.json update for <code>@​eslint/js</code> release (ESLint Jenkins)</li>
<li><a href=""><code>cf682d2</code></a> refactor: simplify new-parens rule schema (<a href="">#17060</a>) (MHO)</li>
<li><a href=""><code>0dde022</code></a> ci: bump actions/add-to-project from 0.4.1 to 0.5.0 (<a href="">#17055</a>) (dependabot[bot])</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/eslint/eslint/blob/main/CHANGELOG.md">eslint's changelog</a>.</em></p>
<blockquote>
<p>v8.39.0 - April 21, 2023</p>
<ul>
<li><a href=""><code>60a6f26</code></a> chore: upgrade <code>@​eslint/js</code><a href="https://github.com/8"><code>@​8</code></a>.39.0 (<a href="">#17102</a>) (Milos Djermanovic)</li>
<li><a href=""><code>d5ba5c0</code></a> chore: package.json update for <code>@​eslint/js</code> release (ESLint Jenkins)</li>
<li><a href=""><code>6987dc5</code></a> docs: Fix formatting in Custom Rules docs (<a href="">#17097</a>) (Milos Djermanovic)</li>
<li><a href=""><code>4ee92e5</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>3f7af9f</code></a> feat: Implement <code>SourceCode#markVariableAsUsed()</code> (<a href="">#17086</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>d8e9887</code></a> docs: Custom Rules cleanup/expansion (<a href="">#16906</a>) (Ben Perlmutter)</li>
<li><a href=""><code>f57eff2</code></a> ci: run tests on Node.js v20 (<a href="">#17093</a>) (Nitin Kumar)</li>
<li><a href=""><code>1fea279</code></a> docs: Clarify how to add to tsc agenda (<a href="">#17084</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>970ef1c</code></a> docs: Update triage board location (Nicholas C. Zakas)</li>
<li><a href=""><code>9d1b8fc</code></a> perf: Binary search in token store <code>utils.search</code> (<a href="">#17066</a>) (Francesco Trotta)</li>
<li><a href=""><code>07a4435</code></a> chore: Add request for minimal repro to bug report (<a href="">#17081</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>eac4943</code></a> refactor: remove unnecessary use of <code>SourceCode#getAncestors</code> in rules (<a href="">#17075</a>) (Milos Djermanovic)</li>
<li><a href=""><code>6d8bffd</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>0a7b60a</code></a> chore: update description of <code>SourceCode#getDeclaredVariables</code> (<a href="">#17072</a>) (Milos Djermanovic)</li>
<li><a href=""><code>6e2df71</code></a> chore: remove unnecessary references to the LICENSE file (<a href="">#17071</a>) (Milos Djermanovic)</li>
</ul>
<p>v8.38.0 - April 7, 2023</p>
<ul>
<li><a href=""><code>59ed060</code></a> chore: upgrade <code>@​eslint/js</code><a href="https://github.com/8"><code>@​8</code></a>.38.0 (<a href="">#17069</a>) (Milos Djermanovic)</li>
<li><a href=""><code>88c0898</code></a> chore: package.json update for <code>@​eslint/js</code> release (ESLint Jenkins)</li>
<li><a href=""><code>7162d34</code></a> docs: Mention new config system is complete (<a href="">#17068</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>a1d561d</code></a> feat: Move getDeclaredVariables and getAncestors to SourceCode (<a href="">#17059</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>0fd6bb2</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>c83531c</code></a> docs: Update/remove external links, eg. point to <code>eslint-community</code> (<a href="">#17061</a>) (Pelle Wessman)</li>
<li><a href=""><code>cf682d2</code></a> refactor: simplify new-parens rule schema (<a href="">#17060</a>) (MHO)</li>
<li><a href=""><code>a3aa6f5</code></a> docs: Clarify <code>no-div-regex</code> rule docs (<a href="">#17051</a>) (Francesco Trotta)</li>
<li><a href=""><code>0dde022</code></a> ci: bump actions/add-to-project from 0.4.1 to 0.5.0 (<a href="">#17055</a>) (dependabot[bot])</li>
<li><a href=""><code>b0f11cf</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>da8d52a</code></a> docs: Update the second object instance for the &quot;no-new&quot; rule (<a href="">#17020</a>) (Ahmadou Waly NDIAYE)</li>
<li><a href=""><code>518130a</code></a> docs: switch language based on current path (<a href="">#16687</a>) (Percy Ma)</li>
<li><a href=""><code>24206c4</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>1c1ece2</code></a> fix: do not report on <code>RegExp(...args)</code> in <code>require-unicode-regexp</code> (<a href="">#17037</a>) (Francesco Trotta)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>560e812</code></a> 8.39.0</li>
<li><a href=""><code>94ff9eb</code></a> Build: changelog update for 8.39.0</li>
<li><a href=""><code>60a6f26</code></a> chore: upgrade <code>@​eslint/js</code><a href="https://github.com/8"><code>@​8</code></a>.39.0 (<a href="">#17102</a>)</li>
<li><a href=""><code>d5ba5c0</code></a> chore: package.json update for <code>@​eslint/js</code> release</li>
<li><a href=""><code>6987dc5</code></a> docs: Fix formatting in Custom Rules docs (<a href="">#17097</a>)</li>
<li><a href=""><code>4ee92e5</code></a> docs: Update README</li>
<li><a href=""><code>3f7af9f</code></a> feat: Implement <code>SourceCode#markVariableAsUsed()</code> (<a href="">#17086</a>)</li>
<li><a href=""><code>d8e9887</code></a> docs: Custom Rules cleanup/expansion (<a href="">#16906</a>)</li>
<li><a href=""><code>f57eff2</code></a> ci: run tests on Node.js v20 (<a href="">#17093</a>)</li>
<li><a href=""><code>1fea279</code></a> docs: Clarify how to add to tsc agenda (<a href="">#17084</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/eslint/eslint/compare/v8.37.0...v8.39.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=eslint&package-manager=npm_and_yarn&previous-version=8.37.0&new-version=8.39.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b824d173756`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
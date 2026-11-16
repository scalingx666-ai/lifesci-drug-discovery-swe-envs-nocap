# Issue

**Title:** Bump eslint from 8.35.0 to 8.37.0

## Description

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

Bumps [eslint](https://github.com/eslint/eslint) from 8.35.0 to 8.37.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/eslint/eslint/releases">eslint's releases</a>.</em></p>
<blockquote>
<h2>v8.37.0</h2>
<h2>Features</h2>
<ul>
<li><a href=""><code>b6ab8b2</code></a> feat: <code>require-unicode-regexp</code> add suggestions (<a href="">#17007</a>) (Josh Goldberg)</li>
<li><a href=""><code>10022b1</code></a> feat: Copy getScope() to SourceCode (<a href="">#17004</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>1665c02</code></a> feat: Use plugin metadata for flat config serialization (<a href="">#16992</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>b3634f6</code></a> feat: docs license (<a href="">#17010</a>) (Samuel Roldan)</li>
<li><a href=""><code>892e6e5</code></a> feat: languageOptions.parser must be an object. (<a href="">#16985</a>) (Nicholas C. Zakas)</li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li><a href=""><code>619f3fd</code></a> fix: correctly handle <code>null</code> default config in <code>RuleTester</code> (<a href="">#17023</a>) (Brad Zacher)</li>
<li><a href=""><code>1fbf118</code></a> fix: <code>getFirstToken</code>/<code>getLastToken</code> on comment-only node (<a href="">#16889</a>) (Francesco Trotta)</li>
<li><a href=""><code>129e252</code></a> fix: Fix typo in <code>logical-assignment-operators</code> rule description (<a href="">#17000</a>) (Francesco Trotta)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li><a href=""><code>75339df</code></a> docs: fix typos and missing info in id-match docs (<a href="">#17029</a>) (Ed Lucas)</li>
<li><a href=""><code>ec2d830</code></a> docs: Fix typos in the <code>semi</code> rule docs (<a href="">#17012</a>) (Andrii Lundiak)</li>
<li><a href=""><code>e39f28d</code></a> docs: add back to top button (<a href="">#16979</a>) (Tanuj Kanti)</li>
<li><a href=""><code>721c717</code></a> docs: Custom Processors cleanup and expansion (<a href="">#16838</a>) (Ben Perlmutter)</li>
<li><a href=""><code>d049f97</code></a> docs: 'How ESLint is Maintained' page (<a href="">#16961</a>) (Ben Perlmutter)</li>
<li><a href=""><code>5251a92</code></a> docs: Describe guard options for guard-for-in (<a href="">#16986</a>) (alope107)</li>
<li><a href=""><code>6157d81</code></a> docs: Add example to guard-for-in docs. (<a href="">#16983</a>) (alope107)</li>
<li><a href=""><code>fd47998</code></a> docs: update <code>Array.prototype.toSorted</code> specification link (<a href="">#16982</a>) (Milos Djermanovic)</li>
<li><a href=""><code>3e1cf6b</code></a> docs: Copy edits on Maintain ESLint docs (<a href="">#16939</a>) (Ben Perlmutter)</li>
</ul>
<h2>Chores</h2>
<ul>
<li><a href=""><code>c67f299</code></a> chore: upgrade <code>@​eslint/js</code><a href="https://github.com/8"><code>@​8</code></a>.37.0 (<a href="">#17033</a>) (Milos Djermanovic)</li>
<li><a href=""><code>ee9ddbd</code></a> chore: package.json update for <code>@​eslint/js</code> release (ESLint Jenkins)</li>
<li><a href=""><code>dddb475</code></a> chore: upgrade <code>@​eslint/eslintrc</code><a href="https://github.com/2"><code>@​2</code></a>.0.2 (<a href="">#17032</a>) (Milos Djermanovic)</li>
<li><a href=""><code>522431e</code></a> chore: upgrade espree@9.5.1 (<a href="">#17031</a>) (Milos Djermanovic)</li>
<li><a href=""><code>f5f9a88</code></a> chore: upgrade eslint-visitor-keys@3.4.0 (<a href="">#17030</a>) (Milos Djermanovic)</li>
<li><a href=""><code>4dd8d52</code></a> ci: bump actions/stale from 7 to 8 (<a href="">#17026</a>) (dependabot[bot])</li>
<li><a href=""><code>ad9dd6a</code></a> chore: remove duplicate scss, (<a href="">#17005</a>) (Strek)</li>
<li><a href=""><code>ada6a3e</code></a> ci: unpin Node 19 (<a href="">#16993</a>) (Milos Djermanovic)</li>
<li><a href=""><code>c3da975</code></a> chore: Remove triage label from template (<a href="">#16990</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>69bc0e2</code></a> ci: pin Node 19 to 19.7.0 (<a href="">#16987</a>) (Milos Djermanovic)</li>
</ul>
<h2>v8.36.0</h2>
<h2>Features</h2>
<ul>
<li><a href=""><code>c89a485</code></a> feat: Add <code>checkJSDoc</code> option to multiline-comment-style (<a href="">#16807</a>) (Laurent Cozic)</li>
<li><a href=""><code>f5f5e11</code></a> feat: Serialize parsers/processors in flat config (<a href="">#16944</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>4799297</code></a> feat: use <a href="https://github.com/eslint-community"><code>@​eslint-community</code></a> dependencies (<a href="">#16784</a>) (Michaël De Boey)</li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li><a href=""><code>92c1943</code></a> fix: correctly iterate files matched by glob patterns (<a href="">#16831</a>) (Nitin Kumar)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li><a href=""><code>b98fdd4</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>caf08ce</code></a> docs: fix estree link in custom formatters docs (<a href="">#16967</a>) (Milos Djermanovic)</li>
<li><a href=""><code>3398431</code></a> docs: Custom Parsers cleanup/expansion (<a href="">#16887</a>) (Ben Perlmutter)</li>
<li><a href=""><code>19d3531</code></a> docs: Update README (GitHub Actions Bot)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/eslint/eslint/blob/main/CHANGELOG.md">eslint's changelog</a>.</em></p>
<blockquote>
<p>v8.37.0 - March 28, 2023</p>
<ul>
<li><a href=""><code>c67f299</code></a> chore: upgrade <code>@​eslint/js</code><a href="https://github.com/8"><code>@​8</code></a>.37.0 (<a href="">#17033</a>) (Milos Djermanovic)</li>
<li><a href=""><code>ee9ddbd</code></a> chore: package.json update for <code>@​eslint/js</code> release (ESLint Jenkins)</li>
<li><a href=""><code>dddb475</code></a> chore: upgrade <code>@​eslint/eslintrc</code><a href="https://github.com/2"><code>@​2</code></a>.0.2 (<a href="">#17032</a>) (Milos Djermanovic)</li>
<li><a href=""><code>522431e</code></a> chore: upgrade espree@9.5.1 (<a href="">#17031</a>) (Milos Djermanovic)</li>
<li><a href=""><code>f5f9a88</code></a> chore: upgrade eslint-visitor-keys@3.4.0 (<a href="">#17030</a>) (Milos Djermanovic)</li>
<li><a href=""><code>75339df</code></a> docs: fix typos and missing info in id-match docs (<a href="">#17029</a>) (Ed Lucas)</li>
<li><a href=""><code>b6ab8b2</code></a> feat: <code>require-unicode-regexp</code> add suggestions (<a href="">#17007</a>) (Josh Goldberg)</li>
<li><a href=""><code>4dd8d52</code></a> ci: bump actions/stale from 7 to 8 (<a href="">#17026</a>) (dependabot[bot])</li>
<li><a href=""><code>619f3fd</code></a> fix: correctly handle <code>null</code> default config in <code>RuleTester</code> (<a href="">#17023</a>) (Brad Zacher)</li>
<li><a href=""><code>ec2d830</code></a> docs: Fix typos in the <code>semi</code> rule docs (<a href="">#17012</a>) (Andrii Lundiak)</li>
<li><a href=""><code>e39f28d</code></a> docs: add back to top button (<a href="">#16979</a>) (Tanuj Kanti)</li>
<li><a href=""><code>ad9dd6a</code></a> chore: remove duplicate scss, (<a href="">#17005</a>) (Strek)</li>
<li><a href=""><code>10022b1</code></a> feat: Copy getScope() to SourceCode (<a href="">#17004</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>1665c02</code></a> feat: Use plugin metadata for flat config serialization (<a href="">#16992</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>b3634f6</code></a> feat: docs license (<a href="">#17010</a>) (Samuel Roldan)</li>
<li><a href=""><code>721c717</code></a> docs: Custom Processors cleanup and expansion (<a href="">#16838</a>) (Ben Perlmutter)</li>
<li><a href=""><code>1fbf118</code></a> fix: <code>getFirstToken</code>/<code>getLastToken</code> on comment-only node (<a href="">#16889</a>) (Francesco Trotta)</li>
<li><a href=""><code>129e252</code></a> fix: Fix typo in <code>logical-assignment-operators</code> rule description (<a href="">#17000</a>) (Francesco Trotta)</li>
<li><a href=""><code>892e6e5</code></a> feat: languageOptions.parser must be an object. (<a href="">#16985</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>ada6a3e</code></a> ci: unpin Node 19 (<a href="">#16993</a>) (Milos Djermanovic)</li>
<li><a href=""><code>c3da975</code></a> chore: Remove triage label from template (<a href="">#16990</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>d049f97</code></a> docs: 'How ESLint is Maintained' page (<a href="">#16961</a>) (Ben Perlmutter)</li>
<li><a href=""><code>5251a92</code></a> docs: Describe guard options for guard-for-in (<a href="">#16986</a>) (alope107)</li>
<li><a href=""><code>69bc0e2</code></a> ci: pin Node 19 to 19.7.0 (<a href="">#16987</a>) (Milos Djermanovic)</li>
<li><a href=""><code>6157d81</code></a> docs: Add example to guard-for-in docs. (<a href="">#16983</a>) (alope107)</li>
<li><a href=""><code>fd47998</code></a> docs: update <code>Array.prototype.toSorted</code> specification link (<a href="">#16982</a>) (Milos Djermanovic)</li>
<li><a href=""><code>3e1cf6b</code></a> docs: Copy edits on Maintain ESLint docs (<a href="">#16939</a>) (Ben Perlmutter)</li>
</ul>
<p>v8.36.0 - March 10, 2023</p>
<ul>
<li><a href=""><code>602b111</code></a> chore: upgrade <code>@​eslint/js</code><a href="https://github.com/8"><code>@​8</code></a>.36.0 (<a href="">#16978</a>) (Milos Djermanovic)</li>
<li><a href=""><code>43c2345</code></a> chore: package.json update for <code>@​eslint/js</code> release (ESLint Jenkins)</li>
<li><a href=""><code>00afb84</code></a> chore: upgrade <code>@​eslint/eslintrc</code><a href="https://github.com/2"><code>@​2</code></a>.0.1 (<a href="">#16977</a>) (Milos Djermanovic)</li>
<li><a href=""><code>698c5aa</code></a> chore: upgrade espree@9.5.0 (<a href="">#16976</a>) (Milos Djermanovic)</li>
<li><a href=""><code>b98fdd4</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>c89a485</code></a> feat: Add <code>checkJSDoc</code> option to multiline-comment-style (<a href="">#16807</a>) (Laurent Cozic)</li>
<li><a href=""><code>f5f5e11</code></a> feat: Serialize parsers/processors in flat config (<a href="">#16944</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>caf08ce</code></a> docs: fix estree link in custom formatters docs (<a href="">#16967</a>) (Milos Djermanovic)</li>
<li><a href=""><code>75acdd2</code></a> chore: lint more js files in docs (<a href="">#16964</a>) (Milos Djermanovic)</li>
<li><a href=""><code>3398431</code></a> docs: Custom Parsers cleanup/expansion (<a href="">#16887</a>) (Ben Perlmutter)</li>
<li><a href=""><code>19d3531</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>4799297</code></a> feat: use <a href="https://github.com/eslint-community"><code>@​eslint-community</code></a> dependencies (<a href="">#16784</a>) (Michaël De Boey)</li>
<li><a href=""><code>b09a512</code></a> docs: detect and fix broken links (<a href="">#16837</a>) (Nitin Kumar)</li>
<li><a href=""><code>92c1943</code></a> fix: correctly iterate files matched by glob patterns (<a href="">#16831</a>) (Nitin Kumar)</li>
<li><a href=""><code>89d9844</code></a> ci: bump actions/add-to-project from 0.4.0 to 0.4.1 (<a href="">#16943</a>) (dependabot[bot])</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4c46fb3</code></a> 8.37.0</li>
<li><a href=""><code>3413d34</code></a> Build: changelog update for 8.37.0</li>
<li><a href=""><code>c67f299</code></a> chore: upgrade <code>@​eslint/js</code><a href="https://github.com/8"><code>@​8</code></a>.37.0 (<a href="">#17033</a>)</li>
<li><a href=""><code>ee9ddbd</code></a> chore: package.json update for <code>@​eslint/js</code> release</li>
<li><a href=""><code>dddb475</code></a> chore: upgrade <code>@​eslint/eslintrc</code><a href="https://github.com/2"><code>@​2</code></a>.0.2 (<a href="">#17032</a>)</li>
<li><a href=""><code>522431e</code></a> chore: upgrade espree@9.5.1 (<a href="">#17031</a>)</li>
<li><a href=""><code>f5f9a88</code></a> chore: upgrade eslint-visitor-keys@3.4.0 (<a href="">#17030</a>)</li>
<li><a href=""><code>75339df</code></a> docs: fix typos and missing info in id-match docs (<a href="">#17029</a>)</li>
<li><a href=""><code>b6ab8b2</code></a> feat: <code>require-unicode-regexp</code> add suggestions (<a href="">#17007</a>)</li>
<li><a href=""><code>4dd8d52</code></a> ci: bump actions/stale from 7 to 8 (<a href="">#17026</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/eslint/eslint/compare/v8.35.0...v8.37.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=eslint&package-manager=npm_and_yarn&previous-version=8.35.0&new-version=8.37.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a96dd2843c29`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
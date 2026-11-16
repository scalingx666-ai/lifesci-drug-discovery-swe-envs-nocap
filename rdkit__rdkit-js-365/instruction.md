# Issue

**Title:** Bump eslint from 8.39.0 to 8.46.0

## Description

Bumps [eslint](https://github.com/eslint/eslint) from 8.39.0 to 8.46.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/eslint/eslint/releases">eslint's releases</a>.</em></p>
<blockquote>
<h2>v8.46.0</h2>
<h2>Features</h2>
<ul>
<li><a href=""><code>8a93438</code></a> feat: <code>require-unicode-regexp</code> support <code>v</code> flag (<a href="">#17402</a>) (SUZUKI Sosuke)</li>
<li><a href=""><code>1a2f966</code></a> feat: <code>no-useless-escape</code> support <code>v</code> flag (<a href="">#17420</a>) (Yosuke Ota)</li>
<li><a href=""><code>ee68d1d</code></a> feat: <code>no-empty-character-class</code> support <code>v</code> flag (<a href="">#17419</a>) (Milos Djermanovic)</li>
<li><a href=""><code>853d32b</code></a> feat: deprecate no-return-await (<a href="">#17417</a>) (Carlos Lopez)</li>
<li><a href=""><code>d4f02e4</code></a> feat: <code>no-control-regex</code> support <code>v</code> flag (<a href="">#17405</a>) (Yosuke Ota)</li>
<li><a href=""><code>2a35f3e</code></a> feat: <code>prefer-named-capture-group</code> support <code>v</code> flag (<a href="">#17409</a>) (Yosuke Ota)</li>
<li><a href=""><code>8ca8b50</code></a> feat: Better error message for flat config plugins (<a href="">#17399</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>509f753</code></a> feat: <code>no-misleading-character-class</code> support <code>v</code> flag (<a href="">#17406</a>) (Yosuke Ota)</li>
<li><a href=""><code>3caf514</code></a> feat: <code>no-regex-spaces</code> support <code>v</code> flag (<a href="">#17407</a>) (Yosuke Ota)</li>
<li><a href=""><code>b7fad2b</code></a> feat: <code>prefer-regex-literals</code> support <code>v</code> flag (<a href="">#17410</a>) (Yosuke Ota)</li>
<li><a href=""><code>a6a3ad4</code></a> feat: <code>no-useless-backreference</code> support <code>v</code> flag (<a href="">#17408</a>) (Yosuke Ota)</li>
<li><a href=""><code>94954a7</code></a> feat: <code>no-invalid-regexp</code> support <code>v</code> flag (<a href="">#17404</a>) (Yosuke Ota)</li>
<li><a href=""><code>1af6eac</code></a> feat: adds option for allowing empty object patterns as parameter (<a href="">#17365</a>) (Tanuj Kanti)</li>
<li><a href=""><code>cf03104</code></a> feat: Improve config error messages (<a href="">#17385</a>) (Nicholas C. Zakas)</li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li><a href=""><code>9803c7c</code></a> fix: FlatESLint#getRulesMetaForResults shouldn't throw on unknown rules (<a href="">#17393</a>) (Milos Djermanovic)</li>
<li><a href=""><code>42faa17</code></a> fix: Update no-loop-func to not overlap with no-undef (<a href="">#17358</a>) (Matt Wilkinson)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li><a href=""><code>4d474e3</code></a> docs: update with TypeScript info (<a href="">#17423</a>) (James)</li>
<li><a href=""><code>091f44e</code></a> docs: File extension named processor deprecation (<a href="">#17362</a>) (Matt Wilkinson)</li>
<li><a href=""><code>9254a6c</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>6d6dc51</code></a> docs: fix overlapping of <code>open in playground</code> button (<a href="">#17403</a>) (Tanuj Kanti)</li>
<li><a href=""><code>7fc3a2c</code></a> docs: Add private class features info to no-underscore-dangle (<a href="">#17386</a>) (Matt Wilkinson)</li>
<li><a href=""><code>da73e58</code></a> docs: Migrating <code>eslint-env</code> configuration comments (<a href="">#17390</a>) (Francesco Trotta)</li>
<li><a href=""><code>80dffed</code></a> docs: fix Ignoring Files section in config migration guide (<a href="">#17392</a>) (Milos Djermanovic)</li>
<li><a href=""><code>8a9abb7</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>7e9be4b</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>0b0bbe0</code></a> docs: Update README (GitHub Actions Bot)</li>
</ul>
<h2>Chores</h2>
<ul>
<li><a href=""><code>d1eb7e4</code></a> chore: Update ecosystem dependencies (<a href="">#17427</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>fab9e97</code></a> chore: package.json update for eslint-config-eslint release (ESLint Jenkins)</li>
<li><a href=""><code>6246711</code></a> chore: package.json update for <code>@​eslint/js</code> release (ESLint Jenkins)</li>
<li><a href=""><code>0aa0bc3</code></a> chore: Add PRs to triage project (<a href="">#17421</a>) (Nicholas C. Zakas)</li>
</ul>
<h2>v8.45.0</h2>
<h2>Features</h2>
<ul>
<li><a href=""><code>cdd063c</code></a> feat: Expose LegacyESLint in unsupported API (<a href="">#17341</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>d34abe5</code></a> feat: fix indent rule for else-if (<a href="">#17318</a>) (Milos Djermanovic)</li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li><a href=""><code>b79b6fb</code></a> fix: Fix suggestion message in <code>no-useless-escape</code> (<a href="">#17339</a>) (Francesco Trotta)</li>
<li><a href=""><code>c667055</code></a> fix: provide unique <code>fix</code> and <code>fix.range</code> objects in lint messages (<a href="">#17332</a>) (Milos Djermanovic)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li><a href=""><code>89f3225</code></a> docs: add playground links to correct and incorrect code blocks (<a href="">#17306</a>) (Josh Goldberg ✨)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/eslint/eslint/blob/main/CHANGELOG.md">eslint's changelog</a>.</em></p>
<blockquote>
<p>v8.46.0 - July 28, 2023</p>
<ul>
<li><a href=""><code>d1eb7e4</code></a> chore: Update ecosystem dependencies (<a href="">#17427</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>fab9e97</code></a> chore: package.json update for eslint-config-eslint release (ESLint Jenkins)</li>
<li><a href=""><code>6246711</code></a> chore: package.json update for <code>@​eslint/js</code> release (ESLint Jenkins)</li>
<li><a href=""><code>8a93438</code></a> feat: <code>require-unicode-regexp</code> support <code>v</code> flag (<a href="">#17402</a>) (SUZUKI Sosuke)</li>
<li><a href=""><code>4d474e3</code></a> docs: update with TypeScript info (<a href="">#17423</a>) (James)</li>
<li><a href=""><code>091f44e</code></a> docs: File extension named processor deprecation (<a href="">#17362</a>) (Matt Wilkinson)</li>
<li><a href=""><code>1a2f966</code></a> feat: <code>no-useless-escape</code> support <code>v</code> flag (<a href="">#17420</a>) (Yosuke Ota)</li>
<li><a href=""><code>0aa0bc3</code></a> chore: Add PRs to triage project (<a href="">#17421</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>ee68d1d</code></a> feat: <code>no-empty-character-class</code> support <code>v</code> flag (<a href="">#17419</a>) (Milos Djermanovic)</li>
<li><a href=""><code>853d32b</code></a> feat: deprecate no-return-await (<a href="">#17417</a>) (Carlos Lopez)</li>
<li><a href=""><code>d4f02e4</code></a> feat: <code>no-control-regex</code> support <code>v</code> flag (<a href="">#17405</a>) (Yosuke Ota)</li>
<li><a href=""><code>9254a6c</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>2a35f3e</code></a> feat: <code>prefer-named-capture-group</code> support <code>v</code> flag (<a href="">#17409</a>) (Yosuke Ota)</li>
<li><a href=""><code>8ca8b50</code></a> feat: Better error message for flat config plugins (<a href="">#17399</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>6d6dc51</code></a> docs: fix overlapping of <code>open in playground</code> button (<a href="">#17403</a>) (Tanuj Kanti)</li>
<li><a href=""><code>509f753</code></a> feat: <code>no-misleading-character-class</code> support <code>v</code> flag (<a href="">#17406</a>) (Yosuke Ota)</li>
<li><a href=""><code>3caf514</code></a> feat: <code>no-regex-spaces</code> support <code>v</code> flag (<a href="">#17407</a>) (Yosuke Ota)</li>
<li><a href=""><code>b7fad2b</code></a> feat: <code>prefer-regex-literals</code> support <code>v</code> flag (<a href="">#17410</a>) (Yosuke Ota)</li>
<li><a href=""><code>a6a3ad4</code></a> feat: <code>no-useless-backreference</code> support <code>v</code> flag (<a href="">#17408</a>) (Yosuke Ota)</li>
<li><a href=""><code>94954a7</code></a> feat: <code>no-invalid-regexp</code> support <code>v</code> flag (<a href="">#17404</a>) (Yosuke Ota)</li>
<li><a href=""><code>7fc3a2c</code></a> docs: Add private class features info to no-underscore-dangle (<a href="">#17386</a>) (Matt Wilkinson)</li>
<li><a href=""><code>da73e58</code></a> docs: Migrating <code>eslint-env</code> configuration comments (<a href="">#17390</a>) (Francesco Trotta)</li>
<li><a href=""><code>10e9cfa</code></a> Merge pull request from GHSA-qwh7-v8hg-w8rh (leo-centurion)</li>
<li><a href=""><code>1af6eac</code></a> feat: adds option for allowing empty object patterns as parameter (<a href="">#17365</a>) (Tanuj Kanti)</li>
<li><a href=""><code>9803c7c</code></a> fix: FlatESLint#getRulesMetaForResults shouldn't throw on unknown rules (<a href="">#17393</a>) (Milos Djermanovic)</li>
<li><a href=""><code>80dffed</code></a> docs: fix Ignoring Files section in config migration guide (<a href="">#17392</a>) (Milos Djermanovic)</li>
<li><a href=""><code>8a9abb7</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>cf03104</code></a> feat: Improve config error messages (<a href="">#17385</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>42faa17</code></a> fix: Update no-loop-func to not overlap with no-undef (<a href="">#17358</a>) (Matt Wilkinson)</li>
<li><a href=""><code>7e9be4b</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>0b0bbe0</code></a> docs: Update README (GitHub Actions Bot)</li>
</ul>
<p>v8.45.0 - July 14, 2023</p>
<ul>
<li><a href=""><code>68f63d7</code></a> chore: package.json update for <code>@​eslint/js</code> release (ESLint Jenkins)</li>
<li><a href=""><code>89f3225</code></a> docs: add playground links to correct and incorrect code blocks (<a href="">#17306</a>) (Josh Goldberg ✨)</li>
<li><a href=""><code>f8892b5</code></a> docs: Expand rule option schema docs (<a href="">#17198</a>) (Matt Wilkinson)</li>
<li><a href=""><code>8bcbf11</code></a> docs: Config Migration Guide (<a href="">#17230</a>) (Ben Perlmutter)</li>
<li><a href=""><code>bb30908</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>b79b6fb</code></a> fix: Fix suggestion message in <code>no-useless-escape</code> (<a href="">#17339</a>) (Francesco Trotta)</li>
<li><a href=""><code>84d243b</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>5ca9b4d</code></a> chore: update eslint-config-eslint exports (<a href="">#17336</a>) (Milos Djermanovic)</li>
<li><a href=""><code>b762632</code></a> docs: Update README (GitHub Actions Bot)</li>
<li><a href=""><code>7bf2e86</code></a> chore: remove unused dependencies (<a href="">#17352</a>) (Percy Ma)</li>
<li><a href=""><code>c6f8cd0</code></a> chore: Remove <code>defaultIgnores</code> from FlatESLint private members (<a href="">#17349</a>) (Francesco Trotta)</li>
<li><a href=""><code>cdd063c</code></a> feat: Expose LegacyESLint in unsupported API (<a href="">#17341</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>c667055</code></a> fix: provide unique <code>fix</code> and <code>fix.range</code> objects in lint messages (<a href="">#17332</a>) (Milos Djermanovic)</li>
<li><a href=""><code>138c096</code></a> docs: add more prefer-destructuring examples with array destructuring (<a href="">#17330</a>) (Milos Djermanovic)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c87db63</code></a> 8.46.0</li>
<li><a href=""><code>b51015f</code></a> Build: changelog update for 8.46.0</li>
<li><a href=""><code>d1eb7e4</code></a> chore: Update ecosystem dependencies (<a href="">#17427</a>)</li>
<li><a href=""><code>fab9e97</code></a> chore: package.json update for eslint-config-eslint release</li>
<li><a href=""><code>6246711</code></a> chore: package.json update for <code>@​eslint/js</code> release</li>
<li><a href=""><code>8a93438</code></a> feat: <code>require-unicode-regexp</code> support <code>v</code> flag (<a href="">#17402</a>)</li>
<li><a href=""><code>4d474e3</code></a> docs: update with TypeScript info (<a href="">#17423</a>)</li>
<li><a href=""><code>091f44e</code></a> docs: File extension named processor deprecation (<a href="">#17362</a>)</li>
<li><a href=""><code>1a2f966</code></a> feat: <code>no-useless-escape</code> support <code>v</code> flag (<a href="">#17420</a>)</li>
<li><a href=""><code>0aa0bc3</code></a> chore: Add PRs to triage project (<a href="">#17421</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/eslint/eslint/compare/v8.39.0...v8.46.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=eslint&package-manager=npm_and_yarn&previous-version=8.39.0&new-version=8.46.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8f585296a3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
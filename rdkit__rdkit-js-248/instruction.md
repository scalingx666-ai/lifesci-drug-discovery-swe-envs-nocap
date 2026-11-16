# Issue

**Title:** Bump eslint from 8.27.0 to 8.28.0

## Description

Bumps [eslint](https://github.com/eslint/eslint) from 8.27.0 to 8.28.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/eslint/eslint/releases">eslint's releases</a>.</em></p>
<blockquote>
<h2>v8.28.0</h2>
<h2>Features</h2>
<ul>
<li><a href=""><code>63bce44</code></a> feat: add <code>ignoreClassFieldInitialValues</code> option to no-magic-numbers (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16539">#16539</a>) (Milos Djermanovic)</li>
<li><a href=""><code>8385ecd</code></a> feat: multiline properties in rule <code>key-spacing</code> with option <code>align</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16532">#16532</a>) (Francesco Trotta)</li>
<li><a href=""><code>a4e89db</code></a> feat: <code>no-obj-calls</code> support <code>Intl</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16543">#16543</a>) (Sosuke Suzuki)</li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li><a href=""><code>c50ae4f</code></a> fix: Ensure that dot files are found with globs. (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16550">#16550</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>9432b67</code></a> fix: throw error for first unmatched pattern (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16533">#16533</a>) (Milos Djermanovic)</li>
<li><a href=""><code>e76c382</code></a> fix: allow <code>* 1</code> when followed by <code>/</code> in no-implicit-coercion (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16522">#16522</a>) (Milos Djermanovic)</li>
</ul>
<h2>Documentation</h2>
<ul>
<li><a href=""><code>34c05a7</code></a> docs: Language Options page intro and tweaks (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16511">#16511</a>) (Ben Perlmutter)</li>
<li><a href=""><code>3e66387</code></a> docs: add intro and edit ignoring files page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16510">#16510</a>) (Ben Perlmutter)</li>
<li><a href=""><code>436f712</code></a> docs: fix Header UI inconsistency (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16464">#16464</a>) (Tanuj Kanti)</li>
<li><a href=""><code>f743816</code></a> docs: switch to wrench emoji for auto-fixable rules (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16545">#16545</a>) (Bryan Mishkin)</li>
<li><a href=""><code>bc0547e</code></a> docs: improve styles for versions and languages page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16553">#16553</a>) (Nitin Kumar)</li>
<li><a href=""><code>6070f58</code></a> docs: clarify esquery issue workaround (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16556">#16556</a>) (Milos Djermanovic)</li>
<li><a href=""><code>b48e4f8</code></a> docs: Command Line Interface intro and tweaks (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16535">#16535</a>) (Ben Perlmutter)</li>
<li><a href=""><code>b92b30f</code></a> docs: Add Rules page intro and content tweaks (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16523">#16523</a>) (Ben Perlmutter)</li>
<li><a href=""><code>1769b42</code></a> docs: Integrations page introduction (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16548">#16548</a>) (Ben Perlmutter)</li>
<li><a href=""><code>a8d0a57</code></a> docs: make table of contents sticky on desktop (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16506">#16506</a>) (Sam Chen)</li>
<li><a href=""><code>a01315a</code></a> docs: fix route of japanese translation site (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16542">#16542</a>) (Tanuj Kanti)</li>
<li><a href=""><code>0515628</code></a> docs: use emoji instead of svg for deprecated rule (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16536">#16536</a>) (Bryan Mishkin)</li>
<li><a href=""><code>68f1288</code></a> docs: set default layouts (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16484">#16484</a>) (Percy Ma)</li>
<li><a href=""><code>776827a</code></a> docs: init config about specifying shared configs (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16483">#16483</a>) (Percy Ma)</li>
<li><a href=""><code>5c39425</code></a> docs: fix broken link to plugins (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16520">#16520</a>) (Ádám T. Nagy)</li>
<li><a href=""><code>c97c789</code></a> docs: Add missing no-new-native-nonconstructor docs code fence (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16503">#16503</a>) (Brandon Mills)</li>
</ul>
<h2>Chores</h2>
<ul>
<li><a href=""><code>e94a4a9</code></a> chore: Add tests to verify <a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16038">#16038</a> is fixed (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16538">#16538</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>e13f194</code></a> chore: stricter validation of <code>meta.docs.description</code> in core rules (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16529">#16529</a>) (Milos Djermanovic)</li>
<li><a href=""><code>72dbfbc</code></a> chore: use <code>pkg</code> parameter in <code>getNpmPackageVersion</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16525">#16525</a>) (webxmsj)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/eslint/eslint/blob/main/CHANGELOG.md">eslint's changelog</a>.</em></p>
<blockquote>
<p>v8.28.0 - November 18, 2022</p>
<ul>
<li><a href=""><code>34c05a7</code></a> docs: Language Options page intro and tweaks (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16511">#16511</a>) (Ben Perlmutter)</li>
<li><a href=""><code>3e66387</code></a> docs: add intro and edit ignoring files page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16510">#16510</a>) (Ben Perlmutter)</li>
<li><a href=""><code>436f712</code></a> docs: fix Header UI inconsistency (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16464">#16464</a>) (Tanuj Kanti)</li>
<li><a href=""><code>f743816</code></a> docs: switch to wrench emoji for auto-fixable rules (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16545">#16545</a>) (Bryan Mishkin)</li>
<li><a href=""><code>bc0547e</code></a> docs: improve styles for versions and languages page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16553">#16553</a>) (Nitin Kumar)</li>
<li><a href=""><code>6070f58</code></a> docs: clarify esquery issue workaround (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16556">#16556</a>) (Milos Djermanovic)</li>
<li><a href=""><code>b48e4f8</code></a> docs: Command Line Interface intro and tweaks (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16535">#16535</a>) (Ben Perlmutter)</li>
<li><a href=""><code>b92b30f</code></a> docs: Add Rules page intro and content tweaks (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16523">#16523</a>) (Ben Perlmutter)</li>
<li><a href=""><code>1769b42</code></a> docs: Integrations page introduction (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16548">#16548</a>) (Ben Perlmutter)</li>
<li><a href=""><code>63bce44</code></a> feat: add <code>ignoreClassFieldInitialValues</code> option to no-magic-numbers (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16539">#16539</a>) (Milos Djermanovic)</li>
<li><a href=""><code>c50ae4f</code></a> fix: Ensure that dot files are found with globs. (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16550">#16550</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>a8d0a57</code></a> docs: make table of contents sticky on desktop (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16506">#16506</a>) (Sam Chen)</li>
<li><a href=""><code>9432b67</code></a> fix: throw error for first unmatched pattern (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16533">#16533</a>) (Milos Djermanovic)</li>
<li><a href=""><code>8385ecd</code></a> feat: multiline properties in rule <code>key-spacing</code> with option <code>align</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16532">#16532</a>) (Francesco Trotta)</li>
<li><a href=""><code>a4e89db</code></a> feat: <code>no-obj-calls</code> support <code>Intl</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16543">#16543</a>) (Sosuke Suzuki)</li>
<li><a href=""><code>a01315a</code></a> docs: fix route of japanese translation site (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16542">#16542</a>) (Tanuj Kanti)</li>
<li><a href=""><code>e94a4a9</code></a> chore: Add tests to verify <a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16038">#16038</a> is fixed (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16538">#16538</a>) (Nicholas C. Zakas)</li>
<li><a href=""><code>0515628</code></a> docs: use emoji instead of svg for deprecated rule (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16536">#16536</a>) (Bryan Mishkin)</li>
<li><a href=""><code>e76c382</code></a> fix: allow <code>* 1</code> when followed by <code>/</code> in no-implicit-coercion (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16522">#16522</a>) (Milos Djermanovic)</li>
<li><a href=""><code>68f1288</code></a> docs: set default layouts (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16484">#16484</a>) (Percy Ma)</li>
<li><a href=""><code>e13f194</code></a> chore: stricter validation of <code>meta.docs.description</code> in core rules (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16529">#16529</a>) (Milos Djermanovic)</li>
<li><a href=""><code>776827a</code></a> docs: init config about specifying shared configs (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16483">#16483</a>) (Percy Ma)</li>
<li><a href=""><code>72dbfbc</code></a> chore: use <code>pkg</code> parameter in <code>getNpmPackageVersion</code> (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16525">#16525</a>) (webxmsj)</li>
<li><a href=""><code>5c39425</code></a> docs: fix broken link to plugins (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16520">#16520</a>) (Ádám T. Nagy)</li>
<li><a href=""><code>c97c789</code></a> docs: Add missing no-new-native-nonconstructor docs code fence (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16503">#16503</a>) (Brandon Mills)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b8769f1</code></a> 8.28.0</li>
<li><a href=""><code>d2b0723</code></a> Build: changelog update for 8.28.0</li>
<li><a href=""><code>34c05a7</code></a> docs: Language Options page intro and tweaks (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16511">#16511</a>)</li>
<li><a href=""><code>3e66387</code></a> docs: add intro and edit ignoring files page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16510">#16510</a>)</li>
<li><a href=""><code>436f712</code></a> docs: fix Header UI inconsistency (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16464">#16464</a>)</li>
<li><a href=""><code>f743816</code></a> docs: switch to wrench emoji for auto-fixable rules (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16545">#16545</a>)</li>
<li><a href=""><code>bc0547e</code></a> docs: improve styles for versions and languages page (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16553">#16553</a>)</li>
<li><a href=""><code>6070f58</code></a> docs: clarify esquery issue workaround (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16556">#16556</a>)</li>
<li><a href=""><code>b48e4f8</code></a> docs: Command Line Interface intro and tweaks (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16535">#16535</a>)</li>
<li><a href=""><code>b92b30f</code></a> docs: Add Rules page intro and content tweaks (<a href="https://github-redirect.dependabot.com/eslint/eslint/issues/16523">#16523</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/eslint/eslint/compare/v8.27.0...v8.28.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=eslint&package-manager=npm_and_yarn&previous-version=8.27.0&new-version=8.28.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3192f22afbad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
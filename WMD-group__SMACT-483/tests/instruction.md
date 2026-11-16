# Issue

**Title:** Bump myst-nb from 1.1.2 to 1.3.0

## Description

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

Bumps [myst-nb](https://github.com/executablebooks/myst-nb) from 1.1.2 to 1.3.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/executablebooks/myst-nb/releases">myst-nb's releases</a>.</em></p>
<blockquote>
<h2>v1.3.0</h2>
<!-- raw HTML omitted -->
<h2>What's Changed</h2>
<ul>
<li>DOCS: clarify meaning of merge_streams option (<a href="">#664</a>) by <a href="https://github.com/mforbes"><code>@​mforbes</code></a> in <a href="">executablebooks/MyST-NB#665</a></li>
<li>MAINT: minor cleanups by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#669</a></li>
<li>ENH: Adding scroll bars with proper cell tags by <a href="https://github.com/dprada"><code>@​dprada</code></a> in <a href="">executablebooks/MyST-NB#454</a></li>
<li>Use admonitions to style collapsible cells :) by <a href="https://github.com/sneakers-the-rat"><code>@​sneakers-the-rat</code></a> in <a href="">executablebooks/MyST-NB#656</a></li>
<li>DOC: Mention conflict with myst_parser extension by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#672</a></li>
<li>TEST: Adding a test case for multiple captioned figures by <a href="https://github.com/mmcky"><code>@​mmcky</code></a> in <a href="">executablebooks/MyST-NB#373</a></li>
<li>Fix link to EBP Contributing Guide by <a href="https://github.com/StFroese"><code>@​StFroese</code></a> in <a href="">executablebooks/MyST-NB#674</a></li>
<li>Improve output cells in dark mode by <a href="https://github.com/jaladh-singhal"><code>@​jaladh-singhal</code></a> in <a href="">executablebooks/MyST-NB#679</a></li>
<li>Add scroll_outputs configuration by <a href="https://github.com/jaladh-singhal"><code>@​jaladh-singhal</code></a> in <a href="">executablebooks/MyST-NB#683</a></li>
<li>ENH: Add handling of image based <code>PendingGlueReference</code> in <code>generate_any_nodes</code> by <a href="https://github.com/StFroese"><code>@​StFroese</code></a> in <a href="">executablebooks/MyST-NB#675</a></li>
<li>MAINT: limit ipython in tox job, too by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#687</a></li>
<li>docs: nicer types in docs by <a href="https://github.com/henryiii"><code>@​henryiii</code></a> in <a href="">executablebooks/MyST-NB#688</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/mforbes"><code>@​mforbes</code></a> made their first contribution in <a href="">executablebooks/MyST-NB#665</a></li>
<li><a href="https://github.com/dprada"><code>@​dprada</code></a> made their first contribution in <a href="">executablebooks/MyST-NB#454</a></li>
<li><a href="https://github.com/StFroese"><code>@​StFroese</code></a> made their first contribution in <a href="">executablebooks/MyST-NB#674</a></li>
<li><a href="https://github.com/jaladh-singhal"><code>@​jaladh-singhal</code></a> made their first contribution in <a href="">executablebooks/MyST-NB#679</a></li>
<li><a href="https://github.com/henryiii"><code>@​henryiii</code></a> made their first contribution in <a href="">executablebooks/MyST-NB#688</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/executablebooks/MyST-NB/compare/v1.2.0...v1.3.0">https://github.com/executablebooks/MyST-NB/compare/v1.2.0...v1.3.0</a></p>
<h2>v1.2.0 - 2025-02-07</h2>
<p>(<a href="https://github.com/executablebooks/MyST-NB/compare/v1.1.2...59fd54fd296ed5395665719396abbf46547fd158">full changelog</a>)</p>
<h3>Enhancements made</h3>
<ul>
<li>ENH: Support translated notebooks <a href="">#600</a> (<a href="https://github.com/OriolAbril"><code>@​OriolAbril</code></a>)</li>
</ul>
<h3>Bugs fixed</h3>
<ul>
<li>FIX: fix path suffix condition in core/read.py <a href="">#641</a> (<a href="https://github.com/je-cook"><code>@​je-cook</code></a>)</li>
<li>BUG: using rstrip to preserve indents <a href="">#637</a> (<a href="https://github.com/bsipocz"><code>@​bsipocz</code></a>)</li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>MAINT: fix CI in prep for release <a href="">#659</a> (<a href="https://github.com/bsipocz"><code>@​bsipocz</code></a>)</li>
<li>MAINT: fail on warnings <a href="">#647</a> (<a href="https://github.com/bsipocz"><code>@​bsipocz</code></a>)</li>
<li>MAINT: adding devdeps testing and cron and workflow dispatch <a href="">#639</a> (<a href="https://github.com/bsipocz"><code>@​bsipocz</code></a>)</li>
<li>MAINT: adding python 3.13 to CI and classifiers <a href="">#635</a> (<a href="https://github.com/bsipocz"><code>@​bsipocz</code></a>)</li>
</ul>
<h3>Documentation improvements</h3>
<ul>
<li>DOCS: clarify meaning of merge_streams option (<a href="">#664</a>) <a href="">#665</a> (<a href="https://github.com/mforbes"><code>@​mforbes</code></a>)</li>
<li>DOCS: add <code>configuration</code> key to readthedocs.yml <a href="">#657</a> (<a href="https://github.com/sneakers-the-rat"><code>@​sneakers-the-rat</code></a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/executablebooks/MyST-NB/blob/main/CHANGELOG.md">myst-nb's changelog</a>.</em></p>
<blockquote>
<h2>v1.3.0 - 2025-07-13</h2>
<p>(<a href="https://github.com/executablebooks/MyST-NB/compare/v1.2.0...v1.3.0">full changelog</a>)</p>
<h2>What's Changed</h2>
<h3>Enhancements made</h3>
<ul>
<li>ENH: Adding scroll bars with proper cell tags by <a href="https://github.com/dprada"><code>@​dprada</code></a> in <a href="">executablebooks/MyST-NB#454</a></li>
<li>Use admonitions to style collapsible cells :) by <a href="https://github.com/sneakers-the-rat"><code>@​sneakers-the-rat</code></a> in <a href="">executablebooks/MyST-NB#656</a></li>
<li>Improve output cells in dark mode by <a href="https://github.com/jaladh-singhal"><code>@​jaladh-singhal</code></a> in <a href="">executablebooks/MyST-NB#679</a></li>
<li>Add scroll_outputs configuration by <a href="https://github.com/jaladh-singhal"><code>@​jaladh-singhal</code></a> in <a href="">executablebooks/MyST-NB#683</a></li>
<li>ENH: Add handling of image based <code>PendingGlueReference</code> in <code>generate_any_nodes</code> by <a href="https://github.com/StFroese"><code>@​StFroese</code></a> in <a href="">executablebooks/MyST-NB#675</a></li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>DOCS: clarify meaning of merge_streams option (<a href="">#664</a>) by <a href="https://github.com/mforbes"><code>@​mforbes</code></a> in <a href="">executablebooks/MyST-NB#665</a></li>
<li>MAINT: minor cleanups by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#669</a></li>
<li>DOC: Mention conflict with myst_parser extension by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#672</a></li>
<li>TEST: Adding a test case for multiple captioned figures by <a href="https://github.com/mmcky"><code>@​mmcky</code></a> in <a href="">executablebooks/MyST-NB#373</a></li>
<li>Fix link to EBP Contributing Guide by <a href="https://github.com/StFroese"><code>@​StFroese</code></a> in <a href="">executablebooks/MyST-NB#674</a></li>
<li>MAINT: limit ipython in tox job, too by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#687</a></li>
<li>docs: nicer types in docs by <a href="https://github.com/henryiii"><code>@​henryiii</code></a> in <a href="">executablebooks/MyST-NB#688</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/mforbes"><code>@​mforbes</code></a> made their first contribution in <a href="">executablebooks/MyST-NB#665</a></li>
<li><a href="https://github.com/dprada"><code>@​dprada</code></a> made their first contribution in <a href="">executablebooks/MyST-NB#454</a></li>
<li><a href="https://github.com/StFroese"><code>@​StFroese</code></a> made their first contribution in <a href="">executablebooks/MyST-NB#674</a></li>
<li><a href="https://github.com/jaladh-singhal"><code>@​jaladh-singhal</code></a> made their first contribution in <a href="">executablebooks/MyST-NB#679</a></li>
<li><a href="https://github.com/henryiii"><code>@​henryiii</code></a> made their first contribution in <a href="">executablebooks/MyST-NB#688</a></li>
</ul>
<h2>v1.2.0 - 2025-02-07</h2>
<p>(<a href="https://github.com/executablebooks/MyST-NB/compare/v1.1.2...v1.2.0">full changelog</a>)</p>
<h3>Enhancements made</h3>
<ul>
<li>ENH: Support translated notebooks by <a href="https://github.com/OriolAbril"><code>@​OriolAbril</code></a> in <a href="">executablebooks/MyST-NB#600</a></li>
</ul>
<h3>Bugs Fixed</h3>
<ul>
<li>BUG: using rstrip to preserve indents by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#637</a></li>
<li>FIX: fix path suffix condition in core/read.py by <a href="https://github.com/je-cook"><code>@​je-cook</code></a> in <a href="">executablebooks/MyST-NB#641</a></li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>DOCS: adding changelog for 1.1.2 by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#638</a></li>
<li>MAINT: adding python 3.13 to CI and classifiers by <a href="https://github.com/bsipocz"><code>@​bsipocz</code></a> in <a href="">executablebooks/MyST-NB#635</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6bb973c</code></a> Preparing for release v1.3</li>
<li><a href=""><code>23b2d62</code></a> And one more bot to ignore</li>
<li><a href=""><code>ff699ca</code></a> Adding more bots to ignore</li>
<li><a href=""><code>1e2d1a4</code></a> docs: nicer types in docs (<a href="">#688</a>)</li>
<li><a href=""><code>4020e26</code></a> MAINT: limit ipython in tox job, too (<a href="">#687</a>)</li>
<li><a href=""><code>b7387d5</code></a> ENH: Add handling of image based <code>PendingGlueReference</code> in `generate_any_node...</li>
<li><a href=""><code>29d6e15</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#685</a>)</li>
<li><a href=""><code>1ddc3a5</code></a> Add scroll_outputs configuration (<a href="">#683</a>)</li>
<li><a href=""><code>9fe8848</code></a> build(deps): bump codecov/codecov-action in the actions group (<a href="">#676</a>)</li>
<li><a href=""><code>fc73430</code></a> Improve output cells in dark mode (<a href="">#679</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/executablebooks/myst-nb/compare/v1.1.2...v1.3.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=myst-nb&package-manager=pip&previous-version=1.1.2&new-version=1.3.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24d5a26abea1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
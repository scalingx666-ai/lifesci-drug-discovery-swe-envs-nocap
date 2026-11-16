# Issue

**Title:** Bump ossf/scorecard-action from 2.4.4 to 2.5.0 in /.github/workflows

## Description

Bumps [ossf/scorecard-action](https://github.com/ossf/scorecard-action) from 2.4.4 to 2.5.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/ossf/scorecard-action/releases">ossf/scorecard-action's releases</a>.</em></p>
<blockquote>
<h2>v2.5.0</h2>
<h2>What's Changed</h2>
<p>This release moves the action to Scorecard v5.6.0, the first Scorecard release since its hosted
services moved to new infrastructure.</p>
<p>For changes to checks and results, and what the infrastructure move means for you, see the
<a href="https://github.com/ossf/scorecard/releases/tag/v5.6.0">Scorecard v5.6.0 release notes</a>.</p>
<ul>
<li>The action's container image is built with Go 1.27.2 on a refreshed distroless base. by
<a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1716</a></li>
<li>The installer (<code>cmd/installer</code>) now creates <code>.github/workflows/scorecard.yml</code>, and still
recognizes existing <code>scorecards.yml</code> and <code>scorecards-analysis.yml</code> workflows. by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1716</a></li>
<li>The Scorecard version in results now always matches the Scorecard release the action is built
with. by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1718</a></li>
<li>The action no longer prints the GitHub token variable while validating its options. by
<a href="https://github.com/arpitjain099"><code>@​arpitjain099</code></a> in <a href="">ossf/scorecard-action#1709</a></li>
<li><code>results_format</code> accepts <code>intoto</code>, which wraps the JSON results in an in-toto attestation
statement. by <a href="https://github.com/puerco"><code>@​puerco</code></a> in <a href="">ossf/scorecard-action#1702</a></li>
</ul>
<h3>Other</h3>
<ul>
<li>Add a daily canary against Scorecard main by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1711</a></li>
<li>Bump Scorecard to the v5.6.0 candidate and fix the canary toolchain by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1714</a></li>
<li>Run Scorecard on every merge, add a zizmor presubmit, analyze workflows with CodeQL, and update
RELEASE.md by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1716</a></li>
<li>Bump Scorecard to v5.6.0 by <a href="https://github.com/justaugustus"><code>@​justaugustus</code></a> in <a href="">ossf/scorecard-action#1719</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/arpitjain099"><code>@​arpitjain099</code></a> made their first contribution in <a href="">ossf/scorecard-action#1709</a></li>
<li><a href="https://github.com/puerco"><code>@​puerco</code></a> made their first contribution in <a href="">ossf/scorecard-action#1702</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/ossf/scorecard-action/compare/v2.4.4...v2.5.0">https://github.com/ossf/scorecard-action/compare/v2.4.4...v2.5.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>fa7117d</code></a> Bump action tag for v2.5.0 release (<a href="">#1720</a>)</li>
<li><a href=""><code>cef4eb5</code></a> :seedling: Bump Scorecard to v5.6.0 (<a href="">#1719</a>)</li>
<li><a href=""><code>bedb16e</code></a> :sparkles: Add intoto results format (<a href="">#1702</a>)</li>
<li><a href=""><code>de70347</code></a> Remove the leftover debug print of the auth token (<a href="">#1709</a>)</li>
<li><a href=""><code>950873d</code></a> :seedling: Derive the reported Scorecard version from go.mod (<a href="">#1718</a>)</li>
<li><a href=""><code>2ce8ee4</code></a> :seedling: Bump github.com/sigstore/cosign/v2 from 2.6.4 to 2.6.5 (<a href="">#1695</a>)</li>
<li><a href=""><code>aabdf5a</code></a> :seedling: Bump the github-actions group across 1 directory with 7 updates (#...</li>
<li><a href=""><code>b4b9adf</code></a> :seedling: CodeQL: Analyze workflows instead of a placeholder JavaScript file</li>
<li><a href=""><code>4e9f2a2</code></a> :book: RELEASE.md: Document drafting release notes</li>
<li><a href=""><code>f618e8b</code></a> :seedling: Build the image with Go 1.27.2 and refresh distroless</li>
<li>Additional commits viewable in <a href="https://github.com/ossf/scorecard-action/compare/2d1146689b8cda280b9bc96326124645441f03bc...fa7117db83c52d787ae5a89f350999701505d78e">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ossf/scorecard-action&package-manager=github_actions&previous-version=2.4.4&new-version=2.5.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a1a7509f93f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
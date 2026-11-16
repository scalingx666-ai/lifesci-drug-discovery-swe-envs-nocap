# Issue

**Title:** Bump web-vitals from 3.1.1 to 3.4.0

## Description

Bumps [web-vitals](https://github.com/GoogleChrome/web-vitals) from 3.1.1 to 3.4.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/GoogleChrome/web-vitals/blob/main/CHANGELOG.md">web-vitals's changelog</a>.</em></p>
<blockquote>
<h3>v3.4.0 (2023-07-11)</h3>
<ul>
<li>Make <code>bindReporter</code> generic over metric type (<a href="">#359</a>)</li>
<li>Update INP status in README (<a href="">#362</a>)</li>
<li>Fix Metric types for better TypeScript support (<a href="">#356</a>)</li>
<li>Fix selector for SVGs for attribution build (<a href="">#354</a>)</li>
</ul>
<h3>v3.3.2 (2023-05-29)</h3>
<ul>
<li>Fix attribution types (<a href="">#348</a>)</li>
<li>Safe access navigation entry type (<a href="">#290</a>)</li>
</ul>
<h3>v3.3.1 (2023-04-04)</h3>
<ul>
<li>Export metric rating thresholds in attribution build as well.</li>
</ul>
<h3>v3.3.0 (2023-03-09)</h3>
<ul>
<li>Export metric rating thresholds, add explicit <code>MetricRatingThresholds</code> type (<a href="">#323</a>)</li>
<li>Trim classname selector (<a href="">#328</a>)</li>
<li>Add link to CrUX versus RUM blog post (<a href="">#327</a>)</li>
<li>Prevent LCP being reported for hidden prerendered pages (<a href="">#326</a>)</li>
<li>Add Server Timing information to docs (<a href="">#324</a>)</li>
<li>Fix link in <code>onINP()</code> thresholds comment (<a href="">#318</a>)</li>
<li>Update web.dev link for <code>onINP()</code> (<a href="">#307</a>)</li>
<li>Add a note about when to load the library (<a href="">#305</a>)</li>
</ul>
<h3>v3.2.0</h3>
<ul>
<li>Version number skipped</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>073033f</code></a> Release v3.4.0</li>
<li><a href=""><code>09436cb</code></a> Update CHANGELOG for 3.4.0 (<a href="">#366</a>)</li>
<li><a href=""><code>8c70367</code></a> Fix typo in inp.ts (<a href="">#364</a>)</li>
<li><a href=""><code>e35816e</code></a> make bindReporter generic over metric type (<a href="">#359</a>)</li>
<li><a href=""><code>7976972</code></a> Update the INP status in README (<a href="">#362</a>)</li>
<li><a href=""><code>5973d51</code></a> Metric type fixes (<a href="">#356</a>)</li>
<li><a href=""><code>1d2c191</code></a> Fix selector SVGs (<a href="">#354</a>)</li>
<li><a href=""><code>32919e4</code></a> Release v3.3.2</li>
<li><a href=""><code>1672619</code></a> Update changelog for v3.3.2 (<a href="">#349</a>)</li>
<li><a href=""><code>5154ee3</code></a> Fix attribution types (<a href="">#348</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/GoogleChrome/web-vitals/compare/v3.1.1...v3.4.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=web-vitals&package-manager=npm_and_yarn&previous-version=3.1.1&new-version=3.4.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2777560afa5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
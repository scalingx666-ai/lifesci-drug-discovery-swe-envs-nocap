# Issue

**Title:** Bump web-vitals from 2.1.4 to 3.0.0

## Description

Bumps [web-vitals](https://github.com/GoogleChrome/web-vitals) from 2.1.4 to 3.0.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/GoogleChrome/web-vitals/blob/main/CHANGELOG.md">web-vitals's changelog</a>.</em></p>
<blockquote>
<h3>v3.0.0 (2022-08-24)</h3>
<ul>
<li><strong>[BREAKING]</strong> Add a config object param to all metric functions (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/225">#225</a>)</li>
<li><strong>[BREAKING]</strong> Report TTFB after a bfcache restore (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/220">#220</a>)</li>
<li><strong>[BREAKING]</strong> Only include last LCP entry in metric entries (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/218">#218</a>)</li>
<li>Update the metric ID prefix for v3 (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/251">#251</a>)</li>
<li>Move the Navigation Timing API polyfill to the base+polyfill build (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/248">#248</a>)</li>
<li>Add a metric rating property (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/246">#246</a>)</li>
<li>Add deprecation notices for base+polyfill builds (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/242">#242</a>)</li>
<li>Add a new attribution build for debugging issues in the field (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/237">#237</a>, <a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/244">#244</a>)</li>
<li>Add support for prerendered pages (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/233">#233</a>)</li>
<li>Rename the <code>ReportHandler</code> type to <code>ReportCallback</code>, with alias for back-compat (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/225">#225</a>, <a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/227">#227</a>)</li>
<li>Add support for the new INP metric (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/221">#221</a>, <a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/232">#232</a>)</li>
<li>Rename <code>getXXX()</code> functions to <code>onXXX()</code> (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/222">#222</a>)</li>
<li>Add a <code>navigationType</code> property to the Metric object (<a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/pull/219">#219</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ab67c29</code></a> Release v3.0.0</li>
<li><a href=""><code>4a64f8a</code></a> Update CHANGELOG and README for v3</li>
<li><a href=""><code>1b38a6e</code></a> Update dependencies</li>
<li><a href=""><code>1eea0f5</code></a> Merge branch 'next'</li>
<li><a href=""><code>4ca38ae</code></a> Release v3.0.0-rc.0</li>
<li><a href=""><code>9fe3cc0</code></a> Update CHANGELOG</li>
<li><a href=""><code>67a92f2</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/issues/251">#251</a> from GoogleChrome/metric-id</li>
<li><a href=""><code>b0b5137</code></a> Update metric ID prefix to v3</li>
<li><a href=""><code>c385f96</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/GoogleChrome/web-vitals/issues/248">#248</a> from GoogleChrome/ttfb-polyfill</li>
<li><a href=""><code>7dfa9fa</code></a> Move NT polyfill to base+polyfill build</li>
<li>Additional commits viewable in <a href="https://github.com/GoogleChrome/web-vitals/compare/v2.1.4...v3.0.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=web-vitals&package-manager=npm_and_yarn&previous-version=2.1.4&new-version=3.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0781f3fe6ae0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
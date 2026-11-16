# Issue

**Title:** Bump conda-incubator/setup-miniconda from 2 to 3

## Description

Bumps [conda-incubator/setup-miniconda](https://github.com/conda-incubator/setup-miniconda) from 2 to 3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/conda-incubator/setup-miniconda/releases">conda-incubator/setup-miniconda's releases</a>.</em></p>
<blockquote>
<h2>Version 3.0.0</h2>
<h3>Features</h3>
<ul>
<li><a href="">#308</a> Update to node20</li>
<li><a href="">#291</a> Add conda-solver option (defaults to libmamba)</li>
</ul>
<h3>Fixes</h3>
<ul>
<li><a href="">#299</a> Fix condaBasePath when useBundled is false, and there's no pre-existing conda</li>
</ul>
<h3>Documentation</h3>
<ul>
<li><a href="">#309</a> Switch to main branch based development</li>
<li><a href="">#313</a> Specify team conda-incubator/setup-miniconda as codeowners</li>
<li><a href="">#318</a> README: update actions in examples, add security section, similar actions</li>
</ul>
<h3>Tasks and Maintenance</h3>
<ul>
<li><a href="">#307</a> Run dependabot against main branch and also update node packages</li>
<li><a href="">#311</a> Bump actions/checkout from 2 to 4</li>
<li><a href="">#310</a> Bump actions/cache from 1 to 3</li>
<li><a href="">#314</a> Strip/update dependencies</li>
<li><a href="">#315</a> Split lint into check and build, switch from <code>npm install</code> to <code>npm ci</code></li>
<li><a href="">#317</a> Bump normalize-url from 4.5.1 to 8.0.0</li>
<li><a href="">#316</a> Faster workflow response / saving resources via timeout/concurrency policy</li>
</ul>
<p><a href="">#308</a>: <a href="">conda-incubator/setup-miniconda#308</a>
<a href="">#291</a>: <a href="">conda-incubator/setup-miniconda#291</a>
<a href="">#299</a>: <a href="">conda-incubator/setup-miniconda#299</a>
<a href="">#309</a>: <a href="">conda-incubator/setup-miniconda#309</a>
<a href="">#313</a>: <a href="">conda-incubator/setup-miniconda#313</a>
<a href="">#318</a>: <a href="">conda-incubator/setup-miniconda#318</a>
<a href="">#307</a>: <a href="">conda-incubator/setup-miniconda#307</a>
<a href="">#311</a>: <a href="">conda-incubator/setup-miniconda#311</a>
<a href="">#310</a>: <a href="">conda-incubator/setup-miniconda#310</a>
<a href="">#314</a>: <a href="">conda-incubator/setup-miniconda#314</a>
<a href="">#315</a>: <a href="">conda-incubator/setup-miniconda#315</a>
<a href="">#317</a>: <a href="">conda-incubator/setup-miniconda#317</a>
<a href="">#316</a>: <a href="">conda-incubator/setup-miniconda#316</a></p>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/isuruf"><code>@​isuruf</code></a> made their first contribution in <a href="">conda-incubator/setup-miniconda#299</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/conda-incubator/setup-miniconda/compare/v2...v3.0.0">https://github.com/conda-incubator/setup-miniconda/compare/v2...v3.0.0</a></p>
<h2>Version 2.3.0</h2>
<h3>Documentation</h3>
<ul>
<li><a href="">#263</a> Update links to GitHub shell docs</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/conda-incubator/setup-miniconda/blob/main/CHANGELOG.md">conda-incubator/setup-miniconda's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/conda-incubator/setup-miniconda/releases/tag/v3.0.1">v3.0.1</a> (2023-11-29)</h2>
<h3>Fixes</h3>
<ul>
<li><a href="">#325</a> Fix environment activation on windows (a v3 regression) due to
hard-coded install PATH</li>
</ul>
<p><a href="">#325</a>: <a href="">conda-incubator/setup-miniconda#325</a></p>
<h2><a href="https://github.com/conda-incubator/setup-miniconda/releases/tag/v3.0.0">v3.0.0</a> (2023-11-27)</h2>
<h3>Features</h3>
<ul>
<li><a href="">#308</a> Update to node20</li>
<li><a href="">#291</a> Add conda-solver option (defaults to libmamba)</li>
</ul>
<h3>Fixes</h3>
<ul>
<li><a href="">#299</a> Fix condaBasePath when useBundled is false, and there's no pre-existing
conda</li>
</ul>
<h3>Documentation</h3>
<ul>
<li><a href="">#309</a> Switch to main branch based development</li>
<li><a href="">#313</a> Specify team conda-incubator/setup-miniconda as codeowners</li>
<li><a href="">#318</a> README: update actions in examples, add security section, similar
actions</li>
</ul>
<h3>Tasks and Maintenance</h3>
<ul>
<li><a href="">#307</a> Run dependabot against main branch and also update node packages</li>
<li><a href="">#311</a> Bump actions/checkout from 2 to 4</li>
<li><a href="">#310</a> Bump actions/cache from 1 to 3</li>
<li><a href="">#314</a> Strip/update dependencies</li>
<li><a href="">#315</a> Split lint into check and build, switch from <code>npm install</code> to <code>npm ci</code></li>
<li><a href="">#317</a> Bump normalize-url from 4.5.1 to 8.0.0</li>
<li><a href="">#316</a> Faster workflow response / saving resources via timeout/concurrency
policy</li>
</ul>
<p><a href="">#308</a>: <a href="">conda-incubator/setup-miniconda#308</a>
<a href="">#291</a>: <a href="">conda-incubator/setup-miniconda#291</a>
<a href="">#299</a>: <a href="">conda-incubator/setup-miniconda#299</a>
<a href="">#309</a>: <a href="">conda-incubator/setup-miniconda#309</a>
<a href="">#313</a>: <a href="">conda-incubator/setup-miniconda#313</a>
<a href="">#318</a>: <a href="">conda-incubator/setup-miniconda#318</a>
<a href="">#307</a>: <a href="">conda-incubator/setup-miniconda#307</a>
<a href="">#311</a>: <a href="">conda-incubator/setup-miniconda#311</a>
<a href="">#310</a>: <a href="">conda-incubator/setup-miniconda#310</a></p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>11b5629</code></a> Prepare 3.0.1 (<a href="">#326</a>)</li>
<li><a href=""><code>8706aa7</code></a> Fix env activation on win (a v3 regression) due to hard-coded install PATH (#...</li>
<li><a href=""><code>c585a97</code></a> Bump conda-incubator/setup-miniconda from 2.3.0 to 3.0.0 (<a href="">#321</a>)</li>
<li><a href=""><code>2defc80</code></a> Prepare release (<a href="">#320</a>)</li>
<li><a href=""><code>0d5a56b</code></a> Bump actions/checkout from 2 to 4 (<a href="">#319</a>)</li>
<li><a href=""><code>45fd3f9</code></a> Merge pull request <a href="">#316</a> from dbast/timeout</li>
<li><a href=""><code>d1e04fc</code></a> Merge pull request <a href="">#299</a> from isuruf/condaBasePath</li>
<li><a href=""><code>fab0073</code></a> Merge pull request <a href="">#318</a> from dbast/readme</li>
<li><a href=""><code>fa6bdf9</code></a> Update with npm run build</li>
<li><a href=""><code>d42f8b8</code></a> Fix condaBasePath when useBundled is false, and there's no pre-existing conda</li>
<li>Additional commits viewable in <a href="https://github.com/conda-incubator/setup-miniconda/compare/v2...v3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=conda-incubator/setup-miniconda&package-manager=github_actions&previous-version=2&new-version=3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4934c213af02`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
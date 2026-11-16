# Issue

**Title:** Bump urllib3 from 1.26.3 to 1.26.5

## Description

Bumps [urllib3](https://github.com/urllib3/urllib3) from 1.26.3 to 1.26.5.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/urllib3/urllib3/releases">urllib3's releases</a>.</em></p>
<blockquote>
<h2>1.26.5</h2>
<p>:warning: <strong>IMPORTANT: urllib3 v2.0 will drop support for Python 2</strong>: <a href="https://urllib3.readthedocs.io/en/latest/v2-roadmap.html">Read more in the v2.0 Roadmap</a></p>
<ul>
<li>Fixed deprecation warnings emitted in Python 3.10.</li>
<li>Updated vendored <code>six</code> library to 1.16.0.</li>
<li>Improved performance of URL parser when splitting the authority component.</li>
</ul>
<p><strong>If you or your organization rely on urllib3 consider supporting us via <a href="https://github.com/sponsors/urllib3">GitHub Sponsors</a></strong></p>
<h2>1.26.4</h2>
<p>:warning: <strong>IMPORTANT: urllib3 v2.0 will drop support for Python 2</strong>: <a href="https://urllib3.readthedocs.io/en/latest/v2-roadmap.html">Read more in the v2.0 Roadmap</a></p>
<ul>
<li>Changed behavior of the default <code>SSLContext</code> when connecting to HTTPS proxy during HTTPS requests. The default <code>SSLContext</code> now sets <code>check_hostname=True</code>.</li>
</ul>
<p><strong>If you or your organization rely on urllib3 consider supporting us via <a href="https://github.com/sponsors/urllib3">GitHub Sponsors</a></strong></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/urllib3/urllib3/blob/main/CHANGES.rst">urllib3's changelog</a>.</em></p>
<blockquote>
<h1>1.26.5 (2021-05-26)</h1>
<ul>
<li>Fixed deprecation warnings emitted in Python 3.10.</li>
<li>Updated vendored <code>six</code> library to 1.16.0.</li>
<li>Improved performance of URL parser when splitting
the authority component.</li>
</ul>
<h1>1.26.4 (2021-03-15)</h1>
<ul>
<li>Changed behavior of the default <code>SSLContext</code> when connecting to HTTPS proxy
during HTTPS requests. The default <code>SSLContext</code> now sets <code>check_hostname=True</code>.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d161647</code></a> Release 1.26.5</li>
<li><a href=""><code>2d4a3fe</code></a> Improve performance of sub-authority splitting in URL</li>
<li><a href=""><code>2698537</code></a> Update vendored six to 1.16.0</li>
<li><a href=""><code>07bed79</code></a> Fix deprecation warnings for Python 3.10 ssl module</li>
<li><a href=""><code>d725a9b</code></a> Add Python 3.10 to GitHub Actions</li>
<li><a href=""><code>339ad34</code></a> Use pytest==6.2.4 on Python 3.10+</li>
<li><a href=""><code>f271c9c</code></a> Apply latest Black formatting</li>
<li><a href=""><code>1884878</code></a> [1.26] Properly proxy EOF on the SSLTransport test suite</li>
<li><a href=""><code>a891304</code></a> Release 1.26.4</li>
<li><a href=""><code>8d65ea1</code></a> Merge pull request from GHSA-5phf-pp7p-vc2r</li>
<li>Additional commits viewable in <a href="https://github.com/urllib3/urllib3/compare/1.26.3...1.26.5">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=urllib3&package-manager=pip&previous-version=1.26.3&new-version=1.26.5)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot use these labels` will set the current labels as the default for future PRs for this repo and language
- `@dependabot use these reviewers` will set the current reviewers as the default for future PRs for this repo and language
- `@dependabot use these assignees` will set the current assignees as the default for future PRs for this repo and language
- `@dependabot use this milestone` will set the current milestone as the default for future PRs for this repo and language

You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/AstraZeneca/kallisto/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b9a649882f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
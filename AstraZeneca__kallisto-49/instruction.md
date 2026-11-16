# Issue

**Title:** Bump urllib3 from 2.0.4 to 2.0.7

## Description

Bumps [urllib3](https://github.com/urllib3/urllib3) from 2.0.4 to 2.0.7.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/urllib3/urllib3/releases">urllib3's releases</a>.</em></p>
<blockquote>
<h2>2.0.7</h2>
<ul>
<li>Made body stripped from HTTP requests changing the request method to GET after HTTP 303 &quot;See Other&quot; redirect responses. (GHSA-g4mx-q9vg-27p4)</li>
</ul>
<h2>2.0.6</h2>
<ul>
<li>Added the <code>Cookie</code> header to the list of headers to strip from requests when redirecting to a different host. As before, different headers can be set via <code>Retry.remove_headers_on_redirect</code>. (GHSA-v845-jxx5-vc9f)</li>
</ul>
<h2>2.0.5</h2>
<ul>
<li>Allowed pyOpenSSL third-party module without any deprecation warning. <a href="">#3126</a></li>
<li>Fixed default <code>blocksize</code> of <code>HTTPConnection</code> classes to match high-level classes. Previously was 8KiB, now 16KiB. <a href="">#3066</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/urllib3/urllib3/blob/main/CHANGES.rst">urllib3's changelog</a>.</em></p>
<blockquote>
<h1>2.0.7 (2023-10-17)</h1>
<ul>
<li>Made body stripped from HTTP requests changing the request method to GET after HTTP 303 &quot;See Other&quot; redirect responses.</li>
</ul>
<h1>2.0.6 (2023-10-02)</h1>
<ul>
<li>Added the <code>Cookie</code> header to the list of headers to strip from requests when redirecting to a different host. As before, different headers can be set via <code>Retry.remove_headers_on_redirect</code>.</li>
</ul>
<h1>2.0.5 (2023-09-20)</h1>
<ul>
<li>Allowed pyOpenSSL third-party module without any deprecation warning. (<code> &lt;</code>__)</li>
<li>Fixed default <code>blocksize</code> of <code>HTTPConnection</code> classes to match high-level classes. Previously was 8KiB, now 16KiB. (<code> &lt;</code>__)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>56f01e0</code></a> Release 2.0.7</li>
<li><a href=""><code>4e50fbc</code></a> Merge pull request from GHSA-g4mx-q9vg-27p4</li>
<li><a href=""><code>80808b0</code></a> Fix docs build on Python 3.12 (<a href="">#3144</a>)</li>
<li><a href=""><code>f28deff</code></a> Add 1.26.17 to the current changelog</li>
<li><a href=""><code>262e3e3</code></a> Release 2.0.6</li>
<li><a href=""><code>644124e</code></a> Merge pull request from GHSA-v845-jxx5-vc9f</li>
<li><a href=""><code>740380c</code></a> Bump cryptography from 41.0.3 to 41.0.4 (<a href="">#3131</a>)</li>
<li><a href=""><code>d9f85a7</code></a> Release 2.0.5</li>
<li><a href=""><code>d41f412</code></a> Undeprecate pyOpenSSL module (<a href="">#3127</a>)</li>
<li><a href=""><code>b6c04cb</code></a> Fix a link to &quot;absolute URI&quot; definition (<a href="">#3128</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/urllib3/urllib3/compare/2.0.4...2.0.7">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=urllib3&package-manager=pip&previous-version=2.0.4&new-version=2.0.7)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/AstraZeneca/kallisto/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c1179f3969b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
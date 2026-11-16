# Issue

**Title:** Bump axios from 1.12.0 to 1.15.2 in /utils/indigo-service/frontend/ui

## Description

Bumps [axios](https://github.com/axios/axios) from 1.12.0 to 1.15.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/axios/axios/releases">axios's releases</a>.</em></p>
<blockquote>
<h2>v1.15.2</h2>
<p>This release delivers prototype-pollution hardening for the Node HTTP adapter, adds an opt-in <code>allowedSocketPaths</code> allowlist to mitigate SSRF via Unix domain sockets, fixes a keep-alive socket memory leak, and ships supply-chain hardening across CI and security docs.</p>
<h2>🔒 Security Fixes</h2>
<ul>
<li><strong>Prototype Pollution Hardening (HTTP Adapter):</strong> Hardened the Node HTTP adapter and <code>resolveConfig</code>/<code>mergeConfig</code>/validator paths to read only own properties and use null-prototype config objects, preventing polluted <code>auth</code>, <code>baseURL</code>, <code>socketPath</code>, <code>beforeRedirect</code>, and <code>insecureHTTPParser</code> from influencing requests. (<strong><a href="">#10779</a></strong>)</li>
<li><strong>SSRF via <code>socketPath</code>:</strong> Rejects non-string <code>socketPath</code> values and adds an opt-in <code>allowedSocketPaths</code> config option to restrict permitted Unix domain socket paths, returning <code>AxiosError</code> <code>ERR_BAD_OPTION_VALUE</code> on mismatch. (<strong><a href="">#10777</a></strong>)</li>
<li><strong>Supply-chain Hardening:</strong> Added <code>.npmrc</code> with <code>ignore-scripts=true</code>, lockfile lint CI, non-blocking reproducible build diff, scoped CODEOWNERS, expanded <code>SECURITY.md</code>/<code>THREATMODEL.md</code> with provenance verification (<code>npm audit signatures</code>), 60-day resolution policy, and maintainer incident-response runbook. (<strong><a href="">#10776</a></strong>)</li>
</ul>
<h2>🚀 New Features</h2>
<ul>
<li><strong><code>allowedSocketPaths</code> Config Option:</strong> New request config option (and TypeScript types) to allowlist Unix domain socket paths used by the Node http adapter; backwards compatible when unset. (<strong><a href="">#10777</a></strong>)</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li><strong>Keep-alive Socket Memory Leak:</strong> Installs a single per-socket <code>error</code> listener tracking the active request via <code>kAxiosSocketListener</code>/<code>kAxiosCurrentReq</code>, eliminating per-request listener accumulation, <code>MaxListenersExceededWarning</code>, and linear heap growth under concurrent or long-running keep-alive workloads (fixes <a href="">#10780</a>). (<strong><a href="">#10788</a></strong>)</li>
</ul>
<h2>🔧 Maintenance &amp; Chores</h2>
<ul>
<li><strong>Changelog:</strong> Updated <code>CHANGELOG.md</code> with v1.15.1 release notes. (<strong><a href="">#10781</a></strong>)</li>
</ul>
<p><a href="https://github.com/axios/axios/compare/v1.15.1...v1.15.2">Full Changelog</a></p>
<h2>v1.15.1</h2>
<p>This release ships a coordinated set of security hardening fixes across headers, body/redirect limits, multipart handling, and XSRF/prototype-pollution vectors, alongside a broad sweep of bug fixes, test migrations, and threat-model documentation updates.</p>
<h2>🔒 Security Fixes</h2>
<ul>
<li><strong>Header Injection Hardening:</strong> Tightened validation and sanitisation across request header construction to close the header-injection attack surface. (<strong><a href="">#10749</a></strong>)</li>
<li><strong>CRLF Stripping in Multipart Headers:</strong> Correctly strips CR/LF from multipart header values to prevent injection via field names and filenames. (<strong><a href="">#10758</a></strong>)</li>
<li><strong>Prototype Pollution / Auth Bypass:</strong> Replaced unsafe <code>in</code> checks with <code>hasOwnProperty</code> to prevent authentication bypass via prototype pollution on config objects, with additional regression tests. (<strong><a href="">#10761</a></strong>, <strong><a href="">#10760</a></strong>)</li>
<li><strong><code>withXSRFToken</code> Truthy Bypass:</strong> Short-circuits on any truthy non-boolean value, so an ambiguous config no longer silently leaks the XSRF token cross-origin. (<strong><a href="">#10762</a></strong>)</li>
<li><strong><code>maxBodyLength</code> With Zero Redirects:</strong> Enforces <code>maxBodyLength</code> even when <code>maxRedirects</code> is set to <code>0</code>, closing a bypass path for oversized request bodies. (<strong><a href="">#10753</a></strong>)</li>
<li><strong>Streamed Response <code>maxContentLength</code> Bypass:</strong> Applies <code>maxContentLength</code> to streamed responses that previously bypassed the cap. (<strong><a href="">#10754</a></strong>)</li>
<li><strong>Follow-up CVE Completion:</strong> Completes an earlier incomplete CVE fix to fully close the regression window. (<strong><a href="">#10755</a></strong>)</li>
</ul>
<h2>🚀 New Features</h2>
<ul>
<li><strong>AI-Based Docs Translations:</strong> Initial scaffold for AI-assisted translations of the documentation site. (<strong><a href="">#10705</a></strong>)</li>
<li><strong><code>Location</code> Request Header Type:</strong> Adds <code>Location</code> to <code>CommonRequestHeadersList</code> for accurate typing of redirect-aware requests. (<strong><a href="">#7528</a></strong>)</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li><strong>FormData Handling:</strong> Removes <code>Content-Type</code> when no boundary is present on <code>FormData</code> fetch requests, supports multi-select fields, cancels <code>request.body</code> instead of the source stream on fetch abort, and fixes a recursion bug in form-data serialisation. (<strong><a href="">#7314</a></strong>, <strong><a href="">#10676</a></strong>, <strong><a href="">#10702</a></strong>, <strong><a href="">#10726</a></strong>)</li>
<li><strong>HTTP Adapter:</strong> Handles socket-only request errors without leaking keep-alive listeners. (<strong><a href="">#10576</a></strong>)</li>
<li><strong>Progress Events:</strong> Clamps <code>loaded</code> to <code>total</code> for computable upload/download progress events. (<strong><a href="">#7458</a></strong>)</li>
<li><strong>Types:</strong> Aligns <code>runWhen</code> type with the runtime behaviour in <code>InterceptorManager</code> and makes response header keys case-insensitive. (<strong><a href="">#7529</a></strong>, <strong><a href="">#10677</a></strong>)</li>
<li><strong><code>buildFullPath</code>:</strong> Uses strict equality in the base/relative URL check. (<strong><a href="">#7252</a></strong>)</li>
<li><strong><code>AxiosURLSearchParams</code> Regex:</strong> Improves the regex used for param serialisation to avoid edge-case mismatches. (<strong><a href="">#10736</a></strong>)</li>
<li><strong>Resilient Value Parsing:</strong> Parses out header/config values instead of throwing on malformed input. (<strong><a href="">#10687</a></strong>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/axios/axios/blob/v1.x/CHANGELOG.md">axios's changelog</a>.</em></p>
<blockquote>
<h2>v1.15.2 - April 21, 2026</h2>
<p>This release delivers prototype-pollution hardening for the Node HTTP adapter, adds an opt-in <code>allowedSocketPaths</code> allowlist to mitigate SSRF via Unix domain sockets, fixes a keep-alive socket memory leak, and ships supply-chain hardening across CI and security docs.</p>
<h2>🔒 Security Fixes</h2>
<ul>
<li><strong>Prototype Pollution Hardening (HTTP Adapter):</strong> Hardened the Node HTTP adapter and <code>resolveConfig</code>/<code>mergeConfig</code>/validator paths to read only own properties and use null-prototype config objects, preventing polluted <code>auth</code>, <code>baseURL</code>, <code>socketPath</code>, <code>beforeRedirect</code>, and <code>insecureHTTPParser</code> from influencing requests. (<strong><a href="">#10779</a></strong>)</li>
<li><strong>SSRF via <code>socketPath</code>:</strong> Rejects non-string <code>socketPath</code> values and adds an opt-in <code>allowedSocketPaths</code> config option to restrict permitted Unix domain socket paths, returning <code>AxiosError</code> <code>ERR_BAD_OPTION_VALUE</code> on mismatch. (<strong><a href="">#10777</a></strong>)</li>
<li><strong>Supply-chain Hardening:</strong> Added <code>.npmrc</code> with <code>ignore-scripts=true</code>, lockfile lint CI, non-blocking reproducible build diff, scoped CODEOWNERS, expanded <code>SECURITY.md</code>/<code>THREATMODEL.md</code> with provenance verification (<code>npm audit signatures</code>), 60-day resolution policy, and maintainer incident-response runbook. (<strong><a href="">#10776</a></strong>)</li>
</ul>
<h2>🚀 New Features</h2>
<ul>
<li><strong><code>allowedSocketPaths</code> Config Option:</strong> New request config option (and TypeScript types) to allowlist Unix domain socket paths used by the Node http adapter; backwards compatible when unset. (<strong><a href="">#10777</a></strong>)</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li><strong>Keep-alive Socket Memory Leak:</strong> Installs a single per-socket <code>error</code> listener tracking the active request via <code>kAxiosSocketListener</code>/<code>kAxiosCurrentReq</code>, eliminating per-request listener accumulation, <code>MaxListenersExceededWarning</code>, and linear heap growth under concurrent or long-running keep-alive workloads (fixes <a href="">#10780</a>). (<strong><a href="">#10788</a></strong>)</li>
</ul>
<h2>🔧 Maintenance &amp; Chores</h2>
<ul>
<li><strong>Changelog:</strong> Updated <code>CHANGELOG.md</code> with v1.15.1 release notes. (<strong><a href="">#10781</a></strong>)</li>
</ul>
<p><a href="https://github.com/axios/axios/compare/v1.15.1...v1.15.2">Full Changelog</a></p>
<hr />
<h2>v1.15.1 - April 19, 2026</h2>
<p>This release ships a coordinated set of security hardening fixes across headers, body/redirect limits, multipart handling, and XSRF/prototype-pollution vectors, alongside a broad sweep of bug fixes, test migrations, and threat-model documentation updates.</p>
<h2>🔒 Security Fixes</h2>
<ul>
<li>
<p><strong>Header Injection Hardening:</strong> Tightened validation and sanitisation across request header construction to close the header-injection attack surface. (<strong><a href="">#10749</a></strong>)</p>
</li>
<li>
<p><strong>CRLF Stripping in Multipart Headers:</strong> Correctly strips CR/LF from multipart header values to prevent injection via field names and filenames. (<strong><a href="">#10758</a></strong>)</p>
</li>
<li>
<p><strong>Prototype Pollution / Auth Bypass:</strong> Replaced unsafe <code>in</code> checks with <code>hasOwnProperty</code> to prevent authentication bypass via prototype pollution on config objects, with additional regression tests. (<strong><a href="">#10761</a></strong>, <strong><a href="">#10760</a></strong>)</p>
</li>
<li>
<p><strong><code>withXSRFToken</code> Truthy Bypass:</strong> Short-circuits on any truthy non-boolean value, so an ambiguous config no longer silently leaks the XSRF token cross-origin. (<strong><a href="">#10762</a></strong>)</p>
</li>
<li>
<p><strong><code>maxBodyLength</code> With Zero Redirects:</strong> Enforces <code>maxBodyLength</code> even when <code>maxRedirects</code> is set to <code>0</code>, closing a bypass path for oversized request bodies. (<strong><a href="">#10753</a></strong>)</p>
</li>
<li>
<p><strong>Streamed Response <code>maxContentLength</code> Bypass:</strong> Applies <code>maxContentLength</code> to streamed responses that previously bypassed the cap. (<strong><a href="">#10754</a></strong>)</p>
</li>
<li>
<p><strong>Follow-up CVE Completion:</strong> Completes an earlier incomplete CVE fix to fully close the regression window. (<strong><a href="">#10755</a></strong>)</p>
</li>
</ul>
<h2>🚀 New Features</h2>
<ul>
<li><strong>AI-Based Docs Translations:</strong> Initial scaffold for AI-assisted translations of the documentation site. (<strong><a href="">#10705</a></strong>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5829343</code></a> chore(release): prepare release 1.15.2 (<a href="">#10789</a>)</li>
<li><a href=""><code>4709a48</code></a> fix: added fix for memory leak in sockets (<a href="">#10788</a>)</li>
<li><a href=""><code>be33360</code></a> chore: update changelog (<a href="">#10781</a>)</li>
<li><a href=""><code>4791514</code></a> fix: more header pollutions (<a href="">#10779</a>)</li>
<li><a href=""><code>6feafcf</code></a> fix: socket issue (<a href="">#10777</a>)</li>
<li><a href=""><code>302e273</code></a> docs: update docs, add a couple actions etc (<a href="">#10776</a>)</li>
<li><a href=""><code>ac42446</code></a> chore(release): prepare release 1.15.1 (<a href="">#10767</a>)</li>
<li><a href=""><code>908f220</code></a> docs: update threatmodel (<a href="">#10765</a>)</li>
<li><a href=""><code>f93f815</code></a> docs: added docs around potential decompressions bomb (<a href="">#10763</a>)</li>
<li><a href=""><code>1728aa1</code></a> fix: short-circuits on any truthy non-boolean in withXSRFToken (<a href="">#10762</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/axios/axios/compare/v1.12.0...v1.15.2">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~GitHub%20Actions">GitHub Actions</a>, a new releaser for axios since your current version.</p>
</details>
<details>
<summary>Install script changes</summary>
<p>This version modifies <code>prepare</code> script that runs during installation. Review the package contents before updating.</p>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=axios&package-manager=npm_and_yarn&previous-version=1.12.0&new-version=1.15.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/epam/Indigo/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c639caae8f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
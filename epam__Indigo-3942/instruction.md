# Issue

**Title:** Bump axios from 1.18.0 to 1.20.0 in /utils/indigo-service/frontend/ui

## Description

Bumps [axios](https://github.com/axios/axios) from 1.18.0 to 1.20.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/axios/axios/releases">axios's releases</a>.</em></p>
<blockquote>
<h2>v1.20.0 — August 19, 2026</h2>
<p>This release hardens runtime option handling, adds RFC 9110 status-code aliases, fixes Node.js and XHR reliability issues, and refreshes project tooling and documentation.</p>
<h2>⚠️ Breaking Changes &amp; Deprecations</h2>
<ul>
<li>HTTP Status Naming: Added ContentTooLarge (413) and UnprocessableContent (422), while retaining PayloadTooLarge and UnprocessableEntity as backward-compatible deprecated aliases. (<a href="">#11082</a>)</li>
</ul>
<h2>🔒 Security Fixes</h2>
<ul>
<li>Runtime Option Handling: Hardened behavioral configuration reads against shared and foreign prototype pollution and normalized unsafe interceptor replacement objects. This also clarifies Fetch redirect and custom implementation behavior, HTTP/2 DNS and proxy handling, CIDR-based NO_PROXY matching, and malformed data URI rejection; see the PR for documented compatibility effects. (<a href="">#11141</a>)</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li>Interceptor Lifecycle: Prevented unbounded handler-array growth by trimming trailing ejected interceptors without changing iteration semantics, and kept interceptor operations safe when the public handlers field is nullish. (<a href="">#11087</a>, <a href="">#11118</a>)</li>
<li>Request Error Preservation: Prevented custom Error.prepareStackTrace implementations that return non-string values from replacing the original request failure with an unrelated TypeError. (<a href="">#11109</a>)</li>
<li>XHR Reliability: Navigation-canceled requests now reject with ECONNABORTED instead of resolving with status 0, while successful downloads flush their final progress callback during the live loadend dispatch. (<a href="">#11094</a>, <a href="">#11121</a>)</li>
<li>Node.js Socket Memory: Removed request-context retention from per-socket error listeners, preventing completed response data from being pinned for the lifetime of pooled keep-alive sockets. (<a href="">#11091</a>)</li>
<li>Core Methods and HTTP Errors: Prevented structural method-header buckets from leaking into outgoing headers, standardized invalid DNS lookup and httpVersion failures as AxiosError.ERR_BAD_OPTION_VALUE, and corrected the timeoutErrorMessage merge strategy. (<a href="">#11096</a>)</li>
</ul>
<h2>🔧 Maintenance &amp; Chores</h2>
<ul>
<li>Dependencies: Updated fast-uri, postcss, js-yaml, mocha, development-tooling groups, and GitHub Actions dependencies. (<a href="">#11092</a>, <a href="">#11098</a>, <a href="">#11099</a>, <a href="">#11106</a>, <a href="">#11107</a>, <a href="">#11122</a>, <a href="">#11123</a>, <a href="">#11126</a>, <a href="">#11127</a>, <a href="">#11133</a>, <a href="">#11140</a>, <a href="">#11143</a>, <a href="">#11144</a>)</li>
<li>Documentation: Applied the v1.19.0 documentation updates, added the missing fs import to the README stream example, introduced localized global search, and repaired the interceptor test link. (<a href="">#11101</a>, <a href="">#11113</a>, <a href="">#11097</a>, <a href="">#11119</a>)</li>
<li>Sponsorship: Updated sponsorship links and data and added ScrapingBee as a sponsor. (<a href="">#11124</a>, <a href="">#11136</a>, <a href="">#11137</a>)</li>
<li>CI and Release: Switched ESM smoke tests to locked dependencies and synchronized package and runtime version metadata for v1.20.0. (<a href="">#11128</a>, <a href="">#11152</a>)</li>
</ul>
<h2>🌟 New Contributors</h2>
<p>We are thrilled to welcome our new contributors. Thank you for helping improve axios:</p>
<ul>
<li><a href="https://github.com/yens1"><code>@​yens1</code></a> (<a href="">#11109</a>)</li>
<li><a href="https://github.com/Sasireddy001"><code>@​Sasireddy001</code></a> (<a href="">#11113</a>)</li>
<li><a href="https://github.com/ari-token-security"><code>@​ari-token-security</code></a> (<a href="">#11094</a>)</li>
<li><a href="https://github.com/timothyokooboh"><code>@​timothyokooboh</code></a> (<a href="">#11097</a>)</li>
<li><a href="https://github.com/gi9439041-png"><code>@​gi9439041-png</code></a> (<a href="">#11119</a>)</li>
<li><a href="https://github.com/Hashim1999164"><code>@​Hashim1999164</code></a> (<a href="">#11082</a>)</li>
<li><a href="https://github.com/v-dev-cl"><code>@​v-dev-cl</code></a> (<a href="">#11091</a>)</li>
<li><a href="https://github.com/r0h1tb"><code>@​r0h1tb</code></a> (<a href="">#11118</a>)</li>
<li><a href="https://github.com/ostapondo"><code>@​ostapondo</code></a> (<a href="">#11121</a>)</li>
</ul>
<p>Full Changelog (<a href="https://github.com/axios/axios/compare/v1.19.0...v1.20.0">https://github.com/axios/axios/compare/v1.19.0...v1.20.0</a>)</p>
<h2>v1.19.0 - July 22, 2026</h2>
<p>This release raises the form-data security floor, adds configuration and type-system capabilities, and fixes NO_PROXY matching, interceptor errors, progress reporting, and serialization edge cases.</p>
<h2>🔒 Security Fixes</h2>
<ul>
<li>Multipart Form Data: Raised the form-data dependency floor to ^4.0.6, preventing fresh installations from resolving versions affected by the CRLF injection vulnerability GHSA-hmw2-7cc7-3qxx (<a href="https://github.com/advisories/GHSA-hmw2-7cc7-3qxx">https://github.com/advisories/GHSA-hmw2-7cc7-3qxx</a>). (<a href="">#11028</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/axios/axios/blob/v1.x/CHANGELOG.md">axios's changelog</a>.</em></p>
<blockquote>
<h1>Changelog</h1>
<h2>v1.19.0 — July 22, 2026</h2>
<p>This release raises the form-data security floor, adds configuration and type-system capabilities, and fixes NO_PROXY matching, interceptor errors, progress reporting, and serialization edge cases.</p>
<h2>🔒 Security Fixes</h2>
<ul>
<li>Multipart Form Data: Raised the form-data dependency floor to ^4.0.6, preventing fresh installations from resolving versions affected by the CRLF injection vulnerability GHSA-hmw2-7cc7-3qxx (<a href="https://github.com/advisories/GHSA-hmw2-7cc7-3qxx">https://github.com/advisories/GHSA-hmw2-7cc7-3qxx</a>). (<a href="">#11028</a>)</li>
</ul>
<h2>🚀 New Features</h2>
<ul>
<li>Configuration Extensibility: Preserved own-enumerable symbol-keyed fields through mergeConfig and added a generic params type across public TypeScript declarations, responses, errors,
adapters, and serializers. (<a href="">#11043</a>, <a href="">#11081</a>)</li>
<li>Header Parameter Parsing: Added the opt-in AxiosHeaders.parseParameters() parser for quote-aware, RFC-style HTTP parameter parsing while preserving legacy parsing behavior. (<a href="">#11051</a>)</li>
<li>HTTP Status Codes: Added the missing Cloudflare 520 WebServerReturnsAnUnknownError status and matching ESM/CJS declarations. (<a href="">#11067</a>)</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li>
<p>Form Data Conversion: Limited formDataToJSON path splitting to dot and bracket notation, preserving literal punctuation in keys, and removed browser-facing Buffer.from usage from toFormData to avoid unnecessary polyfills. (<a href="">#11006</a>, <a href="">#11018</a>)</p>
</li>
<li>
<p>Proxy Bypass: Canonicalized IPv4 shorthand, octal, and hexadecimal forms during NO_PROXY matching and honored * entries within comma- or space-separated bypass lists. (<a href="">#11029</a>, <a href="">#11053</a>)</p>
</li>
<li>
<p>Cancellation: Propagated already-aborted input signals immediately when composing abort signals. (<a href="">#11035</a>)</p>
</li>
<li>
<p>Header Handling: Preserved empty first values for duplicate singleton headers and made AxiosHeaders#getSetCookie() consistently return arrays for present values. (<a href="">#11036</a>, <a href="">#11037</a>)</p>
</li>
<li>
<p>URL Handling: Included normalized, safely redacted offending URLs in malformed-protocol errors and removed repeated trailing slashes when combining base URLs. (<a href="">#11008</a>, <a href="">#11038</a>)</p>
</li>
<li>
<p>Progress Events: Clamped malformed negative progress values to zero and ensured final Node.js download progress events are delivered before streamed responses close. (<a href="">#11039</a>, <a href="">#11040</a>)</p>
</li>
<li>
<p>Error and JSON Serialization: Serialized Set values as arrays in JSON-compatible snapshots and synthesized useful AxiosError messages from otherwise-empty AggregateError instances. (<a href="">#11044</a>, <a href="">#11059</a>)</p>
</li>
<li>
<p>Content-Length Enforcement: Corrected base64 data: URL size estimation so maxContentLength is enforced consistently by the HTTP and Fetch adapters. (<a href="">#11061</a>)</p>
</li>
<li>
<p>Synchronous Interceptors: Prevented requests from being dispatched after synchronous request interceptors fail unless their paired rejection handler resolves successfully. (<a href="">#11071</a>)</p>
</li>
</ul>
<h2>🔧 Maintenance &amp; Chores</h2>
<ul>
<li>Dependencies: Updated development and test tooling, the docs fixture's Axios version, and GitHub Actions integrations including Checkout, Setup Node, Setup Deno, and Zizmor. (<a href="">#11031</a>, <a href="">#11055</a>, <a href="">#11056</a>, <a href="">#11058</a>, <a href="">#11079</a>, <a href="">#11080</a>, <a href="">#11088</a>, <a href="">#11089</a>, <a href="">#11090</a>)</li>
<li>Build Outputs: Limited sourcemap generation to published minified bundles, removing broken map references from non-minified builds. (<a href="">#11054</a>)</li>
<li>Form Data Internals: Centralized FormData header handling and made the Node.js adapter tolerate getHeaders() returning undefined under the content-only policy. (<a href="">#11062</a>)</li>
<li>Developer Experience: Ignored common local AI-tooling directories and fixed a constant-reassignment crash when the development sandbox serves its root path. (<a href="">#11032</a>, <a href="">#11073</a>)</li>
<li>Documentation: Updated sponsor information, clarified that baseURL is not a path-security boundary, scoped provenance claims to attested releases, and corrected the configuration-defaults documentation. (<a href="">#11041</a>, <a href="">#11068</a>, <a href="">#11076</a>, <a href="">#11078</a>)</li>
<li>Publishing: Simplified v1 publishing to use the npm version bundled with Node.js 26 and updated package metadata for the 1.19.0 release. (<a href="">#11083</a>, <a href="">#11095</a>)</li>
</ul>
<h2>🌟 New Contributors</h2>
<p>We are thrilled to welcome our new contributors. Thank you for helping improve Axios:</p>
<ul>
<li><a href="https://github.com/afonsojramos"><code>@​afonsojramos</code></a> (<a href="">#11028</a>)</li>
<li><a href="https://github.com/MahinAnowar"><code>@​MahinAnowar</code></a> (<a href="">#11006</a>)</li>
<li><a href="https://github.com/yassertawfik4"><code>@​yassertawfik4</code></a> (<a href="">#11024</a>)</li>
<li><a href="https://github.com/AnandSundar"><code>@​AnandSundar</code></a> (<a href="">#11029</a>)</li>
<li><a href="https://github.com/lin-hongkuan"><code>@​lin-hongkuan</code></a> (<a href="">#11035</a>)</li>
<li><a href="https://github.com/Wali007-lab"><code>@​Wali007-lab</code></a> (<a href="">#11054</a>)</li>
<li><a href="https://github.com/magicdawn"><code>@​magicdawn</code></a> (<a href="">#11043</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>84a9f3b</code></a> chore(release): prepare release 1.20.0 (<a href="">#11152</a>)</li>
<li><a href=""><code>e6824ee</code></a> fix: core methodList, HTTP adapter errors, and add tests (<a href="">#11096</a>)</li>
<li><a href=""><code>d8a919f</code></a> fix(xhr): flush final progress during the live loadend dispatch (<a href="">#11121</a>)</li>
<li><a href=""><code>2d2a21a</code></a> fix(interceptors): tolerate nullish handlers in syncHandlerEntries (<a href="">#11118</a>)</li>
<li><a href=""><code>d19040b</code></a> fix: harden runtime option handling (<a href="">#11141</a>)</li>
<li><a href=""><code>e0a02dd</code></a> chore(deps): bump zizmorcore/zizmor-action from 0.6.1 to 0.6.2 in the github-...</li>
<li><a href=""><code>d10cb3a</code></a> chore(deps-dev): bump the development_dependencies group with 4 updates (<a href="">#11143</a>)</li>
<li><a href=""><code>2c94646</code></a> chore(deps): bump js-yaml and mocha in /tests/smoke/cjs (<a href="">#11133</a>)</li>
<li><a href=""><code>76c12bc</code></a> chore(deps-dev): bump js-yaml from 4.3.0 to 4.3.1 (<a href="">#11140</a>)</li>
<li><a href=""><code>ba98559</code></a> docs: add ScrapingBee sponsor (<a href="">#11137</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/axios/axios/compare/v1.18.0...v1.20.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=axios&package-manager=npm_and_yarn&previous-version=1.18.0&new-version=1.20.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55ce330fab43`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
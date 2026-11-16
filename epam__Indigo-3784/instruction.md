# Issue

**Title:** Bump axios from 1.16.0 to 1.18.0 in /utils/indigo-service/frontend/ui

## Description

Bumps [axios](https://github.com/axios/axios) from 1.16.0 to 1.18.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/axios/axios/releases">axios's releases</a>.</em></p>
<blockquote>
<h2>v1.18.0 — June 13, 2026</h2>
<p>This release hardens redirect and URL handling, improves the validateStatus configuration semantics, and includes updates to documentation, dependencies, and release metadata.</p>
<h2>🔒 Security Fixes</h2>
<ul>
<li>
<p><strong>Redirect Header Safety:</strong> Added Node HTTP adapter support for stripping caller-specified sensitive headers on cross-origin redirects, helping prevent custom auth headers such as API keys from leaking to another origin. (<strong><a href="">#10892</a></strong>)</p>
</li>
<li>
<p><strong>URL And Request Hardening:</strong> Rejects malformed <code>http:</code> and <code>https:</code> URLs that omit <code>//</code> with <code>ERR_INVALID_URL</code>, while tightening prototype-pollution-safe config reads, stream size limits, FormData depth handling, data URL sizing, and local <code>NO_PROXY</code> matching. (<strong><a href="">#11000</a></strong>)</p>
</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li><strong>Status Validation:</strong> Added <code>transitional.validateStatusUndefinedResolves</code> so applications can opt in to treating <code>validateStatus: undefined</code> like the option was omitted, while <code>validateStatus: null</code> remains the explicit way to accept every status. (<strong><a href="">#10899</a></strong>)</li>
</ul>
<h2>🔧 Maintenance &amp; Chores</h2>
<ul>
<li>
<p><strong>Documentation:</strong> Published the v1.17.0 release notes, fixed a changelog typo, clarified the package update PR policy, and marked the <code>proxy</code> request config as Node.js-only in the advanced docs. (<strong><a href="">#10984</a></strong>, <strong><a href="">#10988</a></strong>, <strong><a href="">#10992</a></strong>, <strong><a href="">#10995</a></strong>)</p>
</li>
<li>
<p><strong>Dependencies:</strong> Bumped <code>@babel/core</code>, <code>@babel/preset-env</code>, <code>@commitlint/cli</code>, <code>@commitlint/config-conventional</code>, <code>@rollup/plugin-babel</code>, <code>@rollup/plugin-commonjs</code>, <code>@vitest/browser</code>, <code>@vitest/browser-playwright</code>, <code>eslint</code>, <code>lint-staged</code>, <code>rollup</code>, <code>vitest</code>, and <code>actions/checkout</code>. (<strong><a href="">#10989</a></strong>, <strong><a href="">#10996</a></strong>, <strong><a href="">#10997</a></strong>)</p>
</li>
<li>
<p><strong>Release Metadata:</strong> Prepared the 1.18.0 release by updating package metadata and the runtime <code>VERSION</code> value. (<strong><a href="">#11003</a></strong>)</p>
</li>
</ul>
<h2>🌟 New Contributors</h2>
<p>We are thrilled to welcome our new contributors. Thank you for helping improve axios:</p>
<ul>
<li><strong><a href="https://github.com/drori12"><code>@​drori12</code></a></strong> (<strong><a href="">#10984</a></strong>)</li>
<li><strong><a href="https://github.com/eyupcanakman"><code>@​eyupcanakman</code></a></strong> (<strong><a href="">#10899</a></strong>)</li>
<li><strong><a href="https://github.com/Adi-Beker"><code>@​Adi-Beker</code></a></strong> (<strong><a href="">#10995</a></strong>)</li>
</ul>
<p><a href="https://github.com/axios/axios/compare/v1.17.0...v1.18.0">Full Changelog</a></p>
<h2>v1.17.0 — June 1, 2026</h2>
<p>This release adds Node HTTP zstd decompression, hardens config and release workflows, and fixes authentication, header, proxy, and type-handling regressions.</p>
<h2>🔒 Security Fixes</h2>
<ul>
<li><strong>Config Hardening:</strong> Guarded <code>socketPath</code>, <code>params</code>, and <code>paramsSerializer</code> reads with own-property checks to prevent inherited prototype values from affecting request behavior, including SSRF-sensitive paths. (<strong><a href="">#10901</a></strong>, <strong><a href="">#10922</a></strong>)</li>
<li><strong>Release Publishing:</strong> Switched the publish workflow to npm staged publishing for safer, auditable package releases with provenance. (<strong><a href="">#10926</a></strong>)</li>
</ul>
<h2>🚀 New Features</h2>
<ul>
<li><strong>HTTP Compression:</strong> Added Node HTTP adapter support for zstd response decompression, with <code>transitional.advertiseZstdAcceptEncoding</code> controlling whether <code>zstd</code> is advertised in <code>Accept-Encoding</code>. (<strong><a href="">#6792</a></strong>, <strong><a href="">#10920</a></strong>)</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li><strong>Authentication Handling:</strong> Restored Basic auth on same-origin Node redirects while continuing to strip credentials cross-origin, and aligned the fetch adapter with HTTP adapter behavior for URL-embedded Basic auth. (<strong><a href="">#10929</a></strong>, <strong><a href="">#10896</a></strong>)</li>
<li><strong>Proxy TLS:</strong> Preserved user <code>httpsAgent</code> TLS options when tunneling HTTPS requests through HTTP CONNECT proxies. (<strong><a href="">#10957</a></strong>)</li>
<li><strong>React Native FormData:</strong> Cleared default <code>Content-Type</code> for React Native <code>FormData</code> so multipart boundaries can be generated correctly. (<strong><a href="">#10898</a></strong>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/axios/axios/blob/v1.x/CHANGELOG.md">axios's changelog</a>.</em></p>
<blockquote>
<h2>v1.18.0 — June 13, 2026</h2>
<p>This release hardens redirect and URL handling, improves the validateStatus configuration semantics, and includes updates to documentation, dependencies, and release metadata.</p>
<h2>🔒 Security Fixes</h2>
<ul>
<li>
<p><strong>Redirect Header Safety:</strong> Added Node HTTP adapter support for stripping caller-specified sensitive headers on cross-origin redirects, helping prevent custom auth headers such as API keys from leaking to another origin. (<strong><a href="">#10892</a></strong>)</p>
</li>
<li>
<p><strong>URL And Request Hardening:</strong> Rejects malformed <code>http:</code> and <code>https:</code> URLs that omit <code>//</code> with <code>ERR_INVALID_URL</code>, while tightening prototype-pollution-safe config reads, stream size limits, FormData depth handling, data URL sizing, and local <code>NO_PROXY</code> matching. (<strong><a href="">#11000</a></strong>)</p>
</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li><strong>Status Validation:</strong> Added <code>transitional.validateStatusUndefinedResolves</code> so applications can opt in to treating <code>validateStatus: undefined</code> like the option was omitted, while <code>validateStatus: null</code> remains the explicit way to accept every status. (<strong><a href="">#10899</a></strong>)</li>
</ul>
<h2>🔧 Maintenance &amp; Chores</h2>
<ul>
<li>
<p><strong>Documentation:</strong> Published the v1.17.0 release notes, fixed a changelog typo, clarified the package update PR policy, and marked the <code>proxy</code> request config as Node.js-only in the advanced docs. (<strong><a href="">#10984</a></strong>, <strong><a href="">#10988</a></strong>, <strong><a href="">#10992</a></strong>, <strong><a href="">#10995</a></strong>)</p>
</li>
<li>
<p><strong>Dependencies:</strong> Bumped <code>@babel/core</code>, <code>@babel/preset-env</code>, <code>@commitlint/cli</code>, <code>@commitlint/config-conventional</code>, <code>@rollup/plugin-babel</code>, <code>@rollup/plugin-commonjs</code>, <code>@vitest/browser</code>, <code>@vitest/browser-playwright</code>, <code>eslint</code>, <code>lint-staged</code>, <code>rollup</code>, <code>vitest</code>, and <code>actions/checkout</code>. (<strong><a href="">#10989</a></strong>, <strong><a href="">#10996</a></strong>, <strong><a href="">#10997</a></strong>)</p>
</li>
<li>
<p><strong>Release Metadata:</strong> Prepared the 1.18.0 release by updating package metadata and the runtime <code>VERSION</code> value. (<strong><a href="">#11003</a></strong>)</p>
</li>
</ul>
<h2>🌟 New Contributors</h2>
<p>We are thrilled to welcome our new contributors. Thank you for helping improve axios:</p>
<ul>
<li><strong><a href="https://github.com/drori12"><code>@​drori12</code></a></strong> (<strong><a href="">#10984</a></strong>)</li>
<li><strong><a href="https://github.com/eyupcanakman"><code>@​eyupcanakman</code></a></strong> (<strong><a href="">#10899</a></strong>)</li>
<li><strong><a href="https://github.com/Adi-Beker"><code>@​Adi-Beker</code></a></strong> (<strong><a href="">#10995</a></strong>)</li>
</ul>
<p><a href="https://github.com/axios/axios/compare/v1.17.0...v1.18.0">Full Changelog</a></p>
<h2>v1.17.0 — June 1, 2026</h2>
<p>This release adds Node HTTP zstd decompression, hardens config and release workflows, and fixes authentication, header, proxy, and type-handling regressions.</p>
<h2>🔒 Security Fixes</h2>
<ul>
<li><strong>Config Hardening:</strong> Guarded <code>socketPath</code>, <code>params</code>, and <code>paramsSerializer</code> reads with own-property checks to prevent inherited prototype values from affecting request behavior, including SSRF-sensitive paths. (<strong><a href="">#10901</a></strong>, <strong><a href="">#10922</a></strong>)</li>
<li><strong>Release Publishing:</strong> Switched the publish workflow to npm staged publishing for safer, auditable package releases with provenance. (<strong><a href="">#10926</a></strong>)</li>
</ul>
<h2>🚀 New Features</h2>
<ul>
<li><strong>HTTP Compression:</strong> Added Node HTTP adapter support for zstd response decompression, with <code>transitional.advertiseZstdAcceptEncoding</code> controlling whether <code>zstd</code> is advertised in <code>Accept-Encoding</code>. (<strong><a href="">#6792</a></strong>, <strong><a href="">#10920</a></strong>)</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li><strong>Authentication Handling:</strong> Restored Basic auth on same-origin Node redirects while continuing to strip credentials cross-origin, and aligned the fetch adapter with HTTP adapter behavior for URL-embedded Basic auth. (<strong><a href="">#10929</a></strong>, <strong><a href="">#10896</a></strong>)</li>
<li><strong>Proxy TLS:</strong> Preserved user <code>httpsAgent</code> TLS options when tunneling HTTPS requests through HTTP CONNECT proxies. (<strong><a href="">#10957</a></strong>)</li>
<li><strong>React Native FormData:</strong> Cleared default <code>Content-Type</code> for React Native <code>FormData</code> so multipart boundaries can be generated correctly. (<strong><a href="">#10898</a></strong>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>2d06f96</code></a> chore(release): prepare release 1.18.0 (<a href="">#11003</a>)</li>
<li><a href=""><code>32fc489</code></a> fix: malformed http urls (<a href="">#11000</a>)</li>
<li><a href=""><code>b40ce49</code></a> chore(deps-dev): bump the development_dependencies group with 10 updates (<a href="">#10</a>...</li>
<li><a href=""><code>fe964f9</code></a> docs: mark proxy config as Node.js only (<a href="">#10995</a>)</li>
<li><a href=""><code>5f229d2</code></a> chore(deps): bump actions/checkout from 6.0.2 to 6.0.3 in the github-actions ...</li>
<li><a href=""><code>fae9d4e</code></a> docs: clarify package update PR policy (<a href="">#10992</a>)</li>
<li><a href=""><code>28ab2ce</code></a> chore(deps-dev): bump the development_dependencies group with 2 updates (<a href="">#10989</a>)</li>
<li><a href=""><code>a8e4f13</code></a> fix(core): keep default validateStatus when request passes undefined (<a href="">#10899</a>)</li>
<li><a href=""><code>614f455</code></a> docs: publish v1.17.0 release notes (<a href="">#10988</a>)</li>
<li><a href=""><code>6bb12c1</code></a> fix: custom auth headers not stripped on cross-origin redirects (<a href="">#10892</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/axios/axios/compare/v1.16.0...v1.18.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=axios&package-manager=npm_and_yarn&previous-version=1.16.0&new-version=1.18.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

You can trigger a rebase of this PR by commenting `@dependabot rebase`.

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

> **Note**
> Automatic rebases have been disabled on this pull request as it has been open for over 30 days.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3f2f30fb3bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
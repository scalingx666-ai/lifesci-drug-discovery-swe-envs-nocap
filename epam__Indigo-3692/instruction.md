# Issue

**Title:** Bump axios from 1.15.2 to 1.16.0 in /utils/indigo-service/frontend/ui

## Description

Bumps [axios](https://github.com/axios/axios) from 1.15.2 to 1.16.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/axios/axios/releases">axios's releases</a>.</em></p>
<blockquote>
<h2>v1.16.0 — May 2, 2026</h2>
<p>This release adds support for the QUERY HTTP method and a new <code>ECONNREFUSED</code> error constant, lands a substantial wave of HTTP, fetch, and XHR adapter bug fixes around redirects, aborts, headers, and timeouts, and welcomes 23 new contributors.</p>
<h2>⚠️ Notable Changes</h2>
<p>A handful of fixes in this release are either security-adjacent or change observable behaviour. Please review before upgrading:</p>
<ul>
<li><strong>Fetch adapter now enforces <code>maxBodyLength</code> and <code>maxContentLength</code>.</strong> These limits were silently ignored on the fetch adapter prior to 1.16.0 — anyone relying on them as a safety net (DoS protection, accidental large uploads) had no protection. (<strong><a href="">#10795</a></strong>)</li>
<li><strong>Proxy requests now preserve user-supplied <code>Host</code> headers.</strong> Previously, the proxy path could overwrite a custom <code>Host</code>. Virtual-host-style routing through a proxy will now behave correctly. (<strong><a href="">#10822</a></strong>)</li>
<li><strong>Basic auth credentials embedded in URLs are now URL-decoded.</strong> If you have percent-encoded credentials in a URL (e.g. <code>https://user:p%40ss@host</code>), the decoded value is what now goes on the wire. (<strong><a href="">#10825</a></strong>)</li>
<li><strong><code>parseProtocol</code> now strictly requires a colon in the protocol separator.</strong> Strings that loosely parsed as protocols before may no longer match. (<strong><a href="">#10729</a></strong>)</li>
<li><strong>Deprecated <code>unescape()</code> replaced with modern UTF-8 encoding.</strong> Non-ASCII URL handling is now spec-correct; consumers depending on legacy <code>unescape()</code> quirks may see different output bytes. (<strong><a href="">#7378</a></strong>)</li>
<li><strong><code>transformRequest</code> input typing change was reverted.</strong> The typing change introduced in <a href="">#10745</a> was reverted in <a href="">#10810</a> after follow-up review — net behavior is unchanged from 1.15.2. (<strong><a href="">#10745</a></strong>, <strong><a href="">#10810</a></strong>)</li>
</ul>
<h2>🚀 New Features</h2>
<ul>
<li><strong>QUERY HTTP Method:</strong> Added support for the QUERY HTTP method across adapters and type definitions. (<strong><a href="">#10802</a></strong>)</li>
<li><strong>ECONNREFUSED Error Constant:</strong> Exposed <code>ECONNREFUSED</code> as a constant on <code>AxiosError</code> so callers can match connection-refused failures without comparing string literals (closes <a href="">#6485</a>). (<strong><a href="">#10680</a></strong>)</li>
<li><strong>Encode Helper Export:</strong> Exported the internal <code>encode</code> helper from <code>buildURL</code> so userland param serializers can reuse the same encoding logic that axios uses internally. (<strong><a href="">#6897</a></strong>)</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li><strong>HTTP Adapter — Redirects &amp; Headers:</strong> Cleared stale headers when a redirect targets a no-proxy host, fixed the redirect listener chain so listeners no longer stack across hops, restored the missing <code>requestDetails</code> argument on <code>beforeRedirect</code>, preserved user-supplied <code>Host</code> headers when forwarding through a proxy, and properly URL-decoded basic auth credentials. (<strong><a href="">#10794</a></strong>, <strong><a href="">#10800</a></strong>, <strong><a href="">#6241</a></strong>, <strong><a href="">#10822</a></strong>, <strong><a href="">#10825</a></strong>)</li>
<li><strong>HTTP Adapter — Streams &amp; Timeouts:</strong> Preserved the partial response object on <code>AxiosError</code> when a stream is aborted after headers arrive, honoured the <code>timeout</code> option during the connect phase when redirects are disabled, and resolved an unsettled-promise hang when an aborted request was combined with compression and <code>maxRedirects: 0</code>. (<strong><a href="">#10708</a></strong>, <strong><a href="">#10819</a></strong>, <strong><a href="">#7149</a></strong>)</li>
<li><strong>Fetch Adapter:</strong> Enforced <code>maxBodyLength</code> / <code>maxContentLength</code> in the fetch adapter, set the <code>User-Agent</code> header to match the HTTP adapter, preserved the original abort reason instead of replacing it with a generic error, and deferred global access so importing the module no longer throws a <code>TypeError</code> in restricted environments. (<strong><a href="">#10795</a></strong>, <strong><a href="">#10772</a></strong>, <strong><a href="">#10806</a></strong>, <strong><a href="">#7260</a></strong>)</li>
<li><strong>XHR Adapter:</strong> Unsubscribed the <code>cancelToken</code> and <code>AbortSignal</code> listeners on the error, timeout, and abort code paths to prevent leaked subscriptions. (<strong><a href="">#10787</a></strong>)</li>
<li><strong>Error Handling:</strong> Attached the parsed response to <code>AxiosError</code> when <code>JSON.parse</code> fails inside <code>dispatchRequest</code>, prevented <code>settle</code> from emitting <code>undefined</code> error codes, and tightened the <code>parseProtocol</code> regex to require a colon in the protocol separator. (<strong><a href="">#10724</a></strong>, <strong><a href="">#7276</a></strong>, <strong><a href="">#10729</a></strong>)</li>
<li><strong>Types &amp; Exports:</strong> Aligned the CommonJS <code>CancelToken</code> typings with the ESM build, fixed a compiler error caused by <code>RawAxiosHeaders</code>, and re-exported <code>create</code> from the package index. (<strong><a href="">#7414</a></strong>, <strong><a href="">#6389</a></strong>, <strong><a href="">#6460</a></strong>)</li>
<li><strong>UTF-8 Encoding:</strong> Replaced the deprecated <code>unescape()</code> call with a modern UTF-8 encoding implementation. (<strong><a href="">#7378</a></strong>)</li>
<li><strong>Misc Cleanup:</strong> Resolved a batch of small inconsistencies and gadget-level issues across the codebase. (<strong><a href="">#10833</a></strong>)</li>
</ul>
<h2>🔧 Maintenance &amp; Chores</h2>
<ul>
<li><strong>Refactor — ES6 Modernisation:</strong> Modernised the <code>utils</code> module and XHR adapter to use ES6 features, and tidied the multipart boundary error message. (<strong><a href="">#10588</a></strong>, <strong><a href="">#7419</a></strong>)</li>
<li><strong>Tests:</strong> Hardened the HTTP test server lifecycle to fix flaky <code>FormData</code> EPIPE failures, fixed Win32 platform support for the pipe tests, and corrected an incorrect test assumption. (<strong><a href="">#10820</a></strong>, <strong><a href="">#10791</a></strong>, <strong><a href="">#10796</a></strong>)</li>
<li><strong>Docs:</strong> Documented <code>paramsSerializer.encode</code> for strict RFC 3986 query encoding, updated the <code>parseReviver</code> TypeScript definitions and configuration docs for ES2023, added timeout guidance to the README's first async example, and expanded notes around the recent type changes. (<strong><a href="">#10821</a></strong>, <strong><a href="">#10782</a></strong>, <strong><a href="">#10759</a></strong>, <strong><a href="">#10804</a></strong>)</li>
<li><strong>Reverted:</strong> Reverted the <code>transformRequest</code> input typing change from <a href="">#10745</a> after follow-up review. (<strong><a href="">#10745</a></strong>, <strong><a href="">#10810</a></strong>)</li>
<li><strong>Dependencies:</strong> Bumped <code>actions/setup-node</code>, the <code>github-actions</code> group, and <code>postcss</code> (in <code>/docs</code>) to their latest versions. (<strong><a href="">#10785</a></strong>, <strong><a href="">#10813</a></strong>, <strong><a href="">#10814</a></strong>)</li>
<li><strong>Release:</strong> Updated changelog and packages, and prepared the 1.16.0 release. (<strong><a href="">#10790</a></strong>, <strong><a href="">#10834</a></strong>)</li>
</ul>
<h2>🌟 New Contributors</h2>
<p>We are thrilled to welcome our new contributors. Thank you for helping improve axios:</p>
<ul>
<li><strong><a href="https://github.com/singhankit001"><code>@​singhankit001</code></a></strong> (<strong><a href="">#10588</a></strong>)</li>
<li><strong><a href="https://github.com/cuiweixie"><code>@​cuiweixie</code></a></strong> (<strong><a href="">#7419</a></strong>)</li>
<li><strong><a href="https://github.com/iruizsalinas"><code>@​iruizsalinas</code></a></strong> (<strong><a href="">#10787</a></strong>)</li>
<li><strong><a href="https://github.com/MarcosNocetti"><code>@​MarcosNocetti</code></a></strong> (<strong><a href="">#10680</a></strong>)</li>
<li><strong><a href="https://github.com/deepview-autofix"><code>@​deepview-autofix</code></a></strong> (<strong><a href="">#10729</a></strong>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/axios/axios/blob/v1.x/CHANGELOG.md">axios's changelog</a>.</em></p>
<blockquote>
<h2>v1.16.0 — May 2, 2026</h2>
<p>This release adds support for the QUERY HTTP method and a new <code>ECONNREFUSED</code> error constant, lands a substantial wave of HTTP, fetch, and XHR adapter bug fixes around redirects, aborts, headers, and timeouts, and welcomes 23 new contributors.</p>
<h2>⚠️ Notable Changes</h2>
<p>A handful of fixes in this release are either security-adjacent or change observable behaviour. Please review before upgrading:</p>
<ul>
<li><strong>Fetch adapter now enforces <code>maxBodyLength</code> and <code>maxContentLength</code>.</strong> These limits were silently ignored on the fetch adapter prior to 1.16.0 — anyone relying on them as a safety net (DoS protection, accidental large uploads) had no protection. (<strong><a href="">#10795</a></strong>)</li>
<li><strong>Proxy requests now preserve user-supplied <code>Host</code> headers.</strong> Previously, the proxy path could overwrite a custom <code>Host</code>. Virtual-host-style routing through a proxy will now behave correctly. (<strong><a href="">#10822</a></strong>)</li>
<li><strong>Basic auth credentials embedded in URLs are now URL-decoded.</strong> If you have percent-encoded credentials in a URL (e.g. <code>https://user:p%40ss@host</code>), the decoded value is what now goes on the wire. (<strong><a href="">#10825</a></strong>)</li>
<li><strong><code>parseProtocol</code> now strictly requires a colon in the protocol separator.</strong> Strings that loosely parsed as protocols before may no longer match. (<strong><a href="">#10729</a></strong>)</li>
<li><strong>Deprecated <code>unescape()</code> replaced with modern UTF-8 encoding.</strong> Non-ASCII URL handling is now spec-correct; consumers depending on legacy <code>unescape()</code> quirks may see different output bytes. (<strong><a href="">#7378</a></strong>)</li>
<li><strong><code>transformRequest</code> input typing change was reverted.</strong> The typing change introduced in <a href="">#10745</a> was reverted in <a href="">#10810</a> after follow-up review — net behavior is unchanged from 1.15.2. (<strong><a href="">#10745</a></strong>, <strong><a href="">#10810</a></strong>)</li>
</ul>
<h2>🚀 New Features</h2>
<ul>
<li><strong>QUERY HTTP Method:</strong> Added support for the QUERY HTTP method across adapters and type definitions. (<strong><a href="">#10802</a></strong>)</li>
<li><strong>ECONNREFUSED Error Constant:</strong> Exposed <code>ECONNREFUSED</code> as a constant on <code>AxiosError</code> so callers can match connection-refused failures without comparing string literals (closes <a href="">#6485</a>). (<strong><a href="">#10680</a></strong>)</li>
<li><strong>Encode Helper Export:</strong> Exported the internal <code>encode</code> helper from <code>buildURL</code> so userland param serializers can reuse the same encoding logic that axios uses internally. (<strong><a href="">#6897</a></strong>)</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li><strong>HTTP Adapter — Redirects &amp; Headers:</strong> Cleared stale headers when a redirect targets a no-proxy host, fixed the redirect listener chain so listeners no longer stack across hops, restored the missing <code>requestDetails</code> argument on <code>beforeRedirect</code>, preserved user-supplied <code>Host</code> headers when forwarding through a proxy, and properly URL-decoded basic auth credentials. (<strong><a href="">#10794</a></strong>, <strong><a href="">#10800</a></strong>, <strong><a href="">#6241</a></strong>, <strong><a href="">#10822</a></strong>, <strong><a href="">#10825</a></strong>)</li>
<li><strong>HTTP Adapter — Streams &amp; Timeouts:</strong> Preserved the partial response object on <code>AxiosError</code> when a stream is aborted after headers arrive, honoured the <code>timeout</code> option during the connect phase when redirects are disabled, and resolved an unsettled-promise hang when an aborted request was combined with compression and <code>maxRedirects: 0</code>. (<strong><a href="">#10708</a></strong>, <strong><a href="">#10819</a></strong>, <strong><a href="">#7149</a></strong>)</li>
<li><strong>Fetch Adapter:</strong> Enforced <code>maxBodyLength</code> / <code>maxContentLength</code> in the fetch adapter, set the <code>User-Agent</code> header to match the HTTP adapter, preserved the original abort reason instead of replacing it with a generic error, and deferred global access so importing the module no longer throws a <code>TypeError</code> in restricted environments. (<strong><a href="">#10795</a></strong>, <strong><a href="">#10772</a></strong>, <strong><a href="">#10806</a></strong>, <strong><a href="">#7260</a></strong>)</li>
<li><strong>XHR Adapter:</strong> Unsubscribed the <code>cancelToken</code> and <code>AbortSignal</code> listeners on the error, timeout, and abort code paths to prevent leaked subscriptions. (<strong><a href="">#10787</a></strong>)</li>
<li><strong>Error Handling:</strong> Attached the parsed response to <code>AxiosError</code> when <code>JSON.parse</code> fails inside <code>dispatchRequest</code>, prevented <code>settle</code> from emitting <code>undefined</code> error codes, and tightened the <code>parseProtocol</code> regex to require a colon in the protocol separator. (<strong><a href="">#10724</a></strong>, <strong><a href="">#7276</a></strong>, <strong><a href="">#10729</a></strong>)</li>
<li><strong>Types &amp; Exports:</strong> Aligned the CommonJS <code>CancelToken</code> typings with the ESM build, fixed a compiler error caused by <code>RawAxiosHeaders</code>, and re-exported <code>create</code> from the package index. (<strong><a href="">#7414</a></strong>, <strong><a href="">#6389</a></strong>, <strong><a href="">#6460</a></strong>)</li>
<li><strong>UTF-8 Encoding:</strong> Replaced the deprecated <code>unescape()</code> call with a modern UTF-8 encoding implementation. (<strong><a href="">#7378</a></strong>)</li>
<li><strong>Misc Cleanup:</strong> Resolved a batch of small inconsistencies and gadget-level issues across the codebase. (<strong><a href="">#10833</a></strong>)</li>
</ul>
<h2>🔧 Maintenance &amp; Chores</h2>
<ul>
<li><strong>Refactor — ES6 Modernisation:</strong> Modernised the <code>utils</code> module and XHR adapter to use ES6 features, and tidied the multipart boundary error message. (<strong><a href="">#10588</a></strong>, <strong><a href="">#7419</a></strong>)</li>
<li><strong>Tests:</strong> Hardened the HTTP test server lifecycle to fix flaky <code>FormData</code> EPIPE failures, fixed Win32 platform support for the pipe tests, and corrected an incorrect test assumption. (<strong><a href="">#10820</a></strong>, <strong><a href="">#10791</a></strong>, <strong><a href="">#10796</a></strong>)</li>
<li><strong>Docs:</strong> Documented <code>paramsSerializer.encode</code> for strict RFC 3986 query encoding, updated the <code>parseReviver</code> TypeScript definitions and configuration docs for ES2023, added timeout guidance to the README's first async example, and expanded notes around the recent type changes. (<strong><a href="">#10821</a></strong>, <strong><a href="">#10782</a></strong>, <strong><a href="">#10759</a></strong>, <strong><a href="">#10804</a></strong>)</li>
<li><strong>Reverted:</strong> Reverted the <code>transformRequest</code> input typing change from <a href="">#10745</a> after follow-up review. (<strong><a href="">#10745</a></strong>, <strong><a href="">#10810</a></strong>)</li>
<li><strong>Dependencies:</strong> Bumped <code>actions/setup-node</code>, the <code>github-actions</code> group, and <code>postcss</code> (in <code>/docs</code>) to their latest versions. (<strong><a href="">#10785</a></strong>, <strong><a href="">#10813</a></strong>, <strong><a href="">#10814</a></strong>)</li>
<li><strong>Release:</strong> Updated changelog and packages, and prepared the 1.16.0 release. (<strong><a href="">#10790</a></strong>, <strong><a href="">#10834</a></strong>)</li>
</ul>
<h2>🌟 New Contributors</h2>
<p>We are thrilled to welcome our new contributors. Thank you for helping improve axios:</p>
<ul>
<li><strong><a href="https://github.com/singhankit001"><code>@​singhankit001</code></a></strong> (<strong><a href="">#10588</a></strong>)</li>
<li><strong><a href="https://github.com/cuiweixie"><code>@​cuiweixie</code></a></strong> (<strong><a href="">#7419</a></strong>)</li>
<li><strong><a href="https://github.com/iruizsalinas"><code>@​iruizsalinas</code></a></strong> (<strong><a href="">#10787</a></strong>)</li>
<li><strong><a href="https://github.com/MarcosNocetti"><code>@​MarcosNocetti</code></a></strong> (<strong><a href="">#10680</a></strong>)</li>
<li><strong><a href="https://github.com/deepview-autofix"><code>@​deepview-autofix</code></a></strong> (<strong><a href="">#10729</a></strong>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>df53d7d</code></a> chore(release): prepare release 1.16.0 (<a href="">#10834</a>)</li>
<li><a href=""><code>9d92bcd</code></a> fix: gadgets and smaller issues (<a href="">#10833</a>)</li>
<li><a href=""><code>5107ee6</code></a> fix: prevent undefined error codes in settle (<a href="">#7276</a>)</li>
<li><a href=""><code>e573499</code></a> fix(fetch): defer global access in fetch adapter (<a href="">#7260</a>)</li>
<li><a href=""><code>ad68e1a</code></a> fix(http): honor timeout during connect without redirects (<a href="">#10819</a>)</li>
<li><a href=""><code>2a51828</code></a> fix(http): decode URL basic auth credentials (<a href="">#10825</a>)</li>
<li><a href=""><code>0e8b6bb</code></a> fix(http): preserve user-supplied Host header when forwarding through a proxy...</li>
<li><a href=""><code>79f39e1</code></a> docs: document paramsSerializer.encode for strict RFC 3986 query encoding (<a href="">#1</a>...</li>
<li><a href=""><code>0fe3a5f</code></a> [Docs/Types] Update <code>parseReviver</code> TypeScript definitions for ES2023 and add ...</li>
<li><a href=""><code>cd6737f</code></a> chore: matches the sibling responseStream.on(aborted) handler and added tests...</li>
<li>Additional commits viewable in <a href="https://github.com/axios/axios/compare/v1.15.2...v1.16.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=axios&package-manager=npm_and_yarn&previous-version=1.15.2&new-version=1.16.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd82e2e36177`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
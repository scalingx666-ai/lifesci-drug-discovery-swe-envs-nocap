# Issue

**Title:** chore(deps): bump node-forge from 1.4.2 to 1.4.3

## Description

Bumps [node-forge](https://github.com/digitalbazaar/forge) from 1.4.2 to 1.4.3.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/digitalbazaar/forge/blob/main/CHANGELOG.md">node-forge's changelog</a>.</em></p>
<blockquote>
<h2>1.4.3 - 2026-11-03</h2>
<h3>Security</h3>
<ul>
<li><strong>HIGH</strong>: X.509 certificate chain verification ignores name constraints.
<ul>
<li><code>pki.verifyCertificateChain()</code> does not check the nameConstraints
extension (RFC 5280 4.2.1.10). A non-critical nameConstraints extension
in a CA certificate is ignored, so a name-constrained intermediate CA can
issue certificates for names outside its permitted subtrees, or inside
its excluded subtrees, and the chain verifies. Exploitation requires the
private key of a name-constrained CA that chains to a trusted root. A
critical nameConstraints extension is rejected as an unsupported critical
extension.</li>
<li>Reported by <a href="https://github.com/bhaswanthc"><code>@​bhaswanthc</code></a>.</li>
<li>CVE ID: <a href="">CVE-TBD</a></li>
<li>GHSA ID: <a href="https://github.com/digitalbazaar/forge/security/advisories/GHSA-3cc4-3294-vgjf">GHSA-3cc4-3294-vgjf</a></li>
</ul>
</li>
<li><strong>MODERATE</strong>: TLS client crash on a handshake record without a session.
<ul>
<li>A TLS client throws an uncaught <code>TypeError</code> from <code>process()</code> when it
receives a ServerHello while it has no session: after a <code>close_notify</code>
alert or a call to <code>close()</code>, or before <code>handshake()</code> is called. A
malicious server, or an on-path attacker, can terminate a Node.js process
that passes socket data to <code>process()</code> without catching exceptions.
Servers are not affected.</li>
<li>Reported by <a href="https://github.com/manus-use"><code>@​manus-use</code></a>.</li>
<li>CVE ID: <a href="">CVE-TBD</a></li>
<li>GHSA ID: <a href="https://github.com/digitalbazaar/forge/security/advisories/GHSA-j8rw-jp99-435v">GHSA-j8rw-jp99-435v</a></li>
</ul>
</li>
<li><strong>MODERATE</strong>: ReDoS in <code>forge.http</code> response header parsing.
<ul>
<li><code>forge.http</code> trims response header and <code>Set-Cookie</code> values with a
regular expression that takes quadratic time on a long run of whitespace
followed by another character. A server, or an on-path attacker, can
block a <code>forge.http</code> client for minutes with one large header.</li>
<li>Reported by <a href="https://github.com/manus-pi"><code>@​manus-pi</code></a>.</li>
<li>CVE ID: <a href="">CVE-TBD</a></li>
<li>GHSA ID: <a href="https://github.com/digitalbazaar/forge/security/advisories/GHSA-6cv4-p8m7-4r25">GHSA-6cv4-p8m7-4r25</a></li>
</ul>
</li>
<li><strong>MODERATE</strong>: TLS client crash on an unsupported ServerHello compression
method.
<ul>
<li>A TLS client accepts any compression method in the ServerHello,
although it only offers no compression. An unknown method makes
<code>process()</code> throw an uncaught <code>Error</code> at ServerHelloDone, before the
server is authenticated. A malicious server, or an on-path attacker, can
terminate a Node.js process that passes socket data to <code>process()</code>
without catching exceptions, including through <code>forge.tls.wrapSocket</code>.
Servers are not affected.</li>
<li>Reported by <a href="https://github.com/alienkeric"><code>@​alienkeric</code></a>.</li>
<li>CVE ID: <a href="">CVE-TBD</a></li>
<li>GHSA ID: <a href="https://github.com/digitalbazaar/forge/security/advisories/GHSA-w4xr-hqv8-ch44">GHSA-w4xr-hqv8-ch44</a></li>
</ul>
</li>
<li><strong>LOW</strong>: Ed25519 signature verification accepts small-order public keys.
<ul>
<li><code>ed25519.verify()</code> does not reject public keys of small order, such as
the identity point. Under such a key, a signature with <code>S = 0</code> and a
small-order <code>R</code> verifies for many or, with the identity key, all
messages, without any private key. Applications are affected only if</li>
</ul>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>936b24d</code></a> Release 1.4.3.</li>
<li><a href=""><code>4d8f79a</code></a> Update changelog.</li>
<li><a href=""><code>1d9816d</code></a> Check the ServerHello compression method.</li>
<li><a href=""><code>326a4d0</code></a> Trim forge.http header values in linear time.</li>
<li><a href=""><code>2cfaeb5</code></a> Ignore handshake messages on a TLS client without a session.</li>
<li><a href=""><code>6b23eae</code></a> Complete nameConstraints enforcement.</li>
<li><a href=""><code>862aa5f</code></a> Enforce nameConstraints in <code>verifyCertificateChain()</code>.</li>
<li><a href=""><code>956f2b5</code></a> Document ed25519.verify() small-order key behavior.</li>
<li><a href=""><code>1b77e6f</code></a> Reject small-order Ed25519 public keys in verify.</li>
<li><a href=""><code>2bd5146</code></a> Add GitHub usernames to credits.</li>
<li>Additional commits viewable in <a href="https://github.com/digitalbazaar/forge/compare/v1.4.2...v1.4.3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=node-forge&package-manager=npm_and_yarn&previous-version=1.4.2&new-version=1.4.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/epam/ketcher/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e9e420e853e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
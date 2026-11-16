# Issue

**Title:** chore(deps): bump node-forge from 1.4.0 to 1.4.2

## Description

Bumps [node-forge](https://github.com/digitalbazaar/forge) from 1.4.0 to 1.4.2.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/digitalbazaar/forge/blob/main/CHANGELOG.md">node-forge's changelog</a>.</em></p>
<blockquote>
<h2>1.4.2 - 2026-10-27</h2>
<h3>Fixed</h3>
<ul>
<li>[pem] Convert non-string input to a string in <code>pem.decode()</code> as before
1.4.1. The 1.4.1 PEM ReDoS fix (GHSA-7wch-p9px-956x) caused a <code>TypeError</code>
for <code>Buffer</code> input, which is used by <code>node-jose</code>.
(<a href="">#1165</a>)</li>
</ul>
<h2>1.4.1 - 2026-10-27</h2>
<h3>Notes</h3>
<ul>
<li>This release involved coordinating many security reports from many groups,
people, and robots over too long period of time. Thank you for your reports
and patience.</li>
<li>Claude Code was used to help organize, track, untangle, merge, test,
validate, fix, and improve it all. Further verification of fixes would be
welcome.</li>
<li>Tracking credits was challenging for some issues due to multiple email and
GitHub reports, incomplete contact details, or combining of partial reports
and fixes. Please let us know if there are credits changes needed here or in
advisory data.</li>
</ul>
<h3>Security</h3>
<ul>
<li><strong>HIGH</strong>: Signature forgery in RSA-PKCS due to ASN.1 extra field in
DigestAlgorithm.
<ul>
<li>RSASSA PKCS#1 v1.5 signature verification accepts forged signatures for low
public exponent keys (e=3). The fix for CVE-2026-33894 only checked the
element count of the outer DigestInfo. Attackers can add &quot;garbage&quot; elements
inside the nested DigestAlgorithm SEQUENCE in order to construct a
signature that passes verification, enabling Bleichenbacher style forgery.</li>
<li>Reported by Geo (<a href="https://github.com/geo-chen"><code>@​geo-chen</code></a>).</li>
<li>CVE ID: <a href="https://www.cve.org/CVERecord?id=CVE-2026-85393">CVE-2026-85393</a></li>
<li>GHSA ID: <a href="https://github.com/digitalbazaar/forge/security/advisories/GHSA-2g46-22mc-6gwp">GHSA-2g46-22mc-6gwp</a></li>
</ul>
</li>
<li><strong>HIGH</strong>: Signature forgery in RSA-PKCS due to non-canonical DigestInfo
encoding.
<ul>
<li>RSASSA PKCS#1 v1.5 signature verification accepts non-canonical DigestInfo
encodings, such as NULL parameters with content, non-minimal length
encodings, and non-canonical OIDs. These provide attackers space to
construct forged signatures for low public exponent keys (e=3), similar to
CVE-2026-33894 and CVE-2026-85393.</li>
<li>Reported by Oren Yomtov (<a href="https://github.com/orenyomtov"><code>@​orenyomtov</code></a>, Fireblocks), Bronson Yen (Calif.io,
in collaboration with Claude and Anthropic Research), Kamil Hałajda,
<a href="https://github.com/pzartech"><code>@​pzartech</code></a>, <a href="https://github.com/antonlissone"><code>@​antonlissone</code></a>, and <a href="https://github.com/Brechard"><code>@​Brechard</code></a>.</li>
<li>CVE ID: <a href="https://www.cve.org/CVERecord?id=CVE-2026-119192">CVE-2026-119192</a></li>
<li>GHSA ID: <a href="https://github.com/digitalbazaar/forge/security/advisories/GHSA-6qrw-m8cv-hcxf">GHSA-6qrw-m8cv-hcxf</a></li>
</ul>
</li>
<li><strong>HIGH</strong>: ASN.1 resource exhaustion via BIT STRING decoding.
<ul>
<li>An Uncontrolled Recursion (CWE-674) and Uncontrolled Resource Consumption
(CWE-400) vulnerability in node-forge versions 1.4.0 and below enables
remote, unauthenticated attackers to exhaust CPU and memory with small
crafted DER or PEM inputs (certificates, keys, and other structures parsed</li>
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
<li><a href=""><code>7928054</code></a> Release 1.4.2.</li>
<li><a href=""><code>1d8c245</code></a> Update changelog.</li>
<li><a href=""><code>ce5b576</code></a> Convert non-string input in <code>pem.decode()</code>.</li>
<li><a href=""><code>c1d64ef</code></a> Fix changelog typo.</li>
<li><a href=""><code>453d196</code></a> Start 1.4.2-0.</li>
<li><a href=""><code>8a91737</code></a> Release 1.4.1.</li>
<li><a href=""><code>fdd1b9f</code></a> Update changelog.</li>
<li><a href=""><code>4c1c3e3</code></a> Add changelog release notes.</li>
<li><a href=""><code>0b455eb</code></a> Ignore TLS heartbeat requests before the handshake.</li>
<li><a href=""><code>e96c47b</code></a> Fix jsbn <code>modInverse</code> hang with negative inputs.</li>
<li>Additional commits viewable in <a href="https://github.com/digitalbazaar/forge/compare/v1.4.0...v1.4.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=node-forge&package-manager=npm_and_yarn&previous-version=1.4.0&new-version=1.4.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c678536f91a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
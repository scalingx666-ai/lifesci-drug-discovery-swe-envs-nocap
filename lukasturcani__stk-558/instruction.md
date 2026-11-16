# Issue

**Title:** Bump pymongo from 4.15.2 to 4.18.2

## Description

Bumps [pymongo](https://github.com/mongodb/mongo-python-driver) from 4.15.2 to 4.18.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/mongodb/mongo-python-driver/releases">pymongo's releases</a>.</em></p>
<blockquote>
<h2>PyMongo 4.18.2</h2>
<p>Community notes: <a href="https://www.mongodb.com/community/forums/t/pymongo-4-18-2-released/343732">https://www.mongodb.com/community/forums/t/pymongo-4-18-2-released/343732</a></p>
<p><a href="https://www.cve.org/CVERecord?id=CVE-2026-96749">CVE-2026-96749</a>
<a href="https://www.cve.org/CVERecord?id=CVE-2026-96748">CVE-2026-96748</a>
<a href="https://www.cve.org/CVERecord?id=CVE-2026-96747">CVE-2026-96747</a></p>
<h2>PyMongo 4.18.1</h2>
<p>Community notes: <a href="https://www.mongodb.com/community/forums/t/pymongo-4-18-1-released/343338">https://www.mongodb.com/community/forums/t/pymongo-4-18-1-released/343338</a></p>
<h2>PyMongo 4.18.0</h2>
<p>Community notes: <a href="https://www.mongodb.com/community/forums/t/pymongo-4-18-released/343137">https://www.mongodb.com/community/forums/t/pymongo-4-18-released/343137</a></p>
<h2>PyMongo 4.17.0</h2>
<p><a href="https://www.mongodb.com/community/forums/t/pymongo-4-17-released/338426">Community notes</a></p>
<h2>What's Changed</h2>
<ul>
<li>refactor(ci): replace shell=True and awk pipes with native Python by <a href="https://github.com/RinZ27"><code>@​RinZ27</code></a> in <a href="">mongodb/mongo-python-driver#2671</a></li>
<li>PYTHON-5697 - Migrate 8.0+ tests to Windows 2022 by <a href="https://github.com/NoahStapp"><code>@​NoahStapp</code></a> in <a href="">mongodb/mongo-python-driver#2681</a></li>
<li>[Spec Resync] 01-19-2026 by <a href="https://github.com/mongodb-drivers-pr-bot"><code>@​mongodb-drivers-pr-bot</code></a>[bot] in <a href="">mongodb/mongo-python-driver#2680</a></li>
<li>Bump pyright from 1.1.407 to 1.1.408 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">mongodb/mongo-python-driver#2675</a></li>
<li>PYTHON-5692 - [Infrastructure] Improve dependabot version updates by <a href="https://github.com/NoahStapp"><code>@​NoahStapp</code></a> in <a href="">mongodb/mongo-python-driver#2682</a></li>
<li>PYTHON-5605 - Drop usage of Ubuntu 20 by <a href="https://github.com/NoahStapp"><code>@​NoahStapp</code></a> in <a href="">mongodb/mongo-python-driver#2683</a></li>
<li>PYTHON-5699 &amp; PYTHON-5698 [Spec Resync] 01-26-2026 by <a href="https://github.com/mongodb-drivers-pr-bot"><code>@​mongodb-drivers-pr-bot</code></a>[bot] in <a href="">mongodb/mongo-python-driver#2685</a></li>
<li>PYTHON-5703 Use Ubuntu24 for AWS Auth tests by <a href="https://github.com/blink1073"><code>@​blink1073</code></a> in <a href="">mongodb/mongo-python-driver#2686</a></li>
<li>PYTHON-5704 Skip free-threading for enterprise auth builds by <a href="https://github.com/blink1073"><code>@​blink1073</code></a> in <a href="">mongodb/mongo-python-driver#2687</a></li>
<li>Bump astral-sh/setup-uv from 7.1.6 to 7.2.0 in the actions group across 1 directory by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">mongodb/mongo-python-driver#2684</a></li>
<li>Bump peter-evans/create-pull-request from 8.0.0 to 8.1.0 in the actions group by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">mongodb/mongo-python-driver#2692</a></li>
<li>PYTHON-1357 - Refactor Cursor and CommandCursor by <a href="https://github.com/NoahStapp"><code>@​NoahStapp</code></a> in <a href="">mongodb/mongo-python-driver#2691</a></li>
<li>[Spec Resync] 02-02-2026 by <a href="https://github.com/mongodb-drivers-pr-bot"><code>@​mongodb-drivers-pr-bot</code></a>[bot] in <a href="">mongodb/mongo-python-driver#2694</a></li>
<li>PYTHON-5467 Add codecov integration by <a href="https://github.com/blink1073"><code>@​blink1073</code></a> in <a href="">mongodb/mongo-python-driver#2690</a></li>
<li>Bump astral-sh/setup-uv from 7.2.0 to 7.2.1 in the actions group by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">mongodb/mongo-python-driver#2700</a></li>
<li>PYTHON-XXXX Fixed typo in Running Tests Locally section. by <a href="https://github.com/caseyclements"><code>@​caseyclements</code></a> in <a href="">mongodb/mongo-python-driver#2698</a></li>
<li>PYTHON-5467 Fix codecov upload by <a href="https://github.com/blink1073"><code>@​blink1073</code></a> in <a href="">mongodb/mongo-python-driver#2701</a></li>
<li>PYTHON-5467 Fix codecov upload on Evergreen by <a href="https://github.com/blink1073"><code>@​blink1073</code></a> in <a href="">mongodb/mongo-python-driver#2702</a></li>
<li>PYTHON-5715 Add appName to OIDC test failpoints by <a href="https://github.com/blink1073"><code>@​blink1073</code></a> in <a href="">mongodb/mongo-python-driver#2697</a></li>
<li>PYTHON-5705 Improve fallback for PyOpenSSL windows system certs loading by <a href="https://github.com/blink1073"><code>@​blink1073</code></a> in <a href="">mongodb/mongo-python-driver#2688</a></li>
<li>PYTHON-3898 Add coverage to all variants by <a href="https://github.com/blink1073"><code>@​blink1073</code></a> in <a href="">mongodb/mongo-python-driver#2705</a></li>
<li>PYTHON-5729 Pin setuptools when using older gevent by <a href="https://github.com/blink1073"><code>@​blink1073</code></a> in <a href="">mongodb/mongo-python-driver#2708</a></li>
<li>Bump the actions group with 2 updates by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">mongodb/mongo-python-driver#2711</a></li>
<li>PYTHON-5708 Temporarily skip some BSON encryption tests by <a href="https://github.com/blink1073"><code>@​blink1073</code></a> in <a href="">mongodb/mongo-python-driver#2709</a></li>
<li>PYTHON-5732 Use mongodb-runner in Evergreen Tests by <a href="https://github.com/blink1073"><code>@​blink1073</code></a> in <a href="">mongodb/mongo-python-driver#2703</a></li>
<li>PYTHON-5731 - Server selection deprioritization only for overload errors on replica sets by <a href="https://github.com/NoahStapp"><code>@​NoahStapp</code></a> in <a href="">mongodb/mongo-python-driver#2710</a></li>
<li>PYTHON-5737 - BSON encoding/decoding performance improvements by <a href="https://github.com/NoahStapp"><code>@​NoahStapp</code></a> in <a href="">mongodb/mongo-python-driver#2715</a></li>
<li>[Spec Resync] 03-02-2026 by <a href="https://github.com/mongodb-drivers-pr-bot"><code>@​mongodb-drivers-pr-bot</code></a>[bot] in <a href="">mongodb/mongo-python-driver#2716</a></li>
<li>Python 4542 - Improved sessions API by <a href="https://github.com/NoahStapp"><code>@​NoahStapp</code></a> in <a href="">mongodb/mongo-python-driver#2712</a></li>
<li>PYTHON-5742 - Add Copilot instructions by <a href="https://github.com/NoahStapp"><code>@​NoahStapp</code></a> in <a href="">mongodb/mongo-python-driver#2717</a></li>
<li>PYTHON-5747 Add jira link to spec resync PR by <a href="https://github.com/sleepyStick"><code>@​sleepyStick</code></a> in <a href="">mongodb/mongo-python-driver#2723</a></li>
<li>PYTHON-5114 Test suite reduce killAllSessions calls by <a href="https://github.com/ShaneHarvey"><code>@​ShaneHarvey</code></a> in <a href="">mongodb/mongo-python-driver#2721</a></li>
<li>PYTHON-5748 Remove unused SpecRunner class by <a href="https://github.com/ShaneHarvey"><code>@​ShaneHarvey</code></a> in <a href="">mongodb/mongo-python-driver#2725</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/mongodb/mongo-python-driver/blob/main/doc/changelog.rst">pymongo's changelog</a>.</em></p>
<blockquote>
<h2>Changes in Version 4.18.2 (2026/09/24)</h2>
<p>Version 4.18.2 is a bug fix release.</p>
<ul>
<li>Hardened the bson buffer size guard against signed integer overflow. (<code>CVE-2026-96749</code>_).</li>
<li>Fixed connection string parsing to percent-decode each host individually. (<code>CVE-2026-96748</code>_).</li>
<li>Client-side field level encryption now rejects a KMS endpoint ending in <code>.sock</code>. (<code>CVE-2026-96747</code>_).</li>
</ul>
<p>.. _CVE-2026-96749: <a href="https://www.cve.org/CVERecord?id=CVE-2026-96749">https://www.cve.org/CVERecord?id=CVE-2026-96749</a>
.. _CVE-2026-96748: <a href="https://www.cve.org/CVERecord?id=CVE-2026-96748">https://www.cve.org/CVERecord?id=CVE-2026-96748</a>
.. _CVE-2026-96747: <a href="https://www.cve.org/CVERecord?id=CVE-2026-96747">https://www.cve.org/CVERecord?id=CVE-2026-96747</a></p>
<p>Issues Resolved
...............</p>
<p>See the <code>PyMongo 4.18.2 release notes in JIRA</code>_ for the list of resolved issues
in this release.</p>
<p>.. _PyMongo 4.18.2 release notes in JIRA: <a href="https://jira.mongodb.org/secure/ReleaseNote.jspa?projectId=10004&amp;version=52896">https://jira.mongodb.org/secure/ReleaseNote.jspa?projectId=10004&amp;version=52896</a></p>
<h2>Changes in Version 4.18.1 (2026/09/10)</h2>
<p>Version 4.18.1 is a bug fix release.</p>
<ul>
<li>Use an exact match for the file ID in GridFS delete methods
(<code>CVE-2026-88029</code>_).</li>
</ul>
<p>.. _CVE-2026-88029: <a href="https://www.cve.org/CVERecord?id=CVE-2026-88029">https://www.cve.org/CVERecord?id=CVE-2026-88029</a></p>
<h2>Changes in Version 4.18.0 (2026/09/03)</h2>
<p>PyMongo 4.18 brings a number of changes including:</p>
<ul>
<li>Added <code>srvAllowedHostsSuffix</code> as a URI option and keyword argument to
:class:<code>~pymongo.synchronous.mongo_client.MongoClient</code> and
:class:<code>~pymongo.asynchronous.mongo_client.AsyncMongoClient</code>. When connecting
via <code>mongodb+srv://</code>, this option overrides the default requirement that
SRV-returned hosts share the same parent domain as the seed hostname,
allowing hosts under a different domain suffix to be accepted. The suffix must
not be a public suffix (per the <code>Public Suffix List &lt;https://publicsuffix.org/list/&gt;</code>_). See the
:class:<code>~pymongo.synchronous.mongo_client.MongoClient</code> and
:class:<code>~pymongo.asynchronous.mongo_client.AsyncMongoClient</code> documentation for
security considerations.</li>
<li>Dropped support for MongoDB 4.2.</li>
<li>Added support for MongoDB 9.0.</li>
<li>PyPy support is deprecated and will be removed in a future release.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>640dd23</code></a> Prep 4.18.2 release (<a href="">#3066</a>)</li>
<li><a href=""><code>6a0ec65</code></a> Update changelog for CVE-2026-88029 reference (<a href="">#3049</a>)</li>
<li><a href=""><code>44be553</code></a> BUMP 4.18.2.dev0</li>
<li><a href=""><code>127d140</code></a> PYTHON-6085 Prep for 4.18.1 release (<a href="">#3047</a>)</li>
<li><a href=""><code>fa67658</code></a> PYTHON-5994 Use exact match for file ID in GridFS delete methods (<a href="">#3046</a>)</li>
<li><a href=""><code>1011e57</code></a> Prep branch v4.18</li>
<li><a href=""><code>4dd7303</code></a> PYTHON-6076 Request workflows permission in create-release-branch (<a href="">#3039</a>)</li>
<li><a href=""><code>e66da83</code></a> PYTHON-5956 Use shared python/setup action for CI setup (<a href="">#2990</a>)</li>
<li><a href=""><code>22a2ec8</code></a> PYTHON-6021 Move _write_concern_for_cmd into BaseObject (<a href="">#3036</a>)</li>
<li><a href=""><code>2a4a004</code></a> PYTHON-5874 Fix test_fork.py failures on Python 3.15 due to fork() Deprecatio...</li>
<li>Additional commits viewable in <a href="https://github.com/mongodb/mongo-python-driver/compare/4.15.2...4.18.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pymongo&package-manager=uv&previous-version=4.15.2&new-version=4.18.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/lukasturcani/stk/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a06f03b7d9e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
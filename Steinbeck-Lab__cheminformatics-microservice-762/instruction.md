# Issue

**Title:** chore(deps): bump axios from 1.13.6 to 1.15.0 in /frontend

## Description

Bumps [axios](https://github.com/axios/axios) from 1.13.6 to 1.15.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/axios/axios/releases">axios's releases</a>.</em></p>
<blockquote>
<h2>v1.15.0</h2>
<p>This release delivers two critical security patches, adds runtime support for Deno and Bun, and includes significant CI hardening, documentation improvements, and routine dependency updates.</p>
<h2>⚠️ Important Changes</h2>
<ul>
<li><strong>Deprecation:</strong> <code>url.parse()</code> usage has been replaced to address Node.js deprecation warnings. If you are on a recent version of Node.js, this resolves console warnings you may have been seeing. (<strong><a href="">#10625</a></strong>)</li>
</ul>
<h2>🔒 Security Fixes</h2>
<ul>
<li><strong>Proxy Handling:</strong> Fixed a <code>no_proxy</code> hostname normalisation bypass that could lead to Server-Side Request Forgery (SSRF). (<strong><a href="">#10661</a></strong>)</li>
<li><strong>Header Injection:</strong> Fixed an unrestricted cloud metadata exfiltration vulnerability via a header injection chain. (<strong><a href="">#10660</a></strong>)</li>
</ul>
<h2>🚀 New Features</h2>
<ul>
<li><strong>Runtime Support:</strong> Added compatibility checks and documentation for Deno and Bun environments. (<strong><a href="">#10652</a></strong>, <strong><a href="">#10653</a></strong>)</li>
</ul>
<h2>🔧 Maintenance &amp; Chores</h2>
<ul>
<li><strong>CI Security:</strong> Hardened workflow permissions to least privilege, added the <code>zizmor</code> security scanner, pinned action versions, and gated npm publishing with OIDC and environment protection. (<strong><a href="">#10618</a></strong>, <strong><a href="">#10619</a></strong>, <strong><a href="">#10627</a></strong>, <strong><a href="">#10637</a></strong>, <strong><a href="">#10666</a></strong>)</li>
<li><strong>Dependencies:</strong> Bumped <code>serialize-javascript</code>, <code>handlebars</code>, <code>picomatch</code>, <code>vite</code>, and <code>denoland/setup-deno</code> to latest versions. Added a 7-day Dependabot cooldown period. (<strong><a href="">#10574</a></strong>, <strong><a href="">#10572</a></strong>, <strong><a href="">#10568</a></strong>, <strong><a href="">#10663</a></strong>, <strong><a href="">#10664</a></strong>, <strong><a href="">#10665</a></strong>, <strong><a href="">#10669</a></strong>, <strong><a href="">#10670</a></strong>, <strong><a href="">#10616</a></strong>)</li>
<li><strong>Documentation:</strong> Unified docs, improved <code>beforeRedirect</code> credential leakage example, clarified <code>withCredentials</code>/<code>withXSRFToken</code> behaviour, HTTP/2 support notes, async/await timeout error handling, header case preservation, and various typo fixes. (<strong><a href="">#10649</a></strong>, <strong><a href="">#10624</a></strong>, <strong><a href="">#7452</a></strong>, <strong><a href="">#7471</a></strong>, <strong><a href="">#10654</a></strong>, <strong><a href="">#10644</a></strong>, <strong><a href="">#10589</a></strong>)</li>
<li><strong>Housekeeping:</strong> Removed stale files, regenerated lockfile, and updated sponsor scripts and blocks. (<strong><a href="">#10584</a></strong>, <strong><a href="">#10650</a></strong>, <strong><a href="">#10582</a></strong>, <strong><a href="">#10640</a></strong>, <strong><a href="">#10659</a></strong>, <strong><a href="">#10668</a></strong>)</li>
<li><strong>Tests:</strong> Added regression coverage for urlencoded <code>Content-Type</code> casing. (<strong><a href="">#10573</a></strong>)</li>
</ul>
<h2>🌟 New Contributors</h2>
<p>We are thrilled to welcome our new contributors. Thank you for helping improve Axios:</p>
<ul>
<li><strong><a href="https://github.com/raashish1601"><code>@​raashish1601</code></a></strong> (<strong><a href="">#10573</a></strong>)</li>
<li><strong><a href="https://github.com/Kilros0817"><code>@​Kilros0817</code></a></strong> (<strong><a href="">#10625</a></strong>)</li>
<li><strong><a href="https://github.com/ashstrc"><code>@​ashstrc</code></a></strong> (<strong><a href="">#10624</a></strong>)</li>
<li><strong><a href="https://github.com/Abhi3975"><code>@​Abhi3975</code></a></strong> (<strong><a href="">#10589</a></strong>)</li>
<li><strong><a href="https://github.com/theamodhshetty"><code>@​theamodhshetty</code></a></strong> (<strong><a href="">#7452</a></strong>)</li>
</ul>
<h2>v1.14.0</h2>
<p>This release focuses on compatibility fixes, adapter stability improvements, and test/tooling modernisation.</p>
<h2>⚠️ Important Changes</h2>
<ul>
<li><strong>Breaking Changes:</strong> None identified in this release.</li>
<li><strong>Action Required:</strong> If you rely on env-based proxy behaviour or CJS resolution edge-cases, validate your integration after upgrade (notably <code>proxy-from-env</code> v2 alignment and <code>main</code> entry compatibility fix).</li>
</ul>
<h2>🚀 New Features</h2>
<ul>
<li><strong>Runtime Features:</strong> No new end-user features were introduced in this release.</li>
<li><strong>Test Coverage Expansion:</strong> Added broader smoke/module test coverage for CJS and ESM package usage. (<a href="">#7510</a>)</li>
</ul>
<h2>🐛 Bug Fixes</h2>
<ul>
<li><strong>Headers:</strong> Trim trailing CRLF in normalised header values. (<a href="">#7456</a>)</li>
<li><strong>HTTP/2:</strong> Close detached HTTP/2 sessions on timeout to avoid lingering sessions. (<a href="">#7457</a>)</li>
<li><strong>Fetch Adapter:</strong> Cancel <code>ReadableStream</code> created during request-stream capability probing to prevent async resource leaks. (<a href="">#7515</a>)</li>
<li><strong>Proxy Handling:</strong> Fixed env proxy behavior with <code>proxy-from-env</code> v2 usage. (<a href="">#7499</a>)</li>
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
<h2><a href="https://github.com/axios/axios/compare/v1.13.2...v1.13.3">1.13.3</a> (2026-01-20)</h2>
<h3>Bug Fixes</h3>
<ul>
<li><strong>http2:</strong> Use port 443 for HTTPS connections by default. (<a href="">#7256</a>) (<a href="">d7e6065</a>)</li>
<li><strong>interceptor:</strong> handle the error in the same interceptor (<a href="">#6269</a>) (<a href="">5945e40</a>)</li>
<li>main field in package.json should correspond to cjs artifacts (<a href="">#5756</a>) (<a href="">7373fbf</a>)</li>
<li><strong>package.json:</strong> add 'bun' package.json 'exports' condition. Load the Node.js build in Bun instead of the browser build (<a href="">#5754</a>) (<a href="">b89217e</a>)</li>
<li>silentJSONParsing=false should throw on invalid JSON (<a href="">#7253</a>) (<a href="">#7257</a>) (<a href="">7d19335</a>)</li>
<li>turn AxiosError into a native error (<a href="">#5394</a>) (<a href="">#5558</a>) (<a href="">1c6a86d</a>)</li>
<li><strong>types:</strong> add handlers to AxiosInterceptorManager interface (<a href="">#5551</a>) (<a href="">8d1271b</a>)</li>
<li><strong>types:</strong> restore AxiosError.cause type from unknown to Error (<a href="">#7327</a>) (<a href="">d8233d9</a>)</li>
<li>unclear error message is thrown when specifying an empty proxy authorization (<a href="">#6314</a>) (<a href="">6ef867e</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li>add <code>undefined</code> as a value in AxiosRequestConfig (<a href="">#5560</a>) (<a href="">095033c</a>)</li>
<li>add automatic minor and patch upgrades to dependabot (<a href="">#6053</a>) (<a href="">65a7584</a>)</li>
<li>add Node.js coverage script using c8 (closes <a href="">#7289</a>) (<a href="">#7294</a>) (<a href="">ec9d94e</a>)</li>
<li>added copilot instructions (<a href="">3f83143</a>)</li>
<li>compatibility with frozen prototypes (<a href="">#6265</a>) (<a href="">860e033</a>)</li>
<li>enhance pipeFileToResponse with error handling (<a href="">#7169</a>) (<a href="">88d7884</a>)</li>
<li><strong>types:</strong> Intellisense for string literals in a widened union (<a href="">#6134</a>) (<a href="">f73474d</a>), closes <a href="">microsoft/TypeScript#33471</a></li>
</ul>
<h3>Reverts</h3>
<ul>
<li>Revert &quot;fix: silentJSONParsing=false should throw on invalid JSON (<a href="">#7253</a>) (<a href="">#7</a>…&quot; (<a href="">#7298</a>) (<a href="">a4230f5</a>), closes <a href="">#7253</a> <a href="">#7</a> <a href="">#7298</a></li>
<li><strong>deps:</strong> bump peter-evans/create-pull-request from 7 to 8 in the github-actions group (<a href="">#7334</a>) (<a href="">2d6ad5e</a>)</li>
</ul>
<h3>Contributors to this release</h3>
<ul>
<li><!-- raw HTML omitted --> <a href="https://github.com/ashvin2005" title="+1752/-4 (  )">Ashvin Tiwari</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/mochinikunj" title="+940/-12 (  )">Nikunj Mochi</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/imanchalsingh" title="+544/-102 (  )">Anchal Singh</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/jasonsaayman" title="+317/-73 (  )">jasonsaayman</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/brodo" title="+99/-120 ( )">Julian Dax</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/AKASHDHARDUBEY" title="+167/-0 (  )">Akash Dhar Dubey</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/madhumitaaa" title="+20/-68 ( )">Madhumita</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/Tackoil" title="+80/-2 ( )">Tackoil</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/justindhillon" title="+41/-41 (  )">Justin Dhillon</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/Rudrxxx" title="+71/-2 ( )">Rudransh</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/WuMingDao" title="+36/-36 ( )">WuMingDao</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/codenomnom" title="+70/-0 (  )">codenomnom</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/Nandann018-ux" title="+60/-10 ( )">Nandan Acharya</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/KernelDeimos" title="+22/-40 ( )">Eric Dubé</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/tiborpilz" title="+40/-4 ( )">Tibor Pilz</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/joaoGabriel55" title="+31/-4 ( )">Gabriel Quaresma</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/turadg" title="+23/-6 ( )">Turadg Aleahmad</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>772a4e5</code></a> chore(release): prepare release 1.15.0 (<a href="">#10671</a>)</li>
<li><a href=""><code>4b07137</code></a> chore(deps-dev): bump vite from 8.0.0 to 8.0.5 in /tests/smoke/esm (<a href="">#10663</a>)</li>
<li><a href=""><code>51e57b3</code></a> chore(deps-dev): bump vite from 8.0.2 to 8.0.5 (<a href="">#10664</a>)</li>
<li><a href=""><code>fba1a77</code></a> chore(deps-dev): bump vite from 8.0.2 to 8.0.5 in /tests/module/esm (<a href="">#10665</a>)</li>
<li><a href=""><code>0bf6e28</code></a> chore(deps): bump denoland/setup-deno in the github-actions group (<a href="">#10669</a>)</li>
<li><a href=""><code>8107157</code></a> chore(deps-dev): bump the development_dependencies group with 4 updates (<a href="">#10670</a>)</li>
<li><a href=""><code>e66530e</code></a> ci: require npm-publish environment for releases (<a href="">#10666</a>)</li>
<li><a href=""><code>49f23cb</code></a> chore(sponsor): update sponsor block (<a href="">#10668</a>)</li>
<li><a href=""><code>3631854</code></a> fix: unrestricted cloud metadata exfiltration via header injection chain (<a href="">#10</a>...</li>
<li><a href=""><code>fb3befb</code></a> fix: no_proxy hostname normalization bypass leads to ssrf (<a href="">#10661</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/axios/axios/compare/v1.13.6...v1.15.0">compare view</a></li>
</ul>
</details>
<details>
<summary>Install script changes</summary>
<p>This version modifies <code>prepare</code> script that runs during installation. Review the package contents before updating.</p>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=axios&package-manager=npm_and_yarn&previous-version=1.13.6&new-version=1.15.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/Steinbeck-Lab/cheminformatics-microservice/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1efc95013336`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
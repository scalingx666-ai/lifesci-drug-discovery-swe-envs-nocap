# Issue

**Title:** chore(deps): bump axios from 1.8.4 to 1.12.0 in /frontend

## Description

Bumps [axios](https://github.com/axios/axios) from 1.8.4 to 1.12.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/axios/axios/releases">axios's releases</a>.</em></p>
<blockquote>
<h2>Release v1.12.0</h2>
<h2>Release notes:</h2>
<h3>Bug Fixes</h3>
<ul>
<li>adding build artifacts (<a href="">9ec86de</a>)</li>
<li>dont add dist on release (<a href="">a2edc36</a>)</li>
<li><strong>fetch-adapter:</strong> set correct Content-Type for Node FormData (<a href="">#6998</a>) (<a href="">a9f47af</a>)</li>
<li><strong>node:</strong> enforce maxContentLength for data: URLs (<a href="">#7011</a>) (<a href="">945435f</a>)</li>
<li>package exports (<a href="">#5627</a>) (<a href="">aa78ac2</a>)</li>
<li><strong>params:</strong> removing '[' and ']' from URL encode exclude characters (<a href="">#3316</a>) (<a href="">#5715</a>) (<a href="">6d84189</a>)</li>
<li>release pr run (<a href="">fd7f404</a>)</li>
<li><strong>types:</strong> change the type guard on isCancel (<a href="">#5595</a>) (<a href="">0dbb7fd</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>adapter:</strong> surface low‑level network error details; attach original error via cause (<a href="">#6982</a>) (<a href="">78b290c</a>)</li>
<li><strong>fetch:</strong> add fetch, Request, Response env config variables for the adapter; (<a href="">#7003</a>) (<a href="">c959ff2</a>)</li>
<li>support reviver on JSON.parse (<a href="">#5926</a>) (<a href="">2a97634</a>), closes <a href="">#5924</a></li>
<li><strong>types:</strong> extend AxiosResponse interface to include custom headers type (<a href="">#6782</a>) (<a href="">7960d34</a>)</li>
</ul>
<h3>Contributors to this release</h3>
<ul>
<li><!-- raw HTML omitted --> <a href="https://github.com/WillianAgostini" title="+132/-16760 (   )">Willian Agostini</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/DigitalBrainJS" title="+4263/-293 (  )">Dmitriy Mozgovoy</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/mkhani01" title="+111/-15 ( )">khani</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/AmeerAssadi" title="+123/-0 ( )">Ameer Assadi</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/emiedonmokumo" title="+55/-35 ( )">Emiedonmokumo Dick-Boro</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/opsysdebug" title="+8/-8 ( )">Zeroday BYTE</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/jasonsaayman" title="+7/-7 (  )">Jason Saayman</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/HealGaren" title="+5/-7 ( )">최예찬</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/gligorkot" title="+3/-1 ( )">Gligor Kotushevski</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/adimit" title="+2/-1 ( )">Aleksandar Dimitrov</a></li>
</ul>
<h2>Release v1.11.0</h2>
<h2>Release notes:</h2>
<h3>Bug Fixes</h3>
<ul>
<li>form-data npm pakcage (<a href="">#6970</a>) (<a href="">e72c193</a>)</li>
<li>prevent RangeError when using large Buffers (<a href="">#6961</a>) (<a href="">a2214ca</a>)</li>
<li><strong>types:</strong> resolve type discrepancies between ESM and CJS TypeScript declaration files (<a href="">#6956</a>) (<a href="">8517aa1</a>)</li>
</ul>
<h3>Contributors to this release</h3>
<ul>
<li><!-- raw HTML omitted --> <a href="https://github.com/izzygld" title="+186/-93 ( )">izzy goldman</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/manishsahanidev" title="+70/-0 ( )">Manish Sahani</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/noritaka1166" title="+12/-10 (  )">Noritaka Kobayashi</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/jrnail23" title="+13/-2 ( )">James Nail</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/Tejaswi1305" title="+1/-1 ( )">Tejaswi1305</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/axios/axios/blob/v1.x/CHANGELOG.md">axios's changelog</a>.</em></p>
<blockquote>
<h1><a href="https://github.com/axios/axios/compare/v1.11.0...v1.12.0">1.12.0</a> (2025-09-11)</h1>
<h3>Bug Fixes</h3>
<ul>
<li>adding build artifacts (<a href="">9ec86de</a>)</li>
<li>dont add dist on release (<a href="">a2edc36</a>)</li>
<li><strong>fetch-adapter:</strong> set correct Content-Type for Node FormData (<a href="">#6998</a>) (<a href="">a9f47af</a>)</li>
<li><strong>node:</strong> enforce maxContentLength for data: URLs (<a href="">#7011</a>) (<a href="">945435f</a>)</li>
<li>package exports (<a href="">#5627</a>) (<a href="">aa78ac2</a>)</li>
<li><strong>params:</strong> removing '[' and ']' from URL encode exclude characters (<a href="">#3316</a>) (<a href="">#5715</a>) (<a href="">6d84189</a>)</li>
<li>release pr run (<a href="">fd7f404</a>)</li>
<li><strong>types:</strong> change the type guard on isCancel (<a href="">#5595</a>) (<a href="">0dbb7fd</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>adapter:</strong> surface low‑level network error details; attach original error via cause (<a href="">#6982</a>) (<a href="">78b290c</a>)</li>
<li><strong>fetch:</strong> add fetch, Request, Response env config variables for the adapter; (<a href="">#7003</a>) (<a href="">c959ff2</a>)</li>
<li>support reviver on JSON.parse (<a href="">#5926</a>) (<a href="">2a97634</a>), closes <a href="">#5924</a></li>
<li><strong>types:</strong> extend AxiosResponse interface to include custom headers type (<a href="">#6782</a>) (<a href="">7960d34</a>)</li>
</ul>
<h3>Contributors to this release</h3>
<ul>
<li><!-- raw HTML omitted --> <a href="https://github.com/WillianAgostini" title="+132/-16760 (   )">Willian Agostini</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/DigitalBrainJS" title="+4263/-293 (  )">Dmitriy Mozgovoy</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/mkhani01" title="+111/-15 ( )">khani</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/AmeerAssadi" title="+123/-0 ( )">Ameer Assadi</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/emiedonmokumo" title="+55/-35 ( )">Emiedonmokumo Dick-Boro</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/opsysdebug" title="+8/-8 ( )">Zeroday BYTE</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/jasonsaayman" title="+7/-7 (  )">Jason Saayman</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/HealGaren" title="+5/-7 ( )">최예찬</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/gligorkot" title="+3/-1 ( )">Gligor Kotushevski</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/adimit" title="+2/-1 ( )">Aleksandar Dimitrov</a></li>
</ul>
<h1><a href="https://github.com/axios/axios/compare/v1.10.0...v1.11.0">1.11.0</a> (2025-07-22)</h1>
<h3>Bug Fixes</h3>
<ul>
<li>form-data npm pakcage (<a href="">#6970</a>) (<a href="">e72c193</a>)</li>
<li>prevent RangeError when using large Buffers (<a href="">#6961</a>) (<a href="">a2214ca</a>)</li>
<li><strong>types:</strong> resolve type discrepancies between ESM and CJS TypeScript declaration files (<a href="">#6956</a>) (<a href="">8517aa1</a>)</li>
</ul>
<h3>Contributors to this release</h3>
<ul>
<li><!-- raw HTML omitted --> <a href="https://github.com/izzygld" title="+186/-93 ( )">izzy goldman</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/manishsahanidev" title="+70/-0 ( )">Manish Sahani</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/noritaka1166" title="+12/-10 (  )">Noritaka Kobayashi</a></li>
<li><!-- raw HTML omitted --> <a href="https://github.com/jrnail23" title="+13/-2 ( )">James Nail</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>0d8ad6e</code></a> chore(release): v1.12.0 (<a href="">#7013</a>)</li>
<li><a href=""><code>fd7f404</code></a> fix: release pr run</li>
<li><a href=""><code>a2edc36</code></a> fix: dont add dist on release</li>
<li><a href=""><code>9ec86de</code></a> fix: adding build artifacts</li>
<li><a href=""><code>945435f</code></a> fix(node): enforce maxContentLength for data: URLs (<a href="">#7011</a>)</li>
<li><a href=""><code>28e5e30</code></a> chore(sponsor): update sponsor block (<a href="">#7005</a>)</li>
<li><a href=""><code>d03f245</code></a> chore(CI): fixed release info script to use npm registry instead of git as fi...</li>
<li><a href=""><code>a0bc911</code></a> chore: removing dist files from src (<a href="">#7002</a>)</li>
<li><a href=""><code>c959ff2</code></a> feat(fetch): add fetch, Request, Response env config variables for the adapte...</li>
<li><a href=""><code>a9f47af</code></a> fix(fetch-adapter): set correct Content-Type for Node FormData (<a href="">#6998</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/axios/axios/compare/v1.8.4...v1.12.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=axios&package-manager=npm_and_yarn&previous-version=1.8.4&new-version=1.12.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/Steinbeck-Lab/cheminformatics-microservice/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31d0a8afdfbd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
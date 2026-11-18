# Issue

**Title:** Bump mendeleev from 1.1.0 to 1.2.0

## Description

Bumps [mendeleev](https://github.com/lmmentel/mendeleev) from 1.1.0 to 1.2.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/lmmentel/mendeleev/releases">mendeleev's releases</a>.</em></p>
<blockquote>
<h2>v1.2.0</h2>
<h2>What's Changed</h2>
<ul>
<li>[ENH] Add units for stored properties by <a href="https://github.com/lmmentel"><code>@​lmmentel</code></a> in <a href="">lmmentel/mendeleev#239</a></li>
<li>Change mendeleev installation command to conda-forge by <a href="https://github.com/lmmentel"><code>@​lmmentel</code></a> in <a href="">lmmentel/mendeleev#245</a></li>
<li>Documentation restructure and sphinx-immaterial migration by <a href="https://github.com/lmmentel"><code>@​lmmentel</code></a> in <a href="">lmmentel/mendeleev#248</a></li>
<li>[MNT] Drop python 3.9 and add 3.14 by <a href="https://github.com/lmmentel"><code>@​lmmentel</code></a> in <a href="">lmmentel/mendeleev#246</a></li>
<li>fix: handle NaN colors in plotly create_tile by <a href="https://github.com/lmmentel"><code>@​lmmentel</code></a> in <a href="">lmmentel/mendeleev#266</a></li>
<li>deps: consolidate all dependabot updates by <a href="https://github.com/lmmentel"><code>@​lmmentel</code></a> in <a href="">lmmentel/mendeleev#267</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/lmmentel/mendeleev/compare/v1.1.0...v1.2.0">https://github.com/lmmentel/mendeleev/compare/v1.1.0...v1.2.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/lmmentel/mendeleev/blob/master/CHANGES.rst">mendeleev's changelog</a>.</em></p>
<blockquote>
<h2>v1.2.0 (27.07.2026)</h2>
<ul>
<li>[ENH] Add units for stored properties by :user:<code>@lmmentel</code> in :pr:<code>239</code></li>
<li>[FIX] Handle NaN colors in plotly create_tile by :user:<code>@lmmentel</code> in :pr:<code>266</code></li>
<li>[MNT] Drop python 3.9 and add 3.14 by :user:<code>@lmmentel</code> in :pr:<code>246</code></li>
<li>[MNT] Documentation restructure and sphinx-immaterial migration by :user:<code>@lmmentel</code> in :pr:<code>248</code></li>
<li>[MNT] Change mendeleev installation command to conda-forge by :user:<code>@lmmentel</code> in :pr:<code>245</code></li>
<li>[MNT] Automate mendeleev-data sync on release by :user:<code>@lmmentel</code></li>
<li>[MNT] Consolidate dependabot updates into single lock update by :user:<code>@lmmentel</code> in :pr:<code>267</code></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6157623</code></a> Bump version: 1.1.0 → 1.2.0</li>
<li><a href=""><code>3686e8d</code></a> remove install.rst from .bumpversion.cfg</li>
<li><a href=""><code>609545e</code></a> remove quick.rst from .bumpversion.cfg</li>
<li><a href=""><code>3f20c0b</code></a> Automate mendeleev-data sync on release</li>
<li><a href=""><code>3cb6351</code></a> deps: consolidate dependabot updates into single lock update (<a href="">#267</a>)</li>
<li><a href=""><code>c8afce9</code></a> fix: handle NaN colors in plotly create_tile (<a href="">#266</a>)</li>
<li><a href=""><code>295a804</code></a> [MNT] Drop python 3.9 and add 3.14 (<a href="">#246</a>)</li>
<li><a href=""><code>4f08354</code></a> Documentation restructure and sphinx-immaterial migration (<a href="">#248</a>)</li>
<li><a href=""><code>580e340</code></a> Change mendeleev installation command to conda-forge (<a href="">#245</a>)</li>
<li><a href=""><code>4e02078</code></a> [ENH] Add units for stored properties (<a href="">#239</a>)</li>
<li>See full diff in <a href="https://github.com/lmmentel/mendeleev/compare/v1.1.0...v1.2.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=mendeleev&package-manager=pip&previous-version=1.1.0&new-version=1.2.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8cc09f0992c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
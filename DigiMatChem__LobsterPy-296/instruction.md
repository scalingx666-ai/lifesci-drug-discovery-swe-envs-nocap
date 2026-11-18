# Issue

**Title:** Bump mendeleev from 0.16.2 to 0.17.0

## Description

Bumps [mendeleev](https://github.com/lmmentel/mendeleev) from 0.16.2 to 0.17.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/lmmentel/mendeleev/blob/master/CHANGES.rst">mendeleev's changelog</a>.</em></p>
<blockquote>
<h2>v0.17.0 (05.06.2024)</h2>
<ul>
<li>[ENH] Add data export to various formats by :user:<code>@lmmentel</code> in :pr:<code>151</code></li>
<li>[ENH] Create metadata table for stored properties by :user:<code>@lmmentel</code> in :pr:<code>156</code></li>
<li>[ENH] Update Isotope.half_life_unit values by :user:<code>@lmmentel</code> in :pr:<code>160</code></li>
<li>[DOC] Add section for alternative implementation of mendeleev to README by :user:<code>@lmmentel</code> in :pr:<code>163</code></li>
<li>[DOC] Add Mendeleev.jl to README by :user:<code>@lmmentel</code> in :pr:<code>164</code></li>
<li>[FIX] Use read-only SQLite connection by :user:<code>@jan-janssen</code> in :pr:<code>165</code></li>
<li>[FIX] Fix fetch_table to be compatible across major versions of pandas and sqlalchemy by :user:<code>@lmmentel</code> in :pr:<code>159</code></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>630be51</code></a> Bump version: 0.16.2 → 0.17.0</li>
<li><a href=""><code>c15a245</code></a> update chagelog</li>
<li><a href=""><code>fd3f12f</code></a> Fix fetch_table to be compatiple across pandas and sqlalchemy versions (<a href="">#159</a>)</li>
<li><a href=""><code>55c2244</code></a> Use read-only SQLite connection (<a href="">#165</a>)</li>
<li><a href=""><code>393692c</code></a> add Mendeleev.jl (<a href="">#164</a>)</li>
<li><a href=""><code>6af017d</code></a> Add section for alternative implementation of mendeleev to README (<a href="">#163</a>)</li>
<li><a href=""><code>88510cc</code></a> Update Isotope.half_life_unit values (<a href="">#160</a>)</li>
<li><a href=""><code>b04a6f0</code></a> Create metadata table for stored properties (<a href="">#156</a>)</li>
<li><a href=""><code>3945030</code></a> Add data export to various formats (<a href="">#151</a>)</li>
<li>See full diff in <a href="https://github.com/lmmentel/mendeleev/compare/v0.16.2...v0.17.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=mendeleev&package-manager=pip&previous-version=0.16.2&new-version=0.17.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62b8b4fcc471`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
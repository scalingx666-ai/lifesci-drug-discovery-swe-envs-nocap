# Issue

**Title:** chore(deps): bump js-yaml in /frontend

## Description

Bumps  and [js-yaml](https://github.com/nodeca/js-yaml). These dependencies needed to be updated together.
Updates `js-yaml` from 3.14.1 to 3.14.2
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/nodeca/js-yaml/blob/master/CHANGELOG.md">js-yaml's changelog</a>.</em></p>
<blockquote>
<h2>[3.14.2] - 2025-11-15</h2>
<h3>Security</h3>
<ul>
<li>Backported v4.1.1 fix to v3</li>
</ul>
<h2>[4.1.1] - 2025-11-12</h2>
<h3>Security</h3>
<ul>
<li>Fix prototype pollution issue in yaml merge (&lt;&lt;) operator.</li>
</ul>
<h2>[4.1.0] - 2021-04-15</h2>
<h3>Added</h3>
<ul>
<li>Types are now exported as <code>yaml.types.XXX</code>.</li>
<li>Every type now has <code>options</code> property with original arguments kept as they were
(see <code>yaml.types.int.options</code> as an example).</li>
</ul>
<h3>Changed</h3>
<ul>
<li><code>Schema.extend()</code> now keeps old type order in case of conflicts
(e.g. Schema.extend([ a, b, c ]).extend([ b, a, d ]) is now ordered as <code>abcd</code> instead of <code>cbad</code>).</li>
</ul>
<h2>[4.0.0] - 2021-01-03</h2>
<h3>Changed</h3>
<ul>
<li>Check <a href="https://github.com/nodeca/js-yaml/blob/master/migrate_v3_to_v4.md">migration guide</a> to see details for all breaking changes.</li>
<li>Breaking: &quot;unsafe&quot; tags <code>!!js/function</code>, <code>!!js/regexp</code>, <code>!!js/undefined</code> are
moved to <a href="https://github.com/nodeca/js-yaml-js-types">js-yaml-js-types</a> package.</li>
<li>Breaking: removed <code>safe*</code> functions. Use <code>load</code>, <code>loadAll</code>, <code>dump</code>
instead which are all now safe by default.</li>
<li><code>yaml.DEFAULT_SAFE_SCHEMA</code> and <code>yaml.DEFAULT_FULL_SCHEMA</code> are removed, use
<code>yaml.DEFAULT_SCHEMA</code> instead.</li>
<li><code>yaml.Schema.create(schema, tags)</code> is removed, use <code>schema.extend(tags)</code> instead.</li>
<li><code>!!binary</code> now always mapped to <code>Uint8Array</code> on load.</li>
<li>Reduced nesting of <code>/lib</code> folder.</li>
<li>Parse numbers according to YAML 1.2 instead of YAML 1.1 (<code>01234</code> is now decimal,
<code>0o1234</code> is octal, <code>1:23</code> is parsed as string instead of base60).</li>
<li><code>dump()</code> no longer quotes <code>:</code>, <code>[</code>, <code>]</code>, <code>(</code>, <code>)</code> except when necessary, <a href="">#470</a>, <a href="">#557</a>.</li>
<li>Line and column in exceptions are now formatted as <code>(X:Y)</code> instead of
<code>at line X, column Y</code> (also present in compact format), <a href="">#332</a>.</li>
<li>Code snippet created in exceptions now contains multiple lines with line numbers.</li>
<li><code>dump()</code> now serializes <code>undefined</code> as <code>null</code> in collections and removes keys with
<code>undefined</code> in mappings, <a href="">#571</a>.</li>
<li><code>dump()</code> with <code>skipInvalid=true</code> now serializes invalid items in collections as null.</li>
<li>Custom tags starting with <code>!</code> are now dumped as <code>!tag</code> instead of <code>!&lt;!tag&gt;</code>, <a href="">#576</a>.</li>
<li>Custom tags starting with <code>tag:yaml.org,2002:</code> are now shorthanded using <code>!!</code>, <a href="">#258</a>.</li>
</ul>
<h3>Added</h3>
<ul>
<li>Added <code>.mjs</code> (es modules) support.</li>
<li>Added <code>quotingType</code> and <code>forceQuotes</code> options for dumper to configure
string literal style, <a href="">#290</a>, <a href="">#529</a>.</li>
<li>Added <code>styles: { '!!null': 'empty' }</code> option for dumper
(serializes <code>{ foo: null }</code> as &quot;<code>foo: </code>&quot;), <a href="">#570</a>.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9963d36</code></a> 3.14.2 released</li>
<li><a href=""><code>10d3c8e</code></a> dist rebuild</li>
<li><a href=""><code>5278870</code></a> fix prototype pollution in merge (&lt;&lt;) (<a href="">#731</a>)</li>
<li>See full diff in <a href="https://github.com/nodeca/js-yaml/compare/3.14.1...3.14.2">compare view</a></li>
</ul>
</details>
<br />

Updates `js-yaml` from 4.1.0 to 4.1.1
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/nodeca/js-yaml/blob/master/CHANGELOG.md">js-yaml's changelog</a>.</em></p>
<blockquote>
<h2>[3.14.2] - 2025-11-15</h2>
<h3>Security</h3>
<ul>
<li>Backported v4.1.1 fix to v3</li>
</ul>
<h2>[4.1.1] - 2025-11-12</h2>
<h3>Security</h3>
<ul>
<li>Fix prototype pollution issue in yaml merge (&lt;&lt;) operator.</li>
</ul>
<h2>[4.1.0] - 2021-04-15</h2>
<h3>Added</h3>
<ul>
<li>Types are now exported as <code>yaml.types.XXX</code>.</li>
<li>Every type now has <code>options</code> property with original arguments kept as they were
(see <code>yaml.types.int.options</code> as an example).</li>
</ul>
<h3>Changed</h3>
<ul>
<li><code>Schema.extend()</code> now keeps old type order in case of conflicts
(e.g. Schema.extend([ a, b, c ]).extend([ b, a, d ]) is now ordered as <code>abcd</code> instead of <code>cbad</code>).</li>
</ul>
<h2>[4.0.0] - 2021-01-03</h2>
<h3>Changed</h3>
<ul>
<li>Check <a href="https://github.com/nodeca/js-yaml/blob/master/migrate_v3_to_v4.md">migration guide</a> to see details for all breaking changes.</li>
<li>Breaking: &quot;unsafe&quot; tags <code>!!js/function</code>, <code>!!js/regexp</code>, <code>!!js/undefined</code> are
moved to <a href="https://github.com/nodeca/js-yaml-js-types">js-yaml-js-types</a> package.</li>
<li>Breaking: removed <code>safe*</code> functions. Use <code>load</code>, <code>loadAll</code>, <code>dump</code>
instead which are all now safe by default.</li>
<li><code>yaml.DEFAULT_SAFE_SCHEMA</code> and <code>yaml.DEFAULT_FULL_SCHEMA</code> are removed, use
<code>yaml.DEFAULT_SCHEMA</code> instead.</li>
<li><code>yaml.Schema.create(schema, tags)</code> is removed, use <code>schema.extend(tags)</code> instead.</li>
<li><code>!!binary</code> now always mapped to <code>Uint8Array</code> on load.</li>
<li>Reduced nesting of <code>/lib</code> folder.</li>
<li>Parse numbers according to YAML 1.2 instead of YAML 1.1 (<code>01234</code> is now decimal,
<code>0o1234</code> is octal, <code>1:23</code> is parsed as string instead of base60).</li>
<li><code>dump()</code> no longer quotes <code>:</code>, <code>[</code>, <code>]</code>, <code>(</code>, <code>)</code> except when necessary, <a href="">#470</a>, <a href="">#557</a>.</li>
<li>Line and column in exceptions are now formatted as <code>(X:Y)</code> instead of
<code>at line X, column Y</code> (also present in compact format), <a href="">#332</a>.</li>
<li>Code snippet created in exceptions now contains multiple lines with line numbers.</li>
<li><code>dump()</code> now serializes <code>undefined</code> as <code>null</code> in collections and removes keys with
<code>undefined</code> in mappings, <a href="">#571</a>.</li>
<li><code>dump()</code> with <code>skipInvalid=true</code> now serializes invalid items in collections as null.</li>
<li>Custom tags starting with <code>!</code> are now dumped as <code>!tag</code> instead of <code>!&lt;!tag&gt;</code>, <a href="">#576</a>.</li>
<li>Custom tags starting with <code>tag:yaml.org,2002:</code> are now shorthanded using <code>!!</code>, <a href="">#258</a>.</li>
</ul>
<h3>Added</h3>
<ul>
<li>Added <code>.mjs</code> (es modules) support.</li>
<li>Added <code>quotingType</code> and <code>forceQuotes</code> options for dumper to configure
string literal style, <a href="">#290</a>, <a href="">#529</a>.</li>
<li>Added <code>styles: { '!!null': 'empty' }</code> option for dumper
(serializes <code>{ foo: null }</code> as &quot;<code>foo: </code>&quot;), <a href="">#570</a>.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9963d36</code></a> 3.14.2 released</li>
<li><a href=""><code>10d3c8e</code></a> dist rebuild</li>
<li><a href=""><code>5278870</code></a> fix prototype pollution in merge (&lt;&lt;) (<a href="">#731</a>)</li>
<li>See full diff in <a href="https://github.com/nodeca/js-yaml/compare/3.14.1...3.14.2">compare view</a></li>
</ul>
</details>
<br />

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `745e55a4bc46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** build(deps): bump the uv group across 1 directory with 13 updates

## Description

Bumps the uv group with 13 updates in the / directory:

| Package | From | To |
| --- | --- | --- |
| [tornado](https://github.com/tornadoweb/tornado) | `6.5.8` | `6.6` |
| [black](https://github.com/psf/black) | `26.3.1` | `26.10.1` |
| [certifi](https://github.com/certifi/python-certifi) | `2025.1.31` | `2026.10.18` |
| [dnspython](https://github.com/rthalley/dnspython) | `2.7.0` | `2.9.0` |
| [filelock](https://github.com/tox-dev/filelock) | `3.18.0` | `4.2.1` |
| [gitpython](https://github.com/gitpython-developers/GitPython) | `3.1.61` | `3.2.1` |
| [jupyterlab](https://github.com/jupyterlab/jupyterlab) | `4.5.10` | `4.6.5` |
| [msgpack](https://github.com/msgpack/msgpack-python) | `1.2.1` | `1.2.3` |
| [nbconvert](https://github.com/jupyter/nbconvert) | `7.17.1` | `7.17.2` |
| [pillow](https://github.com/python-pillow/Pillow) | `12.3.0` | `13.0.0` |
| [pymongo](https://github.com/mongodb/mongo-python-driver) | `4.10.1` | `4.18.3` |
| [virtualenv](https://github.com/pypa/virtualenv) | `20.30.0` | `21.15.2` |
| [werkzeug](https://github.com/pallets/werkzeug) | `3.0.6` | `3.1.9` |

Updates `tornado` from 6.5.8 to 6.6
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/tornadoweb/tornado/blob/master/docs/releases.rst">tornado's changelog</a>.</em></p>
<blockquote>
<h1>Release notes</h1>
<p>.. toctree::
:maxdepth: 2</p>
<p>releases/v6.6.0
releases/v6.5.10
releases/v6.5.9
releases/v6.5.8
releases/v6.5.7
releases/v6.5.6
releases/v6.5.5
releases/v6.5.4
releases/v6.5.3
releases/v6.5.2
releases/v6.5.1
releases/v6.5.0
releases/v6.4.2
releases/v6.4.1
releases/v6.4.0
releases/v6.3.3
releases/v6.3.2
releases/v6.3.1
releases/v6.3.0
releases/v6.2.0
releases/v6.1.0
releases/v6.0.4
releases/v6.0.3
releases/v6.0.2
releases/v6.0.1
releases/v6.0.0
releases/v5.1.1
releases/v5.1.0
releases/v5.0.2
releases/v5.0.1
releases/v5.0.0
releases/v4.5.3
releases/v4.5.2
releases/v4.5.1
releases/v4.5.0
releases/v4.4.3
releases/v4.4.2
releases/v4.4.1
releases/v4.4.0
releases/v4.3.0
releases/v4.2.1
releases/v4.2.0
releases/v4.1.0
releases/v4.0.2</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e2b0f45</code></a> Merge pull request <a href="">#3831</a> from bdarnell/final-6.6</li>
<li><a href=""><code>90c4e3f</code></a> Version bump for 6.6 final release</li>
<li><a href=""><code>ec17353</code></a> Merge pull request <a href="">#3828</a> from bdarnell/downstream-ci-66</li>
<li><a href=""><code>15f66b0</code></a> ci: Add explicit read permission to CI jobs</li>
<li><a href=""><code>4446441</code></a> ci: Run the downstream testbed on a wheel built in the same run</li>
<li><a href=""><code>c2e24d2</code></a> Merge pull request <a href="">#3823</a> from bdarnell/claude/project-thread-uzh2s8</li>
<li><a href=""><code>c2d8884</code></a> test: Add pre-6.3 security fixes to the corpus</li>
<li><a href=""><code>de32687</code></a> test: Add a regression corpus of past security fixes</li>
<li><a href=""><code>7848790</code></a> maint: Add pre-tag checks and release instructions</li>
<li><a href=""><code>f14321e</code></a> ci: Compare benchmarks with the base branch on every PR</li>
<li>Additional commits viewable in <a href="https://github.com/tornadoweb/tornado/compare/v6.5.8...v6.6.0">compare view</a></li>
</ul>
</details>
<br />

Updates `black` from 26.3.1 to 26.10.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/psf/black/releases">black's releases</a>.</em></p>
<blockquote>
<h2>26.10.1</h2>
<h3>Highlights</h3>
<p>This release fixes a security issue in Black's bundled GitHub Action. Repositories that
use the action are encouraged to update to the latest version of Black immediately. This
update is received automatically when using <code>psf/black@stable</code>, and is independent of
the version of Black installed by the action.</p>
<p>When the GitHub Action reads version specifiers from <code>tool.black.required-version</code>, it
now only accepts released versions of Black, as it already did for <code>black</code> requirements
in dependency lists. Other values, such as URL references, are now rejected. This issue
has been registered as <code>GHSA-cg8m-r9f2-5wm2</code>; a CVE identifier is pending.</p>
<h3>Stable style</h3>
<ul>
<li>Fix a long Jupyter notebook assignment magic (for example <code>x = !ls -la</code>) being wrapped
in parentheses, which IPython can no longer run; such cells are now left unchanged
(<a href="">#5481</a>)</li>
<li>Keep repeated lines outside the selected <code>--line-ranges</code> unchanged (<a href="">#5436</a>)</li>
<li>Fix <code>--line-ranges</code> formatting lines that follow a statement when formatting joins or
re-indents that statement (<a href="">#5484</a>)</li>
<li>Fix <code>--line-ranges</code> crashing with an internal error when an unselected statement has a
<code># fmt: skip</code> comment on the last line before a closing bracket (<a href="">#5477</a>)</li>
<li>Prevent moving an encoding declaration (for example <code># -*- coding: latin-1 -*-</code>) onto
the first two lines of a file (<a href="">#5487</a>)</li>
<li>Fix adding an extra trailing blank line inside a multi-line module docstring when its
last line is near the line length limit (<a href="">#5494</a>)</li>
</ul>
<h3>Preview style</h3>
<ul>
<li>Do not split short expressions on delimiters (such as binary operators, comparisons,
or comprehensions) inside brackets when preceded by a standalone comment (<a href="">#5455</a>)</li>
<li>Fix the unstable <code>string_processing</code> feature removing backslash-newline sequences from
raw strings, which changed their value (<a href="">#5482</a>)</li>
<li>Avoid adding unnecessary parentheses around unbreakable right-hand side expressions in
assignments (such as annotated assignments or subscript targets) (<a href="">#5473</a>)</li>
<li>Parenthesize expressions with parameter comments when they exceed the line length
under <code>--preview</code> (<a href="">#5442</a>)</li>
<li>Fix <code>wrap_long_dict_values_in_parens</code> dropping the parentheses around a right-hand
side that contains a dictionary, leaving a line over the length limit (<a href="">#5492</a>)</li>
<li>Fix the unstable <code>string_processing</code> feature adding a space after <code>*</code> or <code>**</code> in a PEP
695 type parameter (<code>* Ts = ...</code>) when it splits a string in the parameter's default
(<a href="">#5504</a>)</li>
<li>Avoid unnecessary line splits of trailers (such as indexing/subscripts) when an
earlier bracket split exceeds the line length only due to a trailing comment (<a href="">#5498</a>)</li>
</ul>
<h3>Configuration</h3>
<ul>
<li>Add <code>--cache-dir</code> to configure the cache directory from the command line (<a href="">#5433</a>)</li>
<li>Don't cache a file as formatted after formatting or checking it with <code>--line-ranges</code>,</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/psf/black/blob/main/CHANGES.md">black's changelog</a>.</em></p>
<blockquote>
<h2>Version 26.10.1</h2>
<h3>Highlights</h3>
<p>This release fixes a security issue in Black's bundled GitHub Action. Repositories that
use the action are encouraged to update to the latest version of Black immediately. This
update is received automatically when using <code>psf/black@stable</code>, and is independent of
the version of Black installed by the action.</p>
<p>When the GitHub Action reads version specifiers from <code>tool.black.required-version</code>, it
now only accepts released versions of Black, as it already did for <code>black</code> requirements
in dependency lists. Other values, such as URL references, are now rejected. This issue
has been registered as <code>GHSA-cg8m-r9f2-5wm2</code>; a CVE identifier is pending.</p>
<h3>Stable style</h3>
<ul>
<li>Fix a long Jupyter notebook assignment magic (for example <code>x = !ls -la</code>) being wrapped
in parentheses, which IPython can no longer run; such cells are now left unchanged
(<a href="">#5481</a>)</li>
<li>Keep repeated lines outside the selected <code>--line-ranges</code> unchanged (<a href="">#5436</a>)</li>
<li>Fix <code>--line-ranges</code> formatting lines that follow a statement when formatting joins or
re-indents that statement (<a href="">#5484</a>)</li>
<li>Fix <code>--line-ranges</code> crashing with an internal error when an unselected statement has a
<code># fmt: skip</code> comment on the last line before a closing bracket (<a href="">#5477</a>)</li>
<li>Prevent moving an encoding declaration (for example <code># -*- coding: latin-1 -*-</code>) onto
the first two lines of a file (<a href="">#5487</a>)</li>
<li>Fix adding an extra trailing blank line inside a multi-line module docstring when its
last line is near the line length limit (<a href="">#5494</a>)</li>
<li>Keep the parentheses around a walrus that is the only item in a set (for example
<code>{(x := f())}</code>) when targeting Python 3.9 or older, since Python 3.8 and 3.9.0 can't
parse it without them (<a href="">#5502</a>)</li>
</ul>
<h3>Preview style</h3>
<ul>
<li>Do not split short expressions on delimiters (such as binary operators, comparisons,
or comprehensions) inside brackets when preceded by a standalone comment (<a href="">#5455</a>)</li>
<li>Fix the unstable <code>string_processing</code> feature removing backslash-newline sequences from
raw strings, which changed their value (<a href="">#5482</a>)</li>
<li>Avoid adding unnecessary parentheses around unbreakable right-hand side expressions in
assignments (such as annotated assignments or subscript targets) (<a href="">#5473</a>)</li>
<li>Parenthesize expressions with parameter comments when they exceed the line length
under <code>--preview</code> (<a href="">#5442</a>)</li>
<li>Fix <code>wrap_long_dict_values_in_parens</code> dropping the parentheses around a right-hand
side that contains a dictionary, leaving a line over the length limit (<a href="">#5492</a>)</li>
<li>Fix the unstable <code>string_processing</code> feature adding a space after <code>*</code> or <code>**</code> in a PEP
695 type parameter (<code>* Ts = ...</code>) when it splits a string in the parameter's default
(<a href="">#5504</a>)</li>
<li>Avoid unnecessary line splits of trailers (such as indexing/subscripts) when an
earlier bracket split exceeds the line length only due to a trailing comment (<a href="">#5498</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>258e7db</code></a> Prepare release 26.10.1 (<a href="">#5511</a>)</li>
<li><a href=""><code>ac1f715</code></a> Action: validate required-version better (<a href="">#5510</a>)</li>
<li><a href=""><code>fe241cc</code></a> Avoid splitting trailers when earlier bracket split exceeds length due to com...</li>
<li><a href=""><code>4fb2897</code></a> Bump actions/upload-artifact from 7.0.1 to 7.0.2 (<a href="">#5500</a>)</li>
<li><a href=""><code>6d0f557</code></a> Bump actions/download-artifact from 8.0.1 to 8.0.2 (<a href="">#5501</a>)</li>
<li><a href=""><code>c45f21d</code></a> Handle PEP 695 type parameter whitespace in whitespace() (<a href="">#5504</a>)</li>
<li><a href=""><code>8ec61a7</code></a> Skip UTF-8 BOM when reading .gitignore (<a href="">#5497</a>)</li>
<li><a href=""><code>c9b1148</code></a> Fix module docstring last_line_length when docstring ends with newline (<a href="">#5494</a>)</li>
<li><a href=""><code>eb88358</code></a> Parenthesize expressions with parameter comments in preview (<a href="">#3113</a>) (<a href="">#5442</a>)</li>
<li><a href=""><code>939fa93</code></a> Keep the parentheses around a right-hand side when a dict value's parentheses...</li>
<li>Additional commits viewable in <a href="https://github.com/psf/black/compare/26.3.1...26.10.1">compare view</a></li>
</ul>
</details>
<br />

Updates `certifi` from 2025.1.31 to 2026.10.18
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5cb238c</code></a> Remove emsign (<a href="">#437</a>)</li>
<li><a href=""><code>69494a7</code></a> Bump actions/download-artifact from 8.0.1 to 8.0.2 (<a href="">#436</a>)</li>
<li><a href=""><code>029c7b0</code></a> Bump actions/upload-artifact from 7.0.1 to 7.0.2 (<a href="">#435</a>)</li>
<li><a href=""><code>9d0a8f1</code></a> Add support for Python 3.15 (<a href="">#432</a>)</li>
<li><a href=""><code>db472ab</code></a> Bump pypa/gh-action-pypi-publish from 1.14.1 to 1.14.2 (<a href="">#431</a>)</li>
<li><a href=""><code>f4bc676</code></a> 2026.07.22 (<a href="">#428</a>)</li>
<li><a href=""><code>4c91f9c</code></a> Bump actions/setup-python from 6.3.0 to 7.0.0 (<a href="">#427</a>)</li>
<li><a href=""><code>01a66c5</code></a> Bump actions/checkout from 7.0.0 to 7.0.1 (<a href="">#426</a>)</li>
<li><a href=""><code>eb355f4</code></a> Bump pypa/gh-action-pypi-publish from 1.14.0 to 1.14.1 (<a href="">#425</a>)</li>
<li><a href=""><code>474e6fc</code></a> Include tests in the source distribution (<a href="">#424</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/certifi/python-certifi/compare/2025.01.31...2026.10.18">compare view</a></li>
</ul>
</details>
<br />

Updates `dnspython` from 2.7.0 to 2.9.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/rthalley/dnspython/releases">dnspython's releases</a>.</em></p>
<blockquote>
<h2>dnspython 2.9.0</h2>
<p>This release fixes a potential <a href="https://github.com/rthalley/dnspython/security/advisories/GHSA-45c3-73f7-pv4m">excessive CPU consumption</a> issue.   Thanks to Evgenios Gkritsis, Constantinos Patsakis, and George Stergiopoulos, for discovering and reporting this issue.</p>
<p>See <a href="https://dnspython.readthedocs.io/en/stable/whatsnew.html">What's New</a> for details.</p>
<p>The minimum supported version of Python is 3.11.</p>
<p>My thanks to the many people who have contributed to this release. Also thanks to my co-maintainers: Nicki Křížek, Petr Špaček, and Brian Wellington.</p>
<p>This release was published to PyPI using Trusted Publishing.</p>
<h2>dnspython 2.8.0</h2>
<p>See <a href="https://dnspython.readthedocs.io/en/stable/whatsnew.html">What's New</a> for details.</p>
<p>The minimum supported version of Python is 3.10.</p>
<p>My thanks to the many people who have contributed to this release. Also thanks to my co-maintainers: Tomáš Křížek, Petr Špaček, and Brian Wellington.</p>
<p>This release was published to PyPI using Trusted Publishing.</p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rthalley/dnspython/blob/main/doc/whatsnew.rst">dnspython's changelog</a>.</em></p>
<blockquote>
<h2>2.9.0</h2>
<ul>
<li>
<p>Decompression chain length is limited to 16.  Prior to this change,
a maliciously crafted DNS message could cause
dns.name.from_wire_parser() to use excessive CPU for DNS name
decompression. Applications which processed untrusted DNS wire form
messages with dnspython could be degraded or DoS'd by the extra CPU
use required.</p>
<p>Thanks to Evgenios Gkritsis, Constantinos Patsakis, and George Stergiopoulos
for finding and reporting this issue.</p>
<p>See <a href="https://github.com/rthalley/dnspython/security/advisories/GHSA-45c3-73f7-pv4m">https://github.com/rthalley/dnspython/security/advisories/GHSA-45c3-73f7-pv4m</a></p>
</li>
<li>
<p>Httpx2 has replaced httpx for HTTPS TCP connections.</p>
</li>
<li>
<p>The minimum supported Python version is now 3.11.</p>
</li>
<li>
<p>DNSSEC now supports ML-DSA-44, a post-quantum signature algorithm.</p>
</li>
<li>
<p>The NSEC3 Next Hashed Owner Name in presentation format is now decoded as
base32hex (RFC 5155 Section 1.3, RFC 4648 Extended Hex Alphabet).  The letters
W, X, Y, and Z are not in that alphabet; they used to be accepted and silently
decoded to a different owner name, so <code>to_text</code> of the result did not match
the input.  They are now rejected.</p>
</li>
<li>
<p>The NID and L64 node/locator ids in presentation format are now rejected when
a group contains anything other than hex digits. A sign or underscore, which
<code>int()</code> silently accepts, produced a record whose text form did not parse
back the same way (RFC 6742).</p>
</li>
<li>
<p>Rdata of a known type in the generic <code>\#</code> syntax, such as an NS record in a
zone file, no longer fails to parse when it contains a name under the origin.
Its names are relativized as in the type's own text form.</p>
</li>
<li>
<p>The SVCB and HTTPS <code>ech</code> parameter value must now be an ECHConfigList with a
correct length prefix and at least 4 octets of content (RFC 9848, RFC 9849).
The individual ECHConfig structures are not checked.</p>
</li>
<li>
<p>SVCB and HTTPS SvcParamKeys in presentation format, including those listed in
<code>mandatory</code>, must now be spelled as RFC 9460 requires: 1-63 lowercase
letters, digits, or hyphens.  Uppercase keys such as <code>ALPN</code> and keys with
underscores such as <code>no_default_alpn</code> are rejected.</p>
</li>
<li>
<p>SVCB and HTTPS presentation format parsing now follows the escaping rules of
RFC 9460.  SvcParamKeys may not contain escapes (e.g. <code>\097lpn=h2</code>), and in
comma-separated values (<code>alpn</code>, <code>docpath</code>) only <code>\,</code> and <code>\\</code> are
valid escapes after character-string decoding (e.g. <code>alpn=&quot;h2\\x&quot;</code> is
rejected).</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e790c8f</code></a> add missing test file</li>
<li><a href=""><code>b72af67</code></a> CI release branch update</li>
<li><a href=""><code>bdd62fe</code></a> release prep</li>
<li><a href=""><code>bafc963</code></a> Merge branch 'decompression-limit'</li>
<li><a href=""><code>c5fecf5</code></a> release tidying</li>
<li><a href=""><code>c7686f3</code></a> update dependencies</li>
<li><a href=""><code>3c855c8</code></a> more type lint</li>
<li><a href=""><code>52815c9</code></a> type lint</li>
<li><a href=""><code>f563427</code></a> lint</li>
<li><a href=""><code>b485e46</code></a> Limit decompression to a chain length of at most 16 pointers.</li>
<li>Additional commits viewable in <a href="https://github.com/rthalley/dnspython/compare/v2.7.0...v2.9.0">compare view</a></li>
</ul>
</details>
<br />

Updates `filelock` from 3.18.0 to 4.2.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/tox-dev/filelock/releases">filelock's releases</a>.</em></p>
<blockquote>
<h2>4.2.1</h2>
<p><!-- raw HTML omitted --><!-- raw HTML omitted --></p>
<h3>Bug fixes</h3>
<ul>
<li>On a singleton wrapper, <code>AsyncReadWriteLock.close()</code> and <code>AsyncSoftReadWriteLock.close()</code> end only the holds that tasks acquired through that wrapper. A reader that arrives during <code>close()</code> gets the closed error instead of joining the ending hold. After synchronous code closes or force-releases the shared lock, the wrappers refuse to admit readers into the ended hold, and <code>close()</code> on such a wrapper returns. Closing one wrapper no longer ends a task's nested hold taken through another wrapper on the same path. <a href="">#832</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li><code>ReadWriteLock</code> locks again after a <code>release()</code> that an exception from a signal handler interrupted. The async read-write wrappers stop admitting readers into such a level. The async read-write locks forget a hold whose backend release failed after the backend let go, and they free the memory of each acquire that times out or is canceled. <code>AsyncFileLock</code> returns from <code>release()</code> after a few hundred acquires gave up behind a waiting one. An exception from a signal handler delivered while an <code>AsyncFileLock</code> call joins its queue no longer blocks every later call on that lock. <a href="">#833</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li>Fix <code>ReadWriteLock</code> acting on <code>-journal</code>, <code>-wal</code> or <code>-shm</code> files another process puts beside its database: a write could land in another file, a reader could get in beside a writer, and an acquire could fail. SQLite now opens the database by name only in a directory no other account can write, and through a private hard link elsewhere. On Windows the directory's access control list decides. Where hard links are unavailable, keep the database in a directory other accounts cannot write, such as one under <code>%LOCALAPPDATA%</code>. The lock removes link directories through a checked descriptor rather than by name, reads a link directory's name only when the locking account owns it, and leaves alone a directory with other content renamed onto a link directory's name. A database whose schema takes more than a few kilobytes to load raises <code>ValueError</code> instead of running past the acquire timeout. <a href="">#834</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li>Fix five bugs in opening the lock file. <code>UnixFileLock</code> no longer truncates a file it did not create, such as one renamed to the lock path, and no longer applies <code>mode</code> to it. An <code>on_acquired</code> hook that writes holder metadata now truncates the file itself. A lease (Linux) or an oplock (Windows) on the lock file or a soft lock's marker no longer holds <code>acquire()</code> past its <code>timeout</code> or <code>blocking=False</code>, and an oplock no longer holds <code>release()</code>; <code>ReadWriteLock</code> on Windows waits for its <code>timeout</code> and raises <code>Timeout</code>. On Windows, a <code>mode</code> without group and other bits, such as <code>0o600</code>, now creates the lock file with an owner-only permission list; the <code>ReadWriteLock</code> database gets the same. The soft locks' writability check no longer follows a symlink swapped in at the lock path. On a filesystem without <code>flock</code>, a contender from another account now waits on a marker it cannot write instead of raising <code>PermissionError</code>. <a href="">#835</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li>Fix <code>SoftFileLock</code>, <code>MarkerSoftFileLock</code> and <code>SoftFileLease</code> removing a live holder's marker in three cases: the holder and the contender run in Linux time namespaces with different boottime offsets; only one of them can read the boot id; a process other than the owner rewrote the marker. Soft markers no longer carry group or other write bits. A process name containing a carriage return or another line separator no longer makes the stale check raise <code>ValueError</code>. When <code>/proc/self/ns/time</code> exists but cannot be read, the stale check no longer compares start times and keeps the marker. <a href="">#836</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li>The async read-write locks record their hold under a task owner, so synchronous code on the executor thread that took the hold can no longer re-enter or release it. <code>AsyncSoftReadWriteLock</code> gives back one level on release, so synchronous readers of a shared singleton keep theirs. <code>SoftReadWriteLock</code> tracks read levels per thread: <code>release()</code> from a thread that holds none raises <code>RuntimeError</code>. After its heartbeat recorded a lost hold, it refuses new acquires until that hold is released. <a href="">#838</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li><code>StrictSoftFileLock</code> creates <code>&lt;path&gt;.filelock</code> and its <code>claims</code> directory with the lock's <code>mode</code> and sets the sticky bit (a directory flag that lets only a file's owner remove it) on both. On the next acquisition it narrows a directory it owns that an earlier release created wider; it leaves a directory of another account as it is, so remove such leftovers by hand. It reaches <code>claims</code> through a descriptor opened without following symlinks; on Windows it holds both directories open and refuses a junction (a directory that points at another directory). Under a sticky parent such as <code>/tmp</code> it refuses a coordination directory of another account, as <code>SoftReadWriteLock</code> does for <code>&lt;path&gt;.rw</code>. One read grace now covers a whole claim scan, a failed claim cleanup no longer leaves the sentinel descriptor open, and a non-regular node at a sentinel private-record name raises <code>SoftFileLockProtocolError</code>. On Windows, contenders read claims without blocking their owner's unlink. <a href="">#839</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li>Fix a lock reporting a hold the OS had dropped after a signal handler raised during <code>acquire</code> or <code>release</code>. A release that a signal handler cuts short after it has started now completes before the error propagates. A handler that acquires the lock its own thread is releasing now gets <code>RuntimeError</code> instead of a hold that stays held. The singleton cache no longer hands out an <code>is_singleton=True</code> lock or a <code>ReadWriteLock</code> whose finalizer is running, which released the new holder's lock. A signal during <code>os.fork()</code> no longer leaves the other threads blocked in their next lock call, and a fork from another thread no longer waits for a <code>ReadWriteLock</code> acquire on a busy database. <a href="">#840</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li>Fix a lock on a relative path locking a file in the directory the process changed to while the lock waited, and leaving its marker behind on release after such a change. The path resolved when an acquisition starts stays in use until the hold ends. An <code>is_singleton=True</code> lookup no longer returns a cached lock whose relative path now resolves to another file; a held lock still matches the file it holds. A rename of the lock's directory during a hold no longer leaves the marker behind or reports a false lease compromise, and a waiter no longer creates a second lock file in a directory that was renamed away. <a href="">#841</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li><code>SoftReadWriteLock</code> reaches its records through descriptors of <code>&lt;path&gt;.rw</code> and <code>gen</code> or <code>holders</code> opened without following symlinks. On Windows it holds those directories open and refuses a junction (a directory that points at another directory). A tree swapped in after an earlier acquire therefore cannot redirect them. Its heartbeat rewrites a holder record only when the name still leads to the file it created, and does not block on a FIFO (a named pipe). A heartbeat that finds <code>&lt;path&gt;.rw</code> replaced by a symlink or junction reports the hold lost instead of ending the heartbeat thread. A live lock object repeats the ownership check whenever the tree it opens is not the one it prepared. <a href="">#842</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li>Fix <code>SoftFileLock</code>, <code>MarkerSoftFileLock</code> and <code>SoftFileLease</code> removing or displacing a live holder's marker in five cases. ext4 gave a freed inode number to the next marker. A stalled <code>FileLock</code> removed its <code>ENOSYS</code> placeholder after a peer replaced it. A failed acquire cleaned up after a successor took the path. A stale break left the lock path empty while it checked the marker it had moved. A <code>lifetime</code> break judged a marker by a reused inode number. On Linux and macOS a stale marker now changes hands in one atomic exchange. On other platforms without one, except Windows, including NFS and SMB, the marker stays in place and waits for <code>timeout</code> or <code>break_lock()</code>. Restoring a marker no longer follows a symlink found under the break name. A holder that releases while a peer's exchange has its marker aside leaves a record no lock parses, so the put-back lands a marker that ages out. A lease heartbeat that finds another file at the lock path once, while a peer's break has its marker aside, waits for the next refresh before it reports a compromise. A contender that finds a dead breaker's marker puts back the marker that breaker left under its break name. A marker is the breaker's own only when it names the breaker's process on this host; the same process number on another host is a holder. A contender takes a stranded marker under a name of its own before it puts the marker back, so two contenders no longer reverse each other's exchange and remove the live holder's marker. A claim left behind by a failed put-back is retried on the next poll. <a href="">#843</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li>Canceling an <code>AsyncReadWriteLock</code> or <code>AsyncSoftReadWriteLock</code> acquire that waits for another process now stops the wait and raises the cancellation. It used to wait until that process released, or raise <code>Timeout</code>. A <code>thread_local=True</code> <code>AsyncFileLock</code> that threads with their own event loops share no longer deadlocks when one thread waits for the lock while another holds it. <a href="">#844</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li><code>SoftReadWriteLock</code> refuses a commit that lands a whole retention window behind the log, so two committers stalled at adjacent generations can no longer admit a second writer. Its stale check samples the clock before it reads a holder record, so a pause between the two no longer counts as time the record stayed unchanged. <a href="">#845</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li>Fix a <code>SoftFileLock</code> contender evicting an empty marker after two seconds while its owner held the lock. The owner is a <code>SoftFileLock</code> before 3.22, which writes nothing into its marker, or a current one still writing its record. An empty marker now reads as held, and <code>timeout</code>, <code>lifetime</code> or <code>break_lock()</code> clears it. A contender that finds an empty marker a dead breaker left aside puts it back instead of removing it. <a href="">#846</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li>Fix <code>ReadWriteLock</code> on Windows acting on <code>-journal</code> and <code>-wal</code> files another account places beside its database: an acquire could fail with <code>OperationalError</code>, or SQLite could replay the journal and delete the file it names. The lock now reads the database directory's access control list. Where an account other than the locking account, <code>SYSTEM</code> and <code>Administrators</code> can add or remove names, SQLite opens a hard link inside a directory only those accounts can write. A filesystem without hard links raises <code>OSError</code>. <a href="">#854</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
<li>Fix <code>SoftReadWriteLock</code> subclasses sharing singleton instances with the base class or sibling subclasses. Each concrete class now keeps its own cache and construction guard, including after fork, while preserving cooperative class-definition keywords. <a href="">#855</a> by <a href="https://github.com/AryanRG"><code>@​AryanRG</code></a>.</li>
</ul>
<h3>New Contributors</h3>
<ul>
<li><a href="https://github.com/AryanRG"><code>@​AryanRG</code></a> made their first contribution in <a href="">#855</a></li>
</ul>
<p><a href="https://pypi.org/project/filelock/4.2.1/">🐍 PyPI release</a></p>
<p><a href="https://github.com/tox-dev/filelock/compare/4.2.0...4.2.1">📜 Full Changelog</a></p>
<h2>4.2.0</h2>
<p><!-- raw HTML omitted --><!-- raw HTML omitted --></p>
<h3>Bug fixes</h3>
<ul>
<li>Fix <code>StrictSoftFileLock</code> raising <code>SoftFileLockProtocolError</code> on Windows when a contender read a claim whose owner was still finishing its unlink. <a href="">#829</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
</ul>
<p><!-- raw HTML omitted --><!-- raw HTML omitted --></p>
<h3>Performance</h3>
<ul>
<li><code>import filelock</code> is about twice as fast: lock types other than <code>FileLock</code> load on first use. <a href="">#831</a> by <a href="https://github.com/gaborbernat"><code>@​gaborbernat</code></a>.</li>
</ul>
<p><a href="https://pypi.org/project/filelock/4.2.0/">🐍 PyPI release</a></p>
<p><a href="https://github.com/tox-dev/filelock/compare/4.1.2...4.2.0">📜 Full Changelog</a></p>
<h2>4.1.2</h2>
<p><!-- raw HTML omitted --><!-- raw HTML omitted --></p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/tox-dev/filelock/blob/main/docs/changelog.rst">filelock's changelog</a>.</em></p>
<blockquote>
<p>###########
Changelog
###########</p>
<p>.. towncrier-draft-entries:: Unreleased</p>
<p>.. towncrier release notes start</p>
<p>.. _release-4-2-5:</p>
<hr />
<p>4.2.5 (2026-10-30)</p>
<hr />
<p>.. _release-4-2-5-fixed:</p>
<h1>Fixed</h1>
<ul>
<li>:meth:<code>~filelock.BaseFileLock.acquire</code> and :meth:<code>~filelock.BaseAsyncFileLock.acquire</code> raise :class:<code>TypeError</code> for a
<em>blocking</em> that is not a :class:<code>bool</code>, as the constructor and the <code>blocking</code> setter already do. A truthy value such
as the string <code>&quot;false&quot;</code> used to count as <code>True</code>, so a call meant as a single attempt waited for the instance's
<code>timeout</code>, and without a limit at the default <code>-1</code> (:pr:<code>870</code>) by :user:<code>simpleqt</code> and :user:<code>gaborbernat</code>.</li>
<li>A :class:<code>~filelock.SoftFileLock</code> acquisition whose first read of its new marker's identity failed reads it again
before rolling back. On Windows the rollback could otherwise not recognize the marker it had created, and the empty
marker it left blocked the path for every later acquisition, since no contender breaks an empty marker (:pr:<code>869</code>) by
:user:<code>simpleqt</code> and :user:<code>gaborbernat</code>.</li>
<li>A <code>fork()</code> child of a process holding a :class:<code>~filelock.SoftFileLease</code> starts from an unheld claim. It used to
inherit the parent's token, last compromise and heartbeat, so :attr:<code>~filelock.SoftFileLease.token</code> and
:attr:<code>~filelock.SoftFileLease.compromise</code> reported a claim the child never held while <code>is_locked</code> reported it
unheld (:pr:<code>868</code>) by :user:<code>dxbjavid</code> and :user:<code>gaborbernat</code>.</li>
<li>A nested acquire of a held :class:<code>~filelock.FileLock</code> or :class:<code>~filelock.SoftFileLock</code> no longer creates the lock
file's parent directory. After a rename of that directory during the hold, the nested acquire recreated the old name,
and when a file had taken the name it raised :class:<code>FileExistsError</code> and left the hold's recursion count incremented
(:pr:<code>878</code>) by :user:<code>0x5t4l1n</code> and :user:<code>gaborbernat</code>.</li>
<li>Fix :class:<code>ReadWriteLock &lt;filelock.ReadWriteLock&gt;</code> failing every acquire with &quot;link directory ... was replaced while
opening&quot; in a group-writable directory whose inherited ACL, such as an NFSv4 one on ZFS, opens the link directory to
the group. The lock now closes the empty link directory to its owner, and where the filesystem refuses that, such as
ZFS with <code>aclmode=restricted</code>, it names the directory to make writable by its owner only (:pr:<code>898</code>) by
:user:<code>gaborbernat</code>.</li>
<li>Fix :class:<code>~filelock.SoftFileLock</code>, :class:<code>~filelock.MarkerSoftFileLock</code> and :class:<code>~filelock.SoftFileLease</code>
raising <code>OverflowError</code> out of <code>acquire()</code>, or never reclaiming a dead holder's lock, when a stranded restore
claim beside the lock names a process number outside <code>1..2**31-1</code> or spells it in non-ASCII digits. Such a claim is
now ignored, as no filelock writes one (:pr:<code>871</code>) by :user:<code>dxbjavid</code> and :user:<code>gaborbernat</code>.</li>
<li>Fix soft locks on Windows keeping the marker of a holder that has exited while another process still holds a handle to
it, such as a parent's <code>subprocess.Popen</code> after <code>wait()</code> or <code>multiprocessing.Process</code> after <code>join()</code>.
Acquiring such a lock with the default <code>timeout=-1</code> waited forever (:pr:<code>874</code>) by :user:<code>nk-batman21</code>.</li>
<li>Fix the read-only reopen of a lock file this account cannot write resolving a relative path against the working
directory of the moment. A <code>chdir</code> between the refused <code>O_RDWR</code> open and the reopen made the acquisition wait on a
file that is not there, or probe one in another directory. The reopen now uses the path the acquisition pinned</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>60331bb</code></a> Release 4.2.1</li>
<li><a href=""><code>834bf13</code></a> 🧪 test(soft): skip Unix pin test on Windows</li>
<li><a href=""><code>9d15e38</code></a> fix(soft-rw): isolate subclass singleton registries (<a href="">#855</a>)</li>
<li><a href=""><code>e1e825b</code></a> 🐛 fix(open): keep lock files intact, honor deadlines and mode (<a href="">#835</a>)</li>
<li><a href=""><code>5e3f2ec</code></a> 🐛 fix(read-write): keep SQLite off shared names, bound schema (<a href="">#834</a>)</li>
<li><a href=""><code>bfa066d</code></a> 🐛 fix(strict): keep claim directories private to the lock (<a href="">#839</a>)</li>
<li><a href=""><code>977d2c3</code></a> 🐛 fix(soft): wait on an empty marker instead of evicting (<a href="">#846</a>)</li>
<li><a href=""><code>740ff66</code></a> 🐛 fix(soft): break stale markers without emptying the lock path (<a href="">#843</a>)</li>
<li><a href=""><code>86c6d5f</code></a> 🐛 fix(async): honor cancellation and per-thread gates (<a href="">#844</a>)</li>
<li><a href=""><code>eeceaa8</code></a> 🐛 fix(soft): keep live holders when owner identity differs (<a href="">#836</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/tox-dev/filelock/compare/3.18.0...4.2.1">compare view</a></li>
</ul>
</details>
<br />

Updates `gitpython` from 3.1.61 to 3.2.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/gitpython-developers/GitPython/releases">gitpython's releases</a>.</em></p>
<blockquote>
<h2>3.2.1</h2>
<h2>What's Changed</h2>
<ul>
<li>prepare for next release, v3.2 by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2260</a></li>
<li>objects: decode a byte mode before reading its digits by <a href="https://github.com/SashaMIT"><code>@​SashaMIT</code></a> in <a href="">gitpython-developers/GitPython#2261</a></li>
<li>build(deps): bump <a href="https://github.com/astral-sh/ruff-pre-commit">https://github.com/astral-sh/ruff-pre-commit</a> from v0.16.5 to 0.16.9 in the pre-commit group by <a href="https://github.com/dependabot"><code>@​dependabot</code></a>[bot] in <a href="">gitpython-developers/GitPython#2263</a></li>
<li>fix(submodule): validate destinations before mutation by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2264</a></li>
<li>fix(util): create lock files in one exclusive step by <a href="https://github.com/radhika1314"><code>@​radhika1314</code></a> in <a href="">gitpython-developers/GitPython#2267</a></li>
<li>fix(commit): accumulate gpgsig continuation lines in linear time by <a href="https://github.com/Keerthana-64"><code>@​Keerthana-64</code></a> in <a href="">gitpython-developers/GitPython#2268</a></li>
<li>fix(index): accept a single PathLike in checkout by <a href="https://github.com/kokotatan"><code>@​kokotatan</code></a> in <a href="">gitpython-developers/GitPython#2269</a></li>
<li>fix(util): redact URL credentials without corrupting the host by <a href="https://github.com/yunaremaia"><code>@​yunaremaia</code></a> in <a href="">gitpython-developers/GitPython#2270</a></li>
<li>change line for changelogs by <a href="https://github.com/CrowZhen"><code>@​CrowZhen</code></a> in <a href="">gitpython-developers/GitPython#2272</a></li>
<li>fix(commit): reject identity fields that alter commit headers by <a href="https://github.com/Keerthana-64"><code>@​Keerthana-64</code></a> in <a href="">gitpython-developers/GitPython#2271</a></li>
<li>fix: stop stalled remote commands when their timeout expires by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2277</a></li>
<li>fix(util): reject symbolic links that alias <code>.gitmodules</code> by <a href="https://github.com/Keerthana-64"><code>@​Keerthana-64</code></a> in <a href="">gitpython-developers/GitPython#2278</a></li>
<li>fix: send one object name or path per git stdin record by <a href="https://github.com/Keerthana-64"><code>@​Keerthana-64</code></a> in <a href="">gitpython-developers/GitPython#2279</a></li>
<li>fix(stats): preserve whitespace in filenames by <a href="https://github.com/v1shay"><code>@​v1shay</code></a> in <a href="">gitpython-developers/GitPython#2280</a></li>
<li>fix(config): preserve exact large integer values by <a href="https://github.com/xiehuanyi"><code>@​xiehuanyi</code></a> in <a href="">gitpython-developers/GitPython#2281</a></li>
<li>fix: resolve IterableList names independently of list attributes by <a href="https://github.com/FanWu-ai"><code>@​FanWu-ai</code></a> in <a href="">gitpython-developers/GitPython#2283</a></li>
<li>fix relative blocking lock 20261011 by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2284</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/SashaMIT"><code>@​SashaMIT</code></a> made their first contribution in <a href="">gitpython-developers/GitPython#2261</a></li>
<li><a href="https://github.com/kokotatan"><code>@​kokotatan</code></a> made their first contribution in <a href="">gitpython-developers/GitPython#2269</a></li>
<li><a href="https://github.com/yunaremaia"><code>@​yunaremaia</code></a> made their first contribution in <a href="">gitpython-developers/GitPython#2270</a></li>
<li><a href="https://github.com/CrowZhen"><code>@​CrowZhen</code></a> made their first contribution in <a href="">gitpython-developers/GitPython#2272</a></li>
<li><a href="https://github.com/v1shay"><code>@​v1shay</code></a> made their first contribution in <a href="">gitpython-developers/GitPython#2280</a></li>
<li><a href="https://github.com/xiehuanyi"><code>@​xiehuanyi</code></a> made their first contribution in <a href="">gitpython-developers/GitPython#2281</a></li>
<li><a href="https://github.com/FanWu-ai"><code>@​FanWu-ai</code></a> made their first contribution in <a href="">gitpython-developers/GitPython#2283</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/gitpython-developers/GitPython/compare/3.2.0...3.2.1">https://github.com/gitpython-developers/GitPython/compare/3.2.0...3.2.1</a></p>
<h2>3.2.0 - Security</h2>
<h2>What's Changed</h2>
<ul>
<li>test: cover subdirectory discovery and pathspec commands in bare-repository worktrees by <a href="https://github.com/christianvuerings"><code>@​christianvuerings</code></a> in <a href="">gitpython-developers/GitPython#2228</a></li>
<li>Read git's yes/no and on/off booleans in get_value by <a href="https://github.com/rawsun007"><code>@​rawsun007</code></a> in <a href="">gitpython-developers/GitPython#2229</a></li>
<li>Clarify detached HEAD access and isolate test branch state by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2231</a></li>
<li>Reject submodule move destinations through intermediate symlinks by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2232</a></li>
<li>fix: validate checkout positional reference options by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2233</a></li>
<li>Fix timeout child-process lookup on non-GNU systems by <a href="https://github.com/aprylewu"><code>@​aprylewu</code></a> in <a href="">gitpython-developers/GitPython#2236</a></li>
<li>Preserve implicit boolean config keys by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2238</a></li>
<li>Reject comments after implicit boolean config keys by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2239</a></li>
<li>Fix case-insensitive Git config name matching by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2241</a></li>
<li>Move project metadata to pyproject.toml by <a href="https://github.com/mwtoews"><code>@​mwtoews</code></a> in <a href="">gitpython-developers/GitPython#2242</a></li>
<li>Move [doc] extra to a PEP 735 dependency group; add uv-sync CI check by <a href="https://github.com/mwtoews"><code>@​mwtoews</code></a> in <a href="">gitpython-developers/GitPython#2243</a></li>
<li>fix: strip inline config comments the way git does by <a href="https://github.com/rawsun007"><code>@​rawsun007</code></a> in <a href="">gitpython-developers/GitPython#2245</a></li>
<li>Drop Python 3.7 by <a href="https://github.com/mwtoews"><code>@​mwtoews</code></a> in <a href="">gitpython-developers/GitPython#2246</a></li>
<li>fix: preserve positional operands in high-level Git commands by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2247</a></li>
<li>submodule: option to update without fetching by <a href="https://github.com/jeffro256"><code>@​jeffro256</code></a> in <a href="">gitpython-developers/GitPython#2244</a></li>
<li>bump minor version to indicate drop of python 3.7 support by <a href="https://github.com/Byron"><code>@​Byron</code></a> in <a href="">gitpython-developers/GitPython#2248</a></li>
<li>fix: skip a UTF-8 BOM when reading config files by <a href="https://github.com/geek-alpha"><code>@​geek-alpha</code></a> in <a href="">gitpython-developers/GitPython#2249</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/gitpython-developers/GitPython/blob/main/doc/source/changes.rst">gitpython's changelog</a>.</em></p>
<blockquote>
<h1>3.2.1</h1>
<p>Security fixes for</p>
<ul>
<li><a href="https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-83vg-56qc-22m7">https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-83vg-56qc-22m7</a></li>
</ul>
<p>If you can, also try and provide feedback on the upcoming v4 branch
<a href="">gitpython-developers/GitPython#2274</a> - patches welcome.</p>
<p>See the following for all changes.
<a href="https://github.com/gitpython-developers/GitPython/releases/tag/3.2.1">https://github.com/gitpython-developers/GitPython/releases/tag/3.2.1</a></p>
<h1>3.2.0</h1>
<p>Drops support for Python 3.7 (5 years after its EOL).</p>
<p>Security fixes for</p>
<ul>
<li>Deprecate the pure-Python <code>GitDB</code> object database backend due to security and
performance issues. Selecting it or a subclass through <code>odbt</code> now emits a
<code>DeprecationWarning</code>. Remove <code>odbt=GitDB</code> to use <code>GitCmdObjectDB</code>, the
existing default, or select <code>odbt=GitCmdObjectDB</code> explicitly. The <code>gitdb</code>
package remains a dependency for shared types and utilities.</li>
<li><a href="https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-gq48-pqfc-9p58">https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-gq48-pqfc-9p58</a></li>
<li><a href="https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-23mf-xhv8-69c2">https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-23mf-xhv8-69c2</a></li>
<li><a href="https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-f9j4-qggq-h239">https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-f9j4-qggq-h239</a></li>
<li><a href="https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-w8jc-g24h-crhw">https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-w8jc-g24h-crhw</a></li>
<li><a href="https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-m64x-33q8-m5h7">https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-m64x-33q8-m5h7</a></li>
<li><a href="https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-fx3j-rwgx-fr94">https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-fx3j-rwgx-fr94</a></li>
</ul>
<p>If you can, also try and provide feedback on the upcoming v4 branch
<a href="">gitpython-developers/GitPython#2274</a> - patches welcome.</p>
<p>See the following for all changes.
<a href="https://github.com/gitpython-developers/GitPython/releases/tag/3.2.0">https://github.com/gitpython-developers/GitPython/releases/tag/3.2.0</a></p>
<h1>3.1.62</h1>
<p>Security fixes for</p>
<ul>
<li><a href="https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-59cr-6r3x-644w">https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-59cr-6r3x-644w</a></li>
</ul>
<p>If you can, also try and provide feedback on the upcoming v4 branch
<a href="">gitpython-developers/GitPython#2274</a> - patches welcome.</p>
<p>See the following for all changes.
<a href="https://github.com/gitpython-developers/GitPython/releases/tag/3.1.62">https://github.com/gitpython-developers/GitPython/releases/tag/3.1.62</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c179357</code></a> prepare changelog prior to release</li>
<li><a href=""><code>97eadb8</code></a> fix(submodule): validate destinations before mutation</li>
<li><a href=""><code>6a7180a</code></a> prepare for next release, v3.2</li>
<li><a href=""><code>0b64501</code></a> refactor(db): deprecate the pure-Python <code>GitDB</code> backend</li>
<li><a href=""><code>9349ff5</code></a> fix(repo): preserve literal separate Git directory paths</li>
<li><a href=""><code>8290c98</code></a> fix: bound actor and date parsing</li>
<li><a href=""><code>9ad28cc</code></a> fix: complete safety checks in Git command wrappers</li>
<li><a href=""><code>ce2093b</code></a> bump minor version to indicate drop of python 3.7 support</li>
<li><a href=""><code>dafafff</code></a> Merge pull request <a href="">#2247</a> from gitpython-developers/pos-arg-sanitization</li>
<li><a href=""><code>790bb31</code></a> fix(remote): reject option-shaped pull operands</li>
<li>Additional commits viewable in <a href="https://github.com/gitpython-developers/GitPython/compare/3.1.61...3.2.1">compare view</a></li>
</ul>
</details>
<br />

Updates `jupyterlab` from 4.5.10 to 4.6.5
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/jupyterlab/jupyterlab/releases">jupyterlab's releases</a>.</em></p>
<blockquote>
<h2>v4.6.5</h2>
<h2>4.6.5</h2>
<p>(<a href="https://github.com/jupyterlab/jupyterlab/compare/v4.6.4...9f5590d07b9a63402a628fe758654f30ee59c2e4">Full Changelog</a>)</p>
<h3>Bugs fixed</h3>
<ul>
<li>Restrict path suggestions to the file dialog root <a href="">#20298</a> (<a href="https://github.com/krassowski"><code>@​krassowski</code></a>)</li>
<li>Fix find in the JSON viewer <a href="">#20023</a> (<a href="https://github.com/jtpio"><code>@​jtpio</code></a>)</li>
<li>Fix editor rulers drawn at the wrong columns when the code font loads late <a href="">#20310</a> (<a href="https://github.com/krassowski"><code>@​krassowski</code></a>)</li>
<li>Fix &quot;New Python File&quot; appearing twice in the file browser context menu <a href="">#20305</a> (<a href="https://github.com/dturaev"><code>@​dturaev</code></a>)</li>
<li>Upgrade <code>@codemirror/view</code> to 6.43.15, fi...

_Description has been truncated_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2139d7af89fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Bump gradle-wrapper from 9.3.1 to 9.4.1

## Description

Bumps [gradle-wrapper](https://github.com/gradle/gradle) from 9.3.1 to 9.4.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/gradle/gradle/releases">gradle-wrapper's releases</a>.</em></p>
<blockquote>
<h2>9.4.1</h2>
<p>The Gradle team is excited to announce Gradle 9.4.1.</p>
<p>Here are the highlights of this release:</p>
<ul>
<li>Java 26 support</li>
<li>Non-class-based JVM tests</li>
<li>Enhanced console progress bar</li>
</ul>
<p><a href="https://docs.gradle.org/9.4.1/release-notes.html">Read the Release Notes</a></p>
<p>We would like to thank the following community members for their contributions to this release of Gradle:
<a href="https://github.com/akankshaa-00">akankshaa-00</a>,
<a href="https://github.com/kelemen">Attila Kelemen</a>,
<a href="https://github.com/Vampire">Björn Kautler</a>,
<a href="https://github.com/dblood">dblood</a>,
<a href="https://github.com/drieks">Dennis Rieks</a>,
<a href="https://github.com/duvvuvenkataramana">duvvuvenkataramana</a>,
<a href="https://github.com/wakingrufus">John Burns</a>,
<a href="https://github.com/Julianw03">Julian</a>,
<a href="https://github.com/kevinstembridge">kevinstembridge</a>,
<a href="https://github.com/NielsDoucet">Niels Doucet</a>,
<a href="https://github.com/hfhbd">Philip Wedemann</a>,
<a href="https://github.com/ploober">ploober</a>,
<a href="https://github.com/rhernandez35">Richard Hernandez</a>,
<a href="https://github.com/rpalcolea">Roberto Perez Alcolea</a>,
<a href="https://github.com/slovdahl">Sebastian Lövdahl</a>,
<a href="https://github.com/stephan2405">stephan2405</a>,
<a href="https://github.com/slandelle">Stephane Landelle</a>,
<a href="https://github.com/usv240">Ujwal Suresh Vanjare</a>,
<a href="https://github.com/urdak">Victor Merkulov</a>,
<a href="https://github.com/Pankraz76">Vincent Potuček</a>,
<a href="https://github.com/vlsi">Vladimir Sitnikov</a>.</p>
<h2>Upgrade instructions</h2>
<p>Switch your build to use Gradle 9.4.1 by updating your wrapper:</p>
<pre><code>./gradlew wrapper --gradle-version=9.4.1 &amp;&amp; ./gradlew wrapper
</code></pre>
<p>See the Gradle <a href="https://docs.gradle.org/9.4.1/userguide/upgrading_version_9.html">9.x upgrade guide</a> to learn about deprecations, breaking changes and other considerations when upgrading.</p>
<p>For Java, Groovy, Kotlin and Android compatibility, see the <a href="https://docs.gradle.org/9.4.1/userguide/compatibility.html">full compatibility notes</a>.</p>
<h2>Reporting problems</h2>
<p>If you find a problem with this release, please file a bug on <a href="https://github.com/gradle/gradle/issues">GitHub Issues</a> adhering to our issue guidelines.
If you're not sure you're encountering a bug, please use the <a href="https://discuss.gradle.org/c/help-discuss">forum</a>.</p>
<p>We hope you will build happiness with Gradle, and we look forward to your feedback via <a href="https://twitter.com/gradle">Twitter</a> or on <a href="https://github.com/gradle">GitHub</a>.</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>2d63270</code></a> Ignore test (<a href="">#37180</a>)</li>
<li><a href=""><code>4c15906</code></a> Ignore test</li>
<li><a href=""><code>9759ac1</code></a> Make console/SIGINT test deterministic (<a href="">#37178</a>)</li>
<li><a href=""><code>aaf6ed4</code></a> Make console/SIGINT test deterministic</li>
<li><a href=""><code>47cb783</code></a> Fix OSC 9;4 progress bar not cleared on SIGINT (<a href="">#37038</a>)</li>
<li><a href=""><code>ef03f1d</code></a> Fix order-dependent assertion in CrossBuildScriptCachingIntegrationSpec</li>
<li><a href=""><code>fd26fd3</code></a> Fix OSC 9;4 taskbar progress bar not cleared on build end or SIGINT</li>
<li><a href=""><code>0a84d67</code></a> Release notes for 9.4.1 (<a href="">#37148</a>)</li>
<li><a href=""><code>e569c31</code></a> cleanup</li>
<li><a href=""><code>9f227de</code></a> cleanup</li>
<li>Additional commits viewable in <a href="https://github.com/gradle/gradle/compare/v9.3.1...v9.4.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=gradle-wrapper&package-manager=gradle&previous-version=9.3.1&new-version=9.4.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84400daff0d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
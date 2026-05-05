---
title: "Announcing PowerShell 7.6 (LTS) GA Release"
url: "https://devblogs.microsoft.com/powershell/announcing-powershell-7-6/"
date: "Wed, 18 Mar 2026 21:47:31 +0000"
author: "Jason Helmick"
feed_url: "https://devblogs.microsoft.com/powershell/feed/"
---
<p><!-- markdownlint-disable MD041 --></p>
<p>We&#8217;re excited to announce the General Availability of PowerShell 7.6, the next Long Term Support
(LTS) release of PowerShell. PowerShell 7.6 is built on .NET 10 (LTS), continuing the alignment
between PowerShell and the modern .NET platform.</p>
<p>PowerShell 7.6 includes reliability improvements across the engine, modules, and interactive shell
experience. Preview releases focused on improving consistency, fixing long-standing issues, and
refining behavior across platforms.</p>
<p>Notable areas of improvement include:</p>
<ul>
<li>Module updates</li>
<li>Engine reliability fixes</li>
<li>Native command handling improvements</li>
<li>Tab completion consistency improvements</li>
<li>Dependency updates aligned with .NET 10</li>
</ul>
<p>As an LTS release, PowerShell 7.6 becomes the recommended version for production automation
environments.</p>
<h2>Highlights</h2>
<ul>
<li>PowerShell 7.6 includes updates to several core modules:
<ul>
<li>PSReadLine</li>
<li>Microsoft.PowerShell.PSResourceGet</li>
<li>Microsoft.PowerShell.ThreadJob</li>
</ul>
</li>
<li>Dozens of tab completion improvements
<ul>
<li>Improved path completion across providers</li>
<li>Added value completion for parameters of several cmdlets</li>
<li>Enabled completes in more contexts and scopes</li>
<li>Added completion of modules by their shortname</li>
</ul>
</li>
<li>Added features to existing commands
<ul>
<li>Added <code>-Delimiter</code> parameter to <code>Get-Clipboard</code></li>
<li>Added the parameter <code>Register-ArgumentCompleter -NativeFallback</code> to support registering a
cover-all completer for native commands</li>
<li>Treat <code>-Target</code> as literal in <code>New-Item</code></li>
<li>Added <code>-ExcludeModule</code> parameter to <code>Get-Command</code></li>
<li>Improved <code>Start-Process -Wait</code> polling efficiency</li>
</ul>
</li>
<li>Several engine improvements
<ul>
<li>Added <code>PSForEach()</code> and <code>PSWhere()</code> as aliases for the PowerShell intrinsic methods <code>Where()</code>
and <code>Foreach()</code></li>
<li>Make <code>SystemPolicy</code> public APIs visible but no-op on Unix platforms so that they can be included
in <code>PowerShellStandard.Library</code></li>
<li>Update <code>DnsNameList</code> for <code>X509Certificate2</code> to use
<code>X509SubjectAlternativeNameExtension.EnumerateDnsNames()</code> method</li>
<li>Fixed stderr output of console host to respect the <code>NO_COLOR</code> environment variable</li>
</ul>
</li>
<li>The following features have been converted to mainstream features:
<ul>
<li><code>PSFeedbackProvider</code></li>
<li><code>PSNativeWindowsTildeExpansion</code></li>
<li><code>PSRedirectToVariable</code></li>
<li><code>PSSubsystemPluginModel</code></li>
</ul>
</li>
</ul>
<h2>Breaking changes</h2>
<p>PowerShell 7.6 includes a small number of breaking changes intended to improve long-term
consistency.</p>
<ul>
<li>Converted <code>-ChildPath</code> parameter to <code>string[]</code> for <code>Join-Path</code> cmdlet. Allows user to give an
array of child paths and avoid the extra usage with <code>-AdditionalChildPath</code>.</li>
<li><code>WildcardPattern.Escape()</code> now correctly escapes lone backticks.</li>
<li>Removed the trailing space from the <code>GetHelpCommand</code> trace source name.</li>
</ul>
<h2>Community contributions</h2>
<p>PowerShell is built by a global community of users and contributors. The following individuals
contributed code to the PowerShell 7.6 release:</p>
<ul>
<li>@AbishekPonmudi, @ArmaanMcleod, @bdeb1337, @cmkb3, @eltociear</li>
<li>@fflaten, @fMichaleczek, @GameMicrowave, @iSazonov, @JayBazuzi</li>
<li>@jborean93, @JustinGrote, @kasperk81, @kborowinski, @kilasuit</li>
<li>@KyZy7, @MartinGC94, @MatejKafka, @mawosoft, @powercode</li>
<li>@pressRtowin, @RichardSlater, @rzippo, @sba923, @senerh</li>
<li>@Tadas, @TheSpyGod, @ThomasNieto, @VbhvGupta, @xtqqczze</li>
</ul>
<p>We want to thank everyone who filed issues, tested previews, improved docs, and submitted fixes
during the PowerShell 7.6 release cycle.</p>
<h2>Call to action</h2>
<p>Install PowerShell 7.6 now.</p>
<p>For more information, see the following articles:</p>
<ul>
<li><a href="https://learn.microsoft.com/powershell/scripting/install/install-powershell">Install PowerShell on Windows, Linux, and macOS</a></li>
<li><a href="https://learn.microsoft.com/powershell/scripting/whats-new/what-s-new-in-powershell-76">What&#8217;s New in PowerShell 7.6</a></li>
</ul>
<h2>Looking ahead</h2>
<p>We continue to work on future releases of PowerShell. See <a href="https://devblogs.microsoft.com/powershell/powershell-openssh-and-dsc-team-investments-for-2026/">Steve Lee&#8217;s recent blog</a> post about
our future plans for PowerShell 7.7 and beyond.</p>
<p>Preview releases will continue to provide early access to new capabilities and improvements.</p>
<p>PowerShell Team</p>
<p><!-- link references --></p>
<p>The post <a href="https://devblogs.microsoft.com/powershell/announcing-powershell-7-6/">Announcing PowerShell 7.6 (LTS) GA Release</a> appeared first on <a href="https://devblogs.microsoft.com/powershell">PowerShell Team</a>.</p>

---
title: "Announcing Microsoft.PowerShell.PlatyPS 1.0.0"
url: "https://devblogs.microsoft.com/powershell/announcing-platyps-100/"
date: "Thu, 24 Jul 2025 21:35:14 +0000"
author: "Jason Helmick, Sean Wheeler"
feed_url: "https://devblogs.microsoft.com/powershell/feed/"
---
<p><!-- markdownlint-disable MD041 --></p>
<p>We&#8217;re pleased to announce the general availability (GA) release of
<a href="https://www.powershellgallery.com/packages/Microsoft.PowerShell.PlatyPS">Microsoft.PowerShell.PlatyPS v1.0.0</a>.</p>
<p><strong>PlatyPS</strong> is the tool that Microsoft uses to create the PowerShell content you get from <code>Get-Help</code>
and build the content published as <a href="https://learn.microsoft.com/powershell/scripting">PowerShell documentation</a> on Microsoft Learn.</p>
<p>PowerShell help files are stored as <a href="https://wikipedia.org/wiki/Microsoft_Assistance_Markup_Language">Microsoft Assistance Markup Language</a> (MAML), an XML
format. <strong>PlatyPS</strong> simplifies the authoring process by allowing you to write the help files in
Markdown, then convert to MAML. <a href="https://wikipedia.org/wiki/Markdown">Markdown</a> is widely used in the software industry,
supported by many editors including <strong>Visual Studio Code</strong>, and easier to author.</p>
<p>With this release, <strong>Microsoft.PowerShell.PlatyPS</strong> is the supported tool. This release is a
substantial rewrite with all new cmdlets. <strong>platyPS v0.14.2</strong> is no longer supported. We encourage
all users to upgrade to <strong>Microsoft.PowerShell.PlatyPS</strong> for the latest features, performance
improvements, and ongoing support. If you have scripts that use the older version of <strong>platyPS</strong>,
you must rewrite them to use the new cmdlets.</p>
<p><strong>Microsoft.PowerShell.PlatyPS</strong> includes several improvements:</p>
<ul>
<li>Re-write in C# leveraging <a href="https://github.com/xoofx/markdig">markdig</a> for parsing Markdown (the same library used by
Microsoft Learn to render Markdown)</li>
<li>Provides a more accurate description of a PowerShell cmdlet and its parameters and includes
information that was previously unavailable</li>
<li>Creates an object model of the help file that you can manipulate and supports chaining cmdlets for
complex operations</li>
<li>Increased performance &#8211; processes 1000s of Markdown files in seconds</li>
</ul>
<p><strong>Microsoft.PowerShell.PlatyPS</strong> runs on:</p>
<ul>
<li>Windows PowerShell 5.1+</li>
<li>PowerShell 7+ on Windows, Linux, and macOS</li>
</ul>
<h2>Installing Microsoft.PowerShell.PlatyPS</h2>
<p>To begin working with <strong>Microsoft.PowerShell.PlatyPS 1.0.0</strong>, install the module from PSGallery.</p>
<pre><code class="language-powershell">Install-PSResource -Name Microsoft.PowerShell.PlatyPS</code></pre>
<h2>Documentation to get started</h2>
<p>For this release, the cmdlet reference is available at <a href="https://learn.microsoft.com/powershell/module/microsoft.powershell.platyps">Microsoft.PowerShell.PlatyPS</a>.
For an example of how to use the new cmdlets, see <em>Example #1</em> in <a href="https://learn.microsoft.com/powershell/module/microsoft.powershell.platyps/new-markdowncommandhelp#example-1-create-markdown-help-files-for-a-module">New-MarkdownCommandHelp</a>.</p>
<h2>Call to action</h2>
<p>Our goal is to make it easier for you to update and maintain PowerShell help files. We value your
feedback. Stop by our <a href="https://github.com/PowerShell/platyPS">GitHub repository</a> and let us know of any issues you find.</p>
<p>Interested in contributing to the PlatyPS project? We welcome feature ideas and contributions.
Please follow the contribution guidance in the <a href="https://github.com/PowerShell/platyPS/blob/main/README.md">Github Readme</a>.</p>
<p>Jason Helmick</p>
<p>Sr. Product Manager, PowerShell</p>
<p><!-- link references --></p>
<p>The post <a href="https://devblogs.microsoft.com/powershell/announcing-platyps-100/">Announcing Microsoft.PowerShell.PlatyPS 1.0.0</a> appeared first on <a href="https://devblogs.microsoft.com/powershell">PowerShell Team</a>.</p>

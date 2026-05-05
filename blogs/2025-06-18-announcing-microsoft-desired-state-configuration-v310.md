---
title: "Announcing Microsoft Desired State Configuration v3.1.0"
url: "https://devblogs.microsoft.com/powershell/announcing-dsc-v3-1-0/"
date: "Wed, 18 Jun 2025 14:12:40 +0000"
author: "Jason Helmick"
feed_url: "https://devblogs.microsoft.com/powershell/feed/"
---
<p><!-- markdownlint-disable MD041 --></p>
<p>We&#8217;re pleased to announce the General Availability of Microsoft&#8217;s Desired State Configuration (DSC)
version 3.1.0. This release marks a significant milestone in our effort to deliver cloud-native
configuration management for cross-platform environments. DSC is a declarative configuration and
orchestration platform that defines a standard way of exposing settings for applications and
services. DSC v3.1.0 is built on collaboration with key improvements driven by partner requests.
Special thanks to the Windows Package Manager (WinGet) team and the incredible support of the DSC
community.</p>
<p>For additional details about the initial DSC v3.0.0 release, see:</p>
<ul>
<li>DSC v3.0.0 <a href="https://devblogs.microsoft.com/powershell/announcing-dsc-v3/">Announcement</a></li>
<li>DSC v3.0.0 <a href="https://devblogs.microsoft.com/powershell/get-started-with-dsc-v3/">Get Started</a></li>
<li>DSC v3.0.0 <a href="https://devblogs.microsoft.com/powershell/enhanced-authoring-with-dsc-v3/">Enhanced Authoring</a></li>
</ul>
<h2>What’s New in DSC v3.1</h2>
<p>This release continues our momentum by delivering features and improvements
driven by real world use, partner feedback, and community contributions.</p>
<p>DSC v3.1 includes updates and fixes across the platform. Here are some of the
most important improvements:</p>
<p><strong>WinGet and partner-driven enhancements</strong></p>
<ul>
<li>Core infrastructure updates to enable DSC-based management in WinGet scenarios.</li>
<li>Extended resource invocation APIs, allowing for richer integration by external tools.</li>
<li>Increased flexibility for configuration refresh and reporting, driven by partner needs.</li>
</ul>
<p><strong>Resource authoring improvements</strong></p>
<ul>
<li>Improved handling and validation for resource schema files, with clearer error messages.</li>
<li>Fixed issues with module loading and path resolution that impacted PSDSC resources.</li>
<li>More robust handling of resources with required and optional properties.</li>
</ul>
<p><strong>Cross-Platform reliability and bug fixes</strong></p>
<ul>
<li>Fixed several Linux-specific issues in resource execution, state detection, and error
reporting.</li>
<li>Improved Windows compatibility, particularly for recent versions and in mixed-OS
environments.</li>
<li>Addressed inconsistencies in the application of <strong>ensure</strong> properties and desired state
evaluation.</li>
</ul>
<p><strong>Performance and quality</strong></p>
<ul>
<li>Optimized configuration drift detection, resulting in faster and more reliable test
operations.</li>
<li>Reduced occurrence of configuration runs left in an indeterminate or failed state.</li>
<li>Improved error handling for edge cases in <code>set</code>, <code>test</code>, and <code>get</code> operations.</li>
</ul>
<p><strong>Diagnostics and usability</strong></p>
<ul>
<li>Expanded logging and diagnostics, making it easier to trace resource behavior and
configuration activity.</li>
<li>Improved the clarity and usefulness of error and warning messages across platforms.</li>
<li>More consistent reporting of operation outcomes in both interactive and automated
scenarios.</li>
</ul>
<p>For a full list of changes, see the <a href="https://github.com/PowerShell/DSC/blob/main/CHANGELOG.md">DSC v3.1 changelog</a></p>
<h2>Installing DSC</h2>
<p>To get started, follow these steps to install DSC on your system:</p>
<p>On Windows, you can install DSC from the Microsoft Store using <code>winget</code>. By installing from the
Store or using <code>winget</code>, you get automatic updates for DSC.</p>
<p>Search for the latest version of DSC:</p>
<pre><code class="language-powershell">winget search DesiredStateConfiguration --source msstore</code></pre>
<pre><code class="language-output">Name                              Id           Version Source
---------------------------------------------------------------
DesiredStateConfiguration         9NVTPZWRC6KQ Unknown msstore
DesiredStateConfiguration-Preview 9PCX3HX4HZ0Z Unknown msstore</code></pre>
<p>Install DSC using the <code>id</code> parameter:</p>
<pre><code class="language-powershell"># Install latest stable
winget install --id 9NVTPZWRC6KQ --source msstore</code></pre>
<pre><code class="language-powershell"># Install latest preview
winget install --id 9PCX3HX4HZ0Z --source msstore</code></pre>
<p>On Linux and macOS, you can install DSC using the following steps:</p>
<ol>
<li>Download the latest release from the <a href="https://github.com/PowerShell/DSC/releases">PowerShell/DSC</a> repository.</li>
<li>Expand the release archive.</li>
<li>Add the folder containing the expanded archive contents to your <code>PATH</code> environment variable.</li>
</ol>
<h2>Support lifecycle</h2>
<p>DSC follows semantic versioning. </p>
<p>The first release of DSC version 3.0.0 is a Stable release. DSC version 3.1.0 is the current Stable
release. Patch releases update the third digit of the semantic version number. For example, 3.1.1 is
a patch update to 3.1.0. Stable releases receive patches for critical bugs and security
vulnerabilities for three months after the next Stable release. For example, version 3.1.0 is
supported for three months after 3.2.0 is released.</p>
<p>Always update to the latest patch version of the release you&#8217;re using.</p>
<h2>Call to action</h2>
<p>For more information about Desired State Configuration v3.0 (DSC), see the <a href="https://learn.microsoft.com/powershell/dsc/overview?view=dsc-3.0">DSC documentation</a>.
We value your feedback. Stop by our <a href="https://github.com/PowerShell/DSC">GitHub repository</a> and let us know of any issues you find.</p>
<p>Jason Helmick</p>
<p>Sr. Product Manager, PowerShell</p>
<p><!-- link references --></p>
<p>The post <a href="https://devblogs.microsoft.com/powershell/announcing-dsc-v3-1-0/">Announcing Microsoft Desired State Configuration v3.1.0</a> appeared first on <a href="https://devblogs.microsoft.com/powershell">PowerShell Team</a>.</p>

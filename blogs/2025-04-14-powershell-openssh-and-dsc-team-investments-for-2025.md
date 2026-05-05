---
title: "PowerShell, OpenSSH, and DSC team investments for 2025"
url: "https://devblogs.microsoft.com/powershell/powershell-openssh-and-dsc-team-investments-for-2025/"
date: "Mon, 14 Apr 2025 13:40:29 +0000"
author: "Steve Lee"
feed_url: "https://devblogs.microsoft.com/powershell/feed/"
---
<h1>Team investments for 2025</h1>
<p>First, apologies getting this out so late into the year.
We&#8217;ve been very busy and just found the time to write this update.</p>
<h2>Security improvements</h2>
<p>We continue to treat security as a top priority and as issues are discovered or reported,
we will continue to prioritize these issues over new feature development.</p>
<h2>Bug fixes and community PRs</h2>
<p>We continue to fix various reported issues, as well as prioritizing the review and merging of community pull requests.
Based on community feedback, we&#8217;re now using a <a href="https://github.com/orgs/PowerShell/projects/44">GitHub project</a> to provide transparency
on which issues and pull requests team members are focusing on.</p>
<h2>PowerShell 7.6</h2>
<p>PowerShell 7.6 will be our latest Long-Term Servicing (LTS) release.
We continue to align with the .NET 10 release cycle and support lifecycle.
There have already been 4 preview releases published.</p>
<h3>Moving PowerShell content folder out of MyDocuments</h3>
<p>This has been a long-standing request from the community due to automatic sync of MyDocuments folder and OneDrive.
While some users want to leverage OneDrive for syncing across their systems,
many other users complain about the performance impact on PowerShell module discovery when modules are stored in the OneDrive folder.
There was a previous experimental feature <a href="https://github.com/PowerShell/PowerShell/pull/18152">PSModuleAutoLoadSkipOfflineFiles</a> that is now mainstream in PowerShell 7.5.
With this change, PowerShell skips modules that are not marked being available locally.
However, this also led to confusion for users who expected their modules to be available when they were not on disk.</p>
<p>As any change here is a breaking change, we&#8217;ve spent a lot of time discussing the best way to approach this.
We are close to finishing a proposal that we will publish to the <a href="https://github.com/powershell/powershell-rfc">PowerShell-RFC</a> repository for
community feedback when ready.
We will have experimental feature available within the 7.6 preview cycle for users to test and provide feedback on.</p>
<p>Note that the PowerShell content folder does not just contain modules, but also the user&#8217;s PowerShell profile, scripts installed from PowerShell Gallery,
and updated help files.</p>
<h3>Enable native commands to integrate with PowerShell more easily</h3>
<p>A common ask from several of our Microsoft partners who are building native commands (Azure CLI, Winget) is to more easily
integrate features such as Feedback Providers and Tab Completion where they don&#8217;t need to publish a separate module from their
application.</p>
<p>We have already published a <a href="https://github.com/PowerShell/PowerShell-RFC/pull/386">design proposal in our RFC repo</a> and would welcome
any feedback from the community.
One of the key requirements is that an application&#8217;s install and uninstall should be clean and not leave behind any artifacts in PowerShell.</p>
<h3>Update <code>PATH</code> environment variable for WinGet</h3>
<p>Currently, if you use WinGet to install a package, it will not update the <code>PATH</code> environment variable.
This means that newly installed applications are not available in the current PowerShell session.
This feature will be similar to the one made in <code>cmd.exe</code> and only apply to a specific applications.</p>
<h3>PowerShell 7 configuration as DSC v3 resource</h3>
<p>As part of our work to enable managing popular developer applications&#8217; settings,
we are working on exposing <code>pwsh</code> as a DSC v3 resource.
This will allow users to manage the settings of PowerShell 7 in a declarative manner.</p>
<h2>PowerShell Gallery</h2>
<p>Significant behind-the-scenes work is happening to migrate the PowerShell Gallery from an Azure Cloud Services classic application
to one hosted on Azure Kubernetes Service (AKS).
This is a difficult effort but, ideally, one that won&#8217;t affect user access or performance.</p>
<h3>EntraID server-side support</h3>
<p>Concurrently, we are working on support for EntraID authentication that
allows users to use a managed identify to publish modules to the PowerShell Gallery instead of an API key.</p>
<h2>PSResourceGet</h2>
<h3>EntraID client-side support</h3>
<p>Along with the changes necessary on the PowerShell Gallery side, corresponding changes are being made to PSResourceGet
to support EntraID authentication.</p>
<h3>Complete Micorosft Artifact Registry (MAR) support</h3>
<p>We continue to progress towards General Availability for support of <a href="https://github.com/microsoft/containerregistry">Microsoft Artifact Registry (MAR)</a> in PSResourceGet.
This allows users to have a default trusted repository for modules and scripts published by Microsoft.
This is built on top of the support we already added for <a href="https://azure.microsoft.com/products/container-registry/">Azure Container Registry (ACR)</a>
Over time, we plan to generally support <a href="https://oras.land/">ORAS</a> as a standard for storing artifacts in container registries, which would enable
support any container registry that supports the OCI distribution spec.</p>
<h2>Windows OpenSSH</h2>
<p>We continue to merge upstream OpenSSH changes into our Windows OpenSSH distribution with previews published to <a href="https://github.com/PowerShell/Win32-OpenSSH/releases">GitHub</a>
and the final release updated into Windows.</p>
<h3>DSC v3 resource</h3>
<p>We continue to develop a DSC v3 resource for <code>SSHD_CONFIG</code> with expectations that previews will be available later this year.</p>
<h2>Desired State Configuration v3 (DSC)</h2>
<p>We already <a href="https://devblogs.microsoft.com/powershell/announcing-dsc-v3/">announced DSC 3.0 General Availablity</a> last month and already have
two service updates available.</p>
<p>DSC v3.0 is available in the <a href="https://apps.microsoft.com/detail/9nvtpzwrc6kq?hl=en-us&amp;gl=US">Microsoft Store</a> or from our <a href="https://github.com/PowerShell/DSC/releases">GitHub repo</a>.
The macOS and Linux releases are curently only available from our GitHub repo.</p>
<h3>DSC v3.1</h3>
<p>In addition, we are making rapid progress on a <a href="https://github.com/PowerShell/DSC/releases/tag/v3.1.0-preview.3">DSC v3.1 release with multiple previews</a> already available.
Preview releases are also available from the <a href="https://apps.microsoft.com/detail/9pcx3hx4hz0z?hl=en-us&amp;gl=US">Microsoft Store</a> or our GitHub repo.</p>
<p>You can see what features are <a href="https://github.com/PowerShell/DSC/issues?q=is%3Aissue%20state%3Aopen%20milestone%3A3.1-Approved">approved</a> or
being <a href="https://github.com/PowerShell/DSC/issues?q=is%3Aissue%20state%3Aopen%20milestone%3A3.1-Consider">considered</a> for the 3.1 release.</p>
<h2>AI Shell</h2>
<p>Our <a href="https://github.com/powershell/aishell">AI Shell</a> project continues to make progress towards integration of AI into the shell to
boost productivity.</p>
<p>Some further improvements being planned:</p>
<ul>
<li>Better macOS support</li>
<li>Enhanced Azure PowerShell support</li>
<li>Expansion of new Agents</li>
<li>Better integration with PowerShell</li>
<li>Support for <a href="https://modelcontextprotocol.io/introduction">Model Context Protocol (MCP)</a></li>
</ul>
<h2>Other tooling updates</h2>
<p>We will continue to address reported issues and merge community pull requests for the following projects:</p>
<ul>
<li>PowerShell VSCode extension</li>
<li>PowerShell Script Analyzer</li>
<li>others as needed</li>
</ul>
<h2>Conclusion</h2>
<p>Security is our top priority. We continue to improve the security of how we deliver software. Those improvements are not visible to the community, but they ensure that we are delivering secure software.
We will continue to work on the community&#8217;s top issues and pull requests across our many projects, when possible.
We are very thankful to our active community members!</p>
<p>The post <a href="https://devblogs.microsoft.com/powershell/powershell-openssh-and-dsc-team-investments-for-2025/">PowerShell, OpenSSH, and DSC team investments for 2025</a> appeared first on <a href="https://devblogs.microsoft.com/powershell">PowerShell Team</a>.</p>

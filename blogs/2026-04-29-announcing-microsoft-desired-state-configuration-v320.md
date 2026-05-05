---
title: "Announcing Microsoft Desired State Configuration v3.2.0"
url: "https://devblogs.microsoft.com/powershell/announcing-dsc-v3-2-0/"
date: "Wed, 29 Apr 2026 18:31:13 +0000"
author: "Jason Helmick"
feed_url: "https://devblogs.microsoft.com/powershell/feed/"
---
<p><!-- markdownlint-disable MD041 --></p>
<h1>Announcing DSC v3.2.0</h1>
<p>We&#8217;re excited to announce the General Availability of Microsoft Desired State Configuration (DSC)
v3.2.0. This release delivers new built-in Windows resources, experimental Bicep integration via
gRPC, version pinning, a richer expression language, custom functions, and continued adapter
improvements. All these changes are driven by real-world use, partner feedback, and community
contributions. Special thanks to the WinGet team and the incredible DSC community.</p>
<p>For background on the DSC v3 platform, see:</p>
<ul>
<li>DSC v3.0.0 <a href="https://devblogs.microsoft.com/powershell/announcing-dsc-v3/">Announcement</a></li>
<li>DSC v3.1.0 <a href="https://devblogs.microsoft.com/powershell/announcing-dsc-v3-1-0/">Announcement</a></li>
</ul>
<h2>What&#8217;s New in DSC v3.2</h2>
<h3>New Windows resources</h3>
<p>DSC v3.2 ships several new built-in Windows resources, significantly expanding what you can manage
out of the box:</p>
<ul>
<li><code>Microsoft.Windows/Service</code> — manage Windows services</li>
<li><code>Microsoft.Windows/OptionalFeatureList</code> — manage Windows Optional features
<ul>
<li>Requires using the ZIP package of DSC for now</li>
</ul>
</li>
<li><code>Microsoft.Windows/FeatureOnDemandList</code> — manage Windows Features on Demand
<ul>
<li>Requires using the ZIP package of DSC for now</li>
</ul>
</li>
<li><code>Microsoft.Windows/FirewallRuleList</code> — manage Windows Firewall rules</li>
<li><code>Microsoft.OpenSSH.SSHD/sshd_config</code> — manage entire SSH server configuration</li>
<li><code>Microsoft.OpenSSH.SSHD/Subsystem</code> and <code>Microsoft.OpenSSH.SSHD/SubsystemList</code> — manage SSH server
configuration for subsystem entries</li>
<li><code>Microsoft.OpenSSH.SSHD/Windows</code> — manage Windows SSH server configuration, such as the default
shell</li>
</ul>
<p>These resources are included in the DSC package and ready to use without additional installation.</p>
<h3>Bicep integration via gRPC (experimental)</h3>
<p>DSC v3.2 introduces a gRPC server, enabling Bicep to orchestrate DSC resources directly. The
<code>dsc-bicep-ext</code> extension is now included in the MSIX package and exposed on <code>PATH</code>.</p>
<p>This is the foundation for the <em>Bicep to DSC integration</em>. Write your configuration in Bicep. Bicep
orchestrates the execution directly over gRPC without going through ARM.</p>
<h3>Extended WhatIf support</h3>
<p>DSC v3.2 adds <code>--what-if</code> support to the <code>dsc resource set</code> command, letting you preview changes
before applying them:</p>
<pre><code class="language-bash">dsc resource set --what-if --resource Microsoft.Windows/Service --input '{
    "name": "spooler",
    "startupType": "disabled"
}'</code></pre>
<p>Prior to this release there was no way to run <code>--what-if</code> against individual resources. You could
use the <code>--what-if</code> flag with the <code>dsc config set</code> command, which ran all resources in your
configuration in <code>--what-if</code> mode.</p>
<p>Resource manifests can now declare <code>whatIfReturns</code> to describe what a what-if operation returns,
enabling richer preview output across resources.</p>
<h3>Version pinning</h3>
<p>DSC v3.2 supports pinning configuration documents to specific versions of DSC and pinning resource
instances in configuration documents to specific versions of the resource.</p>
<p>Now you can author a DSC configuration document and ensure that it only executes when the given
versions of DSC and resources that are available on the system. Prior to this release, DSC always
used the latest version of a resource discovered on a system for configuration operations.</p>
<p>The following example shows how to pin a configuration document to a specific version of DSC using
the <code>version</code> directive and how to pin individual resource instances to specific versions using the
<code>requireVersion</code> field.</p>
<pre><code class="language-yaml">$schema: https://aka.ms/dsc/schemas/v3/bundled/config/document.json
directives:
  version: '=3.2.0' # This configuration is only valid for exactly version 3.2.0
resources:
- name: os
  type: Microsoft/OSInfo
  requireVersion: '^1.0' # Resource versions &gt;= 1.0.0 and &lt; 2.0.0 are valid
  properties: {}
- name: echo
  type: Microsoft.DSC.Debug/Echo
  requireVersion: '&gt;=1.0.0, &lt;1.3'
  properties:
    output: echo</code></pre>
<p>When DSC evaluates a resource version pin in a configuration document, it looks for the latest
version of the resource that meets the given requirement. If no compatible version is discovered
on the system, DSC raises an error.</p>
<p>Starting with version 3.2, when you specify the <code>version</code> directive, DSC raises an error when the
version of DSC operating on the configuration document isn&#8217;t compatible.</p>
<h3>Expression language improvements</h3>
<p>Configuration documents now support a richer expression syntax:</p>
<ul>
<li><strong>Lambda expressions</strong> with <code>map()</code> and <code>filter()</code> functions (ARM syntax)</li>
<li><strong><code>dataUri()</code></strong> and <strong><code>dataUriToString()</code></strong> functions</li>
<li><strong><code>reference()</code></strong> usage inside <code>copy</code> loops</li>
<li><strong><code>requireVersion</code></strong> replaces <code>apiVersion</code> for version requirements</li>
</ul>
<p>These additions make configuration documents more expressive and reduce the need to duplicate
values across resources.</p>
<h3>Adapter improvements</h3>
<p>DSC 3.2 adds support for adapted resource manifests to the PowerShell adapters. Resource authors can
create <em>adapted resource manifests</em> that prevent adapters from needing to do more intensive
discovery operations.</p>
<p>This release also includes other improvements to the PowerShell adapters:</p>
<ul>
<li>Added automatic conversion of PowerShell streams to DSC traces. Resource authors can participate
in DSC&#8217;s tracing model by using the normal <code>Write-*</code> cmdlets.</li>
<li>Fixed passing credentials to adapted PSDSC resource instances.</li>
</ul>
<h3>Metadata and execution improvements</h3>
<ul>
<li><code>Microsoft.DSC</code> metadata is now split into <code>directives</code> and <code>executionInformation</code> — cleaner
separation of configuration intent from execution context.</li>
<li><code>_refreshEnv</code> resource metadata updates Windows environment variables during deployment without
requiring a restart.</li>
<li>Resource manifests can now specify <code>requireSecurityContext</code> per operation, helping users avoid
problems where they retrieve data for a resource with a <code>get</code> or <code>test</code> operation and then get an
access denied error when they try to run the <code>set</code> command.</li>
<li>Resources and extensions can now be marked as <strong>deprecated</strong>, with a deprecation message surfaced
at runtime.</li>
</ul>
<h3>New extension capabilities</h3>
<p>DSC 3.2 adds support for two new extension capabilities: importing configurations and retrieving
secrets.</p>
<p>You can use an extension with the <code>import</code> capability to process arbitrary files as DSC
configuration documents. For example, a hypothetical extension with this capability could transform
the following TOML snippet into a DSC configuration document:</p>
<pre><code class="language-toml"># example.dsc.toml
[directives]
version = '3.2.0'
[resources.os]
type       = 'Microsoft/OSInfo'
properties = {}</code></pre>
<p>The resulting DSC configuration document:</p>
<pre><code class="language-yaml"># effective DSC configuration document
$schema: https://aka.ms/dsc/schemas/v3/bundled/config/document.json
directives:
  version: '=3.2.0' # This configuration is only valid for exactly version 3.2.0
resources:
- name: os
  type: Microsoft/OSInfo
  properties: {}</code></pre>
<p>When you use the <code>--file</code> option with the <code>dsc config *</code> commands, DSC checks the file extension to
see whether an extension can process that file. If there is no DSC extension that handles the given
file extension, DSC tries to parse the file as a configuration document.</p>
<p>You can use a DSC extension with the <code>secret</code> capability to retrieve secrets at runtime. Presenting
secret retrieval through the extension model enables DSC to be used with secrets in a variety of
contexts without requiring the core engine to handle these operations directly. This capability is
paired with the new <code>secret()</code> configuration expression for retrieving secrets by name.</p>
<h3>Experimental PowerShell discovery extension</h3>
<p>DSC now includes a discovery extension for finding DSC resources in PowerShell modules. This
extension looks for resource manifests and adapted resource manifests located inside PowerShell
modules on the system. This makes it possible for resource authors to ship DSC resources written
in PowerShell that are <em>not</em> PSDSC resources.</p>
<p>For example, with this extension, DSC could discover a resource implemented as a PowerShell script
as long as the module <em>also</em> includes a valid manifest for the resource.</p>
<h3>Bug fixes</h3>
<ul>
<li>Fixed duplicate resources appearing in <code>dsc resource list</code></li>
<li>Added a clear error when attempting to use DISM resources via Appx (previously a silent failure)</li>
<li>Fixed <code>executionInformation</code> in config export results</li>
<li>Fixed discovery failures when encountering unsupported manifests</li>
</ul>
<h2>Community contributions</h2>
<p>DSC v3.2 reflects the work of an active and growing contributor community. The following community
members made notable contributions to this release:</p>
<ul>
<li><strong>@Gijsreyn (Gijs Reijn)</strong> — experimental PowerShell discovery extension, <code>lambda</code>/<code>map</code>/<code>filter</code>
expressions, <code>dataUri</code> functions, adapted resource manifest fixes, and more.</li>
<li><strong>@mimachniak</strong> — PowerShell adapter credentials fix for passing username and password.</li>
</ul>
<p>Thank you to everyone who filed issues, tested previews, and submitted fixes during the DSC v3.2
release cycle.</p>
<h2>Installing DSC</h2>
<p>On Windows, you can install DSC from the Microsoft Store using <code>winget</code>. Installing from the Store
gives you automatic updates.</p>
<p>Search for the latest version of DSC:</p>
<pre><code class="language-powershell">winget search DesiredStateConfiguration --source msstore

Name                              Id           Version
------------------------------------------------------
DesiredStateConfiguration         9NVTPZWRC6KQ Unknown
DesiredStateConfiguration-Preview 9PCX3HX4HZ0Z Unknown</code></pre>
<p>Install DSC using the <code>id</code> parameter:</p>
<p><!-- TODO: confirm Store ID with Mikey --></p>
<pre><code class="language-powershell"># Install latest stable
winget install --id 9NVTPZWRC6KQ --source msstore</code></pre>
<pre><code class="language-powershell"># Install latest preview
winget install --id 9PCX3HX4HZ0Z --source msstore</code></pre>
<p>To install the ZIP package on Windows, Linux, or macOS:</p>
<ol>
<li>Download the latest release from the <a href="https://github.com/PowerShell/DSC/releases">PowerShell/DSC</a> repository.</li>
<li>Expand the release archive.</li>
<li>Add the folder containing the expanded archive contents to your <code>PATH</code> environment variable.</li>
</ol>
<h2>Support lifecycle</h2>
<p>DSC follows semantic versioning. DSC v3.2.0 is the current stable release. Patch releases update
the third digit of the semantic version number — for example, 3.2.1 is a patch update to 3.2.0.</p>
<p>Stable releases receive patches for critical bugs and security vulnerabilities for three months
after the next stable release. For example, v3.2.0 is supported for three months after v3.3.0 is
released.</p>
<p>Always update to the latest patch version of the release you&#8217;re using.</p>
<h2>Looking ahead</h2>
<p>Work continues on DSC v3.3, with previews starting shortly after the v3.2.0 GA release.</p>
<h2>Call to action</h2>
<p>For more information about DSC, see the <a href="https://learn.microsoft.com/powershell/dsc">DSC documentation</a>. We value your feedback. Stop by our
<a href="https://github.com/PowerShell/DSC">GitHub repository</a> and let us know of any issues you find.</p>
<p>Jason Helmick</p>
<p>Sr. Product Manager, PowerShell</p>
<p><!-- updated link references --></p>
<p>The post <a href="https://devblogs.microsoft.com/powershell/announcing-dsc-v3-2-0/">Announcing Microsoft Desired State Configuration v3.2.0</a> appeared first on <a href="https://devblogs.microsoft.com/powershell">PowerShell Team</a>.</p>

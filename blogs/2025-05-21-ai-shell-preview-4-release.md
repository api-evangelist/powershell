---
title: "AI Shell Preview 4 Release!"
url: "https://devblogs.microsoft.com/powershell/preview-4-ai-shell/"
date: "Wed, 21 May 2025 15:16:13 +0000"
author: "Steven Bucher"
feed_url: "https://devblogs.microsoft.com/powershell/feed/"
---
<p><!-- markdownlint-disable MD041 --></p>
<h1>AI Shell Preview 4 Is here: Better macOS support, and more!</h1>
<p>We&#8217;re excited to share the latest preview release of AI Shell that includes new features and
improvements based on your feedback. This release focuses on improving the user experience by
improving access to Azure OpenAI deployments, improvements to the <code>Invoke-AIShell</code> command, and
expanded compatibility with macOS.</p>
<h2>MacOS support improvements</h2>
<p>We&#8217;ve made significant improvements to the macOS side car experience with iTerm2. Previously, the
side car experience was unreliable and didn&#8217;t support the <code>/code post</code> command. Now you have a more
reliable experience with feature parity with your experience on Windows. For this experience you
need to run PowerShell 7 in iTerm2. For more information about PowerShell 7 on macOS, see
<a href="https://learn.microsoft.com/powershell/scripting/install/installing-powershell-on-macos">Installing PowerShell on macOS</a>.</p>
<p><img alt="AI Shell Preview 4 on mac" src="https://devblogs.microsoft.com/powershell/wp-content/uploads/sites/30/2025/05/macdemo.gif" /></p>
<h2>Support for Microsoft Entra ID</h2>
<p>To keep password and keys secure, we&#8217;ve added support for Entra ID authentication to to Azure OpenAI
instances. Now you can access your Azure OpenAI resource without storing keys in the configuration
file. The following example shows how to configure Entra ID authentication:</p>
<pre><code class="language-jsonc">{
  // Declare GPT instances.
  "GPTs": [
      // Declaration of an Azure OpenAI instance with EntraID authentication
      {
        "Name": "ps-az-entraId",
        "Description": "A GPT instance with expertise in PowerShell scripting using Entra ID authentication.",
        "Endpoint": "&lt;Your Endpoint&gt;",
        "Deployment": "&lt;Your Deployment Name&gt;",
        "ModelName": "&lt;Your Model Name&gt;",
        "AuthType": "EntraID",
        "SystemPrompt": "You are a helpful and friendly assistant with expertise in PowerShell scripting and command line."
      }
  ],

  // Specify the default GPT instance to use for user query.
  "Active": "ps-az-entraId"
}</code></pre>
<p>This is the hierarchy of credentials that AI Shell will use to authenticate to Azure OpenAI:</p>
<ul>
<li><code>EnvironmentCredential</code></li>
<li><code>WorkloadIdentityCredential</code></li>
<li><code>ManagedIdentityCredential</code></li>
<li><code>SharedTokenCacheCredential</code></li>
<li><code>VisualStudioCredential</code></li>
<li><code>AzureCliCredential</code></li>
<li><code>AzurePowerShellCredential</code></li>
<li><code>AzureDeveloperCliCredential</code></li>
<li><code>InteractiveBrowserCredential</code></li>
</ul>
<p>For more information on what these particular credentials are, please see the
<a href="https://learn.microsoft.com/dotnet/api/azure.identity.defaultazurecredential">DefaultAzureCredential</a> reference.</p>
<h2>Invoke-AIShell command additions</h2>
<p>We&#8217;ve added additional parameters to the <code>Invoke-AIShell</code> command to allow for easier use of the
side pane without leaving the left side of the screen.</p>
<ul>
<li><code>-PostCode</code> &#8211; This parameter allows you to post code generated from the side pane to the connected
PowerShell session. It reduces the need to switch between the side pane and terminal to run the
<code>/code post</code> command.</li>
<li><code>-CopyCode</code> &#8211; This parameter allows you to copy code from the side pane without using the
<code>/code copy</code> command.</li>
<li><code>-Exit</code> &#8211; This parameter allows you to exit the side pane without using the <code>/exit</code>
command.</li>
</ul>
<p><img alt="Video of Invoke-AIShell Demo." src="https://devblogs.microsoft.com/powershell/wp-content/uploads/sites/30/2025/05/InvokeAIShellDemo.gif" /></p>
<p>These new parameters allow you to use your terminal normally. You can inject AI generated commands
without cluttering your main buffer and keep all the details and descriptions in the side pane. This
is a great way to use AI Shell as side by side shell assistant! Coupled with PSReadLine Predictive
IntelliSense, you can quickly and easily use AI Shell in your normal shell workflow.</p>
<h2>Phi Silica agent</h2>
<p>We&#8217;ve added a new experimental agent called <strong>Phi Silica</strong>. This agent uses the built-in Phi Silica
model included with the latest Copilot+ PCs, allowing you to have an offline experience with AI
Shell.</p>
<p><div class="alert alert-primary"><p class="alert-divider"><i class="fabric-icon fabric-icon--Info"></i><strong>Note</strong></p>This agent isn&#8217;t shipped with the default installation of AI
Shell. To use this agent, you need to clone the repo and build the code. Follow the instructions at
<a href="https://github.com/PowerShell/AIShell?tab=readme-ov-file#locally-building-ai-shell">
Locally Building AI Shell</a>.</div></p>
<p><img alt="Phi Silica Agent" src="https://devblogs.microsoft.com/powershell/wp-content/uploads/sites/30/2025/05/PhiSilicaAgentDemo.gif" /></p>
<p>This experimental AI provider is a proof of concept that&#8217;s still under development. You should only
use it for testing. Expect breaking changes in future releases.</p>
<h2>Additional minor improvements</h2>
<p>Here are a few additional improvements that have been made in this release:</p>
<ul>
<li>Updated model information to support latest OpenAI models (<a href="https://github.com/PowerShell/AIShell/pull/368">#368</a>)</li>
<li>Add /clear as an alias to the command /cls to clear console in AIShell (<a href="https://github.com/PowerShell/AIShell/pull/370">#370</a>)</li>
<li>Update installation script to install the AIShell module on macOS too (<a href="https://github.com/PowerShell/AIShell/pull/374">#374</a>)</li>
<li>Enhanced model management and system prompt integration in OllamaAgent (<a href="https://github.com/PowerShell/AIShell/pull/351">#351</a>) (Thanks
<a href="https://github.com/cnupy">@cnupy!</a>)</li>
</ul>
<p>To see the full list of changes, check out the changelog in the <a href="https://github.com/PowerShell/AIShell/releases/tag/v1.0.0-preview.4">release page</a>.</p>
<h2>How to install AI Shell Preview 4</h2>
<p>To install the latest version of AI Shell, run the following command in your PowerShell terminal:</p>
<pre><code class="language-powershell">Invoke-Expression "&amp; { $(Invoke-RestMethod 'https://aka.ms/install-aishell.ps1') }"</code></pre>
<p>As usual we would love for you to try AI Shell and provide feedback in our <a href="https://github.com/PowerShell/AIShell/issues">GitHub repository</a>.</p>
<p>Thanks so much!</p>
<p>AI Shell Team</p>
<p>Steven Bucher &amp; Dongbo Wang</p>
<p><!-- updated link references --></p>
<p>The post <a href="https://devblogs.microsoft.com/powershell/preview-4-ai-shell/">AI Shell Preview 4 Release!</a> appeared first on <a href="https://devblogs.microsoft.com/powershell">PowerShell Team</a>.</p>

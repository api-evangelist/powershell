---
title: "Introducing MCP Support in AI Shell Preview 6"
url: "https://devblogs.microsoft.com/powershell/preview-6-ai-shell/"
date: "Tue, 05 Aug 2025 18:40:38 +0000"
author: "Steven Bucher"
feed_url: "https://devblogs.microsoft.com/powershell/feed/"
---
<p><!-- markdownlint-disable MD041 --></p>
<h1>AI Shell Preview 6 is here!</h1>
<p>We are super excited to announce the latest preview release of AI Shell. This release focuses on
enhancing the user experience with new features, improved error handling, and better integration
with Model Context Protocol (MCP) tools.</p>
<h2>What&#8217;s new at a glance</h2>
<ul>
<li>MCP client integration</li>
<li>Built-in tools</li>
<li><code>Resolve-Error</code> command improvements</li>
<li>Aliases and flows for staying in your terminal</li>
</ul>
<h2>MCP Integration</h2>
<p>AI Shell now acts as an MCP client, which allows you to add any MCP server to your AI Shell
experience. Connecting to an MCP server massively improves the capability of your AI Shell giving
you the tools that provide more relevant data or carry out actions!</p>
<p><img alt="AI Shell MCP Client" src="https://devblogs.microsoft.com/powershell/wp-content/uploads/sites/30/2025/08/AISHMCPDemo.gif" /></p>
<h3>Adding MCP Servers</h3>
<p>To add an MCP server, create an <code>mcp.json</code> file in <code>$HOME\.aish\</code> folder. The following example
shows two MCP servers: <code>everything</code> and <code>filesystem</code>. You can add any MCP servers you want.</p>
<pre><code class="language-json">{
    "servers": {
      "everything":{
        "type":"stdio",
        "command":"npx",
        "args":["-y", "@modelcontextprotocol/server-everything"]
      },
      "filesystem": {
        "type": "stdio",
        "command": "npx",
        "args": [
          "-y",
          "@modelcontextprotocol/server-filesystem",
          "C:/Users/username/"
        ]
      }
    }
  }</code></pre>
<p>If it&#8217;s a remote MCP server, change the type to <code>https</code>. You know that you have successfully added
an MCP server when you see it in the AI Shell UI. You can confirm that it&#8217;s running by checking the
status of the server through the <code>/mcp</code> command. Using <code>/mcp</code> also lists each MCP Server and the
tools available.</p>
<p><img alt="Screenshot of MCP servers registered in AI Shell" src="https://devblogs.microsoft.com/powershell/wp-content/uploads/sites/30/2025/08/mcpui.jpeg" /></p>
<p><div class="alert alert-primary"><p class="alert-divider"><i class="fabric-icon fabric-icon--Info"></i><strong>NOTE</strong></p>You must have <code>Node.js</code> or <code>uv</code> installed to use MCP servers that
use those command lines tools.</div></p>
<h3>Standalone experience with AI Shell and MCP Servers</h3>
<p>MCP servers enhance your standalone experience with AI Shell, allowing your command line to use MCP
servers and AI to perform tasks. For example, <a href="https://github.com/SimonB97/win-cli-mcp-server?tab=readme-ov-file"><code>@simonb97/server-win-cli</code></a> is an MCP server that
allows you to run commands on your Windows machine, whether it be PowerShell, CMD, Git Bash, or any
configured shell you use! It also provides configuration settings to define which commands and
operations are allowed to run.</p>
<p><div class="alert alert-danger"><p class="alert-divider"><i class="fabric-icon fabric-icon--ErrorBadge"></i><strong>CAUTION</strong></p>Please note this is a community MCP server and not an
official Microsoft MCP Server. We encourage you to do your own research and testing before using
it.</div></p>
<p><img alt="AI Shell with MCP Server" src="https://devblogs.microsoft.com/powershell/wp-content/uploads/sites/30/2025/08/standaloneMCPDemo.gif" /></p>
<p>Additional MCP servers:</p>
<ul>
<li><a href="https://github.com/wonderwhy-er/DesktopCommanderMCP">DesktopCommander</a></li>
<li><a href="https://mcpservers.org/">Other community MCP Servers</a></li>
</ul>
<h2>Built-in Tools for AI Shell</h2>
<p>This release introduces built-in tools that are now accessible to agents within AI Shell. These
commands are similar to MCP Server tools, but are exclusive to the AI Shell experience. These tools
are designed to enhance the AI Shell experience by providing context-aware capabilities and
automation features. They can be used in conjunction with the MCP servers to create a powerful
AI-driven shell environment.</p>
<table>
<thead>
<tr>
<th>Tool Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>get_working_directory</code></td>
<td>Get the current working directory of the connected PowerShell session, including the provider name (e.g., <code>FileSystem</code>, <code>Certificate</code>) and the path (e.g., <code>C:\\</code>, <code>cert:\\</code>).</td>
</tr>
<tr>
<td><code>get_command_history</code></td>
<td>Get up to 5 of the most recent commands executed in the connected PowerShell session.</td>
</tr>
<tr>
<td><code>get_terminal_content</code></td>
<td>Get all output currently displayed in the terminal window of the connected PowerShell session.</td>
</tr>
<tr>
<td><code>get_environment_variables</code></td>
<td>Get environment variables and their values from the connected PowerShell session. Values of potentially sensitive variables are redacted.</td>
</tr>
<tr>
<td><code>copy_text_to_clipboard</code></td>
<td>Copy the provided text or code to the system clipboard, making it available for pasting elsewhere.</td>
</tr>
<tr>
<td><code>post_code_to_terminal</code></td>
<td>Insert code into the prompt of the connected PowerShell session without executing it. The user can review and choose to run it manually by pressing Enter.</td>
</tr>
<tr>
<td><code>run_command_in_terminal</code></td>
<td>This tool allows you to execute shell commands in a persistent PowerShell session, preserving environment variables, working directory, and other context across multiple commands.</td>
</tr>
<tr>
<td><code>get_command_output</code></td>
<td>Get the output of a command previously started with <code>run_command_in_terminal</code>.</td>
</tr>
</tbody>
</table>
<p><div class="alert alert-primary"><p class="alert-divider"><i class="fabric-icon fabric-icon--Info"></i><strong>Note</strong></p>The built-in tools rely on the side-car experience with a
connected PowerShell session and provide enhanced context awareness and automation capabilities.</div></p>
<p>Here is a simple demo showing how you can have AI Shell run commands on your behalf using the
<code>run_command_in_terminal</code> tool:</p>
<p><img alt="Run command in terminal tool" src="https://devblogs.microsoft.com/powershell/wp-content/uploads/sites/30/2025/08/openai-agent-1.gif" /></p>
<p>This example shows how additional context is provided to AI Shell to improve results:</p>
<p><img alt="Getting more context with built-in tools" src="https://devblogs.microsoft.com/powershell/wp-content/uploads/sites/30/2025/08/openai-agent-2.gif" /></p>
<p>You can also use the <code>get_terminal_content</code> tool to get the content from the connected terminal and
provide it to AI Shell to help it understand what you are trying to do:</p>
<p><img alt="Getting content from the screen ran before AI Shell starts to get assistance" src="https://devblogs.microsoft.com/powershell/wp-content/uploads/sites/30/2025/08/openai-agent-3.gif" /></p>
<h2>Resolve-Error Command Improvements</h2>
<p>Previously the <code>Resolve-Error</code> command was only able to run after an error occurred in the previous
command. Now, <code>Resolve-Error</code> identifies which command the user wants to troubleshoot:</p>
<ul>
<li>If the last error&#8217;s command matches the most recent command in history, it&#8217;s assumed to be the one
the user is interested in.</li>
<li>If the last error&#8217;s command isn&#8217;t the most recent and <code>$LastErrorCode</code> is null or zero, the error
likely comes from an earlier command, not the very last one.</li>
<li>If <code>$LastErrorCode</code> is non-zero and <code>$?</code> is false, the last command was a failing native command.</li>
<li>If <code>$LastErrorCode</code> is non-zero but <code>$?</code> is true, it&#8217;s unclear which command or failure the user
is focused on, so the agent analyzes the terminal content to determine the relevant context.</li>
</ul>
<p>This logic allows AI Shell to better understand what the error the user is trying to resolve is
rather than requiring you to ask for AI&#8217;s help immediately after an error occurs.</p>
<h2>Staying in your shell</h2>
<p>The <code>Invoke-AIShell</code> and <code>Resolve-Error</code> commands allow you to stay in your working terminal to
interact with the AI Shell agent. To learn more about the parameters added, see the
<a href="https://devblogs.microsoft.com/powershell/preview-4-ai-shell/">previous blog post</a> that details these features. For your convenience, these commands have
aliases that make them quicker to use.</p>
<table>
<thead>
<tr>
<th>Command Name</th>
<th>Alias</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>Invoke-AIShell</code></td>
<td><code>askai</code></td>
</tr>
<tr>
<td><code>Resolve-Error</code></td>
<td><code>fixit</code></td>
</tr>
</tbody>
</table>
<p><img alt="Fixing an error and utilizing fixit and askai commands" src="https://devblogs.microsoft.com/powershell/wp-content/uploads/sites/30/2025/08/openai-agent-4.gif" /></p>
<h2>How to install AI Shell</h2>
<p>To install the latest version of AI Shell, run the following command in your PowerShell terminal:</p>
<pre><code class="language-powershell">Invoke-Expression "&amp; { $(Invoke-RestMethod 'https://aka.ms/install-aishell.ps1') }"</code></pre>
<p>We hope that these enhancements make your experience with AI Shell more powerful! We are always
looking for feedback and suggestions, so please submit issues or feature requests in our
<a href="https://github.com/PowerShell/AIShell">GitHub repository</a>.</p>
<p>Thank you so much!</p>
<p>AI Shell Team</p>
<p>Steven Bucher &amp; Dongbo Wang</p>
<p><!-- link references --></p>
<p>The post <a href="https://devblogs.microsoft.com/powershell/preview-6-ai-shell/">Introducing MCP Support in AI Shell Preview 6</a> appeared first on <a href="https://devblogs.microsoft.com/powershell">PowerShell Team</a>.</p>

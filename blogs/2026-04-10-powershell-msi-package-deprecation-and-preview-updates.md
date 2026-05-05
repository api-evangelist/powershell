---
title: "PowerShell MSI package deprecation and preview updates"
url: "https://devblogs.microsoft.com/powershell/powershell-msi-deprecation/"
date: "Fri, 10 Apr 2026 14:46:23 +0000"
author: "Jason Helmick"
feed_url: "https://devblogs.microsoft.com/powershell/feed/"
---
<p><!-- markdownlint-disable MD041 --></p>
<p>Beginning with PowerShell 7.7-preview.1 (April 2026), the MSIX package will be the primary
installation method for PowerShell on Windows. We will no longer ship the MSI installer package for
new PowerShell releases.</p>
<p>For existing releases, including PowerShell 7.6, we will continue to provide MSI packages. However,
MSI isn&#8217;t planned for future releases, including PowerShell 7.7 GA and beyond.</p>
<h2>Why we&#8217;re making this change</h2>
<p>MSIX provides a modern installation and servicing model and is supported by Windows deployment
tools. It uses a declarative model that&#8217;s more predictable and reliable than MSI, which relies on
custom actions and scripts that can lead to inconsistent behavior. MSIX supports built-in update
mechanisms with differential updates. Microsoft is investing in improving MSIX.</p>
<p>MSI is a legacy technology. Servicing MSI installations requires external tooling and often results
in full reinstalls. MSI doesn&#8217;t meet modern accessibility requirements, particularly for screen
reader scenarios. To be accessible, MSI must present predictable tab stops and accurate
announcements for screen readers, which it doesn&#8217;t. Accessibility is a core requirement for
PowerShell.</p>
<p>This decision isn&#8217;t <em>just</em> about modernizing packaging for its own sake. It&#8217;s about ensuring that
PowerShell installations are modern and accessible for all users, now and in the future.</p>
<h2>Looking forward</h2>
<p>Our goal is to provide a fully accessible, reliable, and enterprise-ready installation experience.
At this time, MSIX doesn&#8217;t support all use case scenarios that MSI enabled, such as remoting and
execution by system-level services (like Task Scheduler). We recognize this gap and are actively
working to address it.</p>
<p>As part of this work, we&#8217;re investing in:</p>
<ul>
<li>Improving MSIX support for system-level and enterprise deployment scenarios</li>
<li>Ensuring accessibility requirements are fully met across all installation paths</li>
<li>Providing clearer guidance and tooling for deployment at scale</li>
</ul>
<p>We will continue to share updates as this work progresses.</p>
<h2>Closing</h2>
<p>We understand this change may require adjustments, especially in environments that rely heavily on
MSI-based deployment. We appreciate your patience as we make this transition.</p>
<p>Our focus is to ensure PowerShell remains accessible, predictable, and practical for all users.</p>
<p>&#8212; The PowerShell Team</p>
<p>The post <a href="https://devblogs.microsoft.com/powershell/powershell-msi-deprecation/">PowerShell MSI package deprecation and preview updates</a> appeared first on <a href="https://devblogs.microsoft.com/powershell">PowerShell Team</a>.</p>

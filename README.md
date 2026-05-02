# PowerShell (powershell)
PowerShell is a cross-platform task automation solution made up of a command-line shell, a scripting language, and a configuration management framework. The PowerShell ecosystem exposes APIs through the PowerShell Gallery (an OData-based package repository), the Runspace .NET hosting APIs, and PowerShell Remoting protocols (WS-Management and SSH).

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/powershell/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consuming
- **Access:** 3rd-Party

## Tags:

 - Automation, Command-Line, Cross-Platform, Scripting, Shell, Windows, DevOps

## Timestamps

- **Created:** 2024-01-15
- **Modified:** 2026-04-28

## APIs

### PowerShell Gallery API
The PowerShell Gallery is the central repository for PowerShell modules, scripts, and DSC resources. It exposes a public OData v2 API for searching, retrieving, and downloading packages programmatically.

**Human URL:** [https://www.powershellgallery.com/](https://www.powershellgallery.com/)

**Base URL:** `https://www.powershellgallery.com/api/v2`

#### Tags:

 - Modules, NuGet, Packages, Repository, OData

#### Properties

- [Documentation](https://docs.microsoft.com/en-us/powershell/gallery/overview)
- [Metadata](https://www.powershellgallery.com/api/v2/$metadata)

### PowerShell Runspace API
.NET APIs for creating, configuring, and managing PowerShell runspaces from host applications. Enables embedding PowerShell execution inside .NET programs.

**Human URL:** [https://docs.microsoft.com/en-us/dotnet/api/system.management.automation.runspaces](https://docs.microsoft.com/en-us/dotnet/api/system.management.automation.runspaces)


#### Tags:

 - Automation, .NET, Runspace, SDK

#### Properties

- [Documentation](https://docs.microsoft.com/en-us/powershell/scripting/developer/hosting/creating-runspaces)
- [SDK](https://www.nuget.org/packages/System.Management.Automation/)
- [Examples](https://github.com/PowerShell/PowerShell/tree/master/test/hosting)

### PowerShell Remoting API
APIs and protocols for remote PowerShell execution over WS-Management (WinRM) and SSH. Enables one-to-one and one-to-many remote command and session management.

**Human URL:** [https://docs.microsoft.com/en-us/powershell/scripting/learn/remoting/running-remote-commands](https://docs.microsoft.com/en-us/powershell/scripting/learn/remoting/running-remote-commands)


#### Tags:

 - Remoting, SSH, WinRM, WS-Management

#### Properties

- [Documentation](https://docs.microsoft.com/en-us/powershell/scripting/learn/remoting/powershell-remoting-faq)
- [ProtocolSpecification](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-psrp/)

## Common Properties

- [Website](https://microsoft.com/powershell)
- [GitHub](https://github.com/PowerShell/PowerShell)
- [Documentation](https://docs.microsoft.com/en-us/powershell/)
- [Blog](https://devblogs.microsoft.com/powershell/)
- [Community](https://github.com/PowerShell/PowerShell/blob/master/docs/community/README.md)
- [GettingStarted](https://docs.microsoft.com/en-us/powershell/scripting/learn/ps101/01-getting-started)
- [License](https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt)
- [Releases](https://github.com/PowerShell/PowerShell/releases)
- [Roadmap](https://github.com/PowerShell/PowerShell/projects)
- [Security](https://github.com/PowerShell/PowerShell/security/policy)
- [Contributing](https://github.com/PowerShell/PowerShell/blob/master/.github/CONTRIBUTING.md)

## Maintainers

**FN:** Microsoft

**Email:** powershell@microsoft.com

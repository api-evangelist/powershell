# PowerShell (powershell)

PowerShell is a cross-platform task automation solution made up of a command-line shell, a scripting language, and a configuration management framework. The PowerShell ecosystem exposes APIs through the PowerShell Gallery (an OData-based package repository), the Runspace .NET hosting APIs, and PowerShell Remoting protocols (WS-Management and SSH).

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/powershell/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/powershell/refs/heads/main/apis.yml)

## Scope

- **Type:** Index

## Tags

- Automation
- Command-Line
- Cross-Platform
- Scripting
- Shell
- Windows
- DevOps

## Timestamps

- **Created:** 2024-01-15
- **Modified:** 2026-04-28

## APIs

### PowerShell Gallery API

The PowerShell Gallery is the central repository for PowerShell modules, scripts, and DSC resources. It exposes a public OData v2 API for searching, retrieving, and downloading packages programmatically.

- **Human URL:** [https://www.powershellgallery.com/](https://www.powershellgallery.com/)
- **Base URL:** `https://www.powershellgallery.com/api/v2`

#### Tags

- Modules
- NuGet
- Packages
- Repository
- OData

#### Properties

- [Documentation](https://docs.microsoft.com/en-us/powershell/gallery/overview)
- [Metadata](https://www.powershellgallery.com/api/v2/$metadata)
- [Postman Collection](collections/powershell.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/powershell.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### PowerShell Runspace API

.NET APIs for creating, configuring, and managing PowerShell runspaces from host applications. Enables embedding PowerShell execution inside .NET programs.

- **Human URL:** [https://docs.microsoft.com/en-us/dotnet/api/system.management.automation.runspaces](https://docs.microsoft.com/en-us/dotnet/api/system.management.automation.runspaces)

#### Tags

- Automation
- .NET
- Runspace
- SDK

#### Properties

- [Documentation](https://docs.microsoft.com/en-us/powershell/scripting/developer/hosting/creating-runspaces)
- [SDK](https://www.nuget.org/packages/System.Management.Automation/)
- [Examples](https://github.com/PowerShell/PowerShell/tree/master/test/hosting)
- [Postman Collection](collections/powershell.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/powershell.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### PowerShell Remoting API

APIs and protocols for remote PowerShell execution over WS-Management (WinRM) and SSH. Enables one-to-one and one-to-many remote command and session management.

- **Human URL:** [https://docs.microsoft.com/en-us/powershell/scripting/learn/remoting/running-remote-commands](https://docs.microsoft.com/en-us/powershell/scripting/learn/remoting/running-remote-commands)

#### Tags

- Remoting
- SSH
- WinRM
- WS-Management

#### Properties

- [Documentation](https://docs.microsoft.com/en-us/powershell/scripting/learn/remoting/powershell-remoting-faq)
- [Protocol Specification](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-psrp/)
- [Postman Collection](collections/powershell.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/powershell.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Website](https://microsoft.com/powershell)
- [Git Hub](https://github.com/PowerShell/PowerShell)
- [Documentation](https://docs.microsoft.com/en-us/powershell/)
- [Blog](https://devblogs.microsoft.com/powershell/)
- [Community](https://github.com/PowerShell/PowerShell/blob/master/docs/community/README.md)
- [Getting Started](https://docs.microsoft.com/en-us/powershell/scripting/learn/ps101/01-getting-started)
- [License](https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt)
- [Releases](https://github.com/PowerShell/PowerShell/releases)
- [Roadmap](https://github.com/PowerShell/PowerShell/projects)
- [Security](https://github.com/PowerShell/PowerShell/security/policy)
- [Contributing](https://github.com/PowerShell/PowerShell/blob/master/.github/CONTRIBUTING.md)
- [Integrations](https://www.microsoft.com/en-us/marketplace)

## Maintainers

**FN:** Microsoft
**Email:** powershell@microsoft.com
**URL:** https://github.com/PowerShell

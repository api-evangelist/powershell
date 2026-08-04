# PowerShell (powershell)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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

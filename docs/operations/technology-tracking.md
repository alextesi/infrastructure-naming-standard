# Technology Tracking Separation

This document explains why technology tracking must remain separate from the infrastructure naming standard and suggests practical ways to implement it.

## Purpose

The naming standard identifies a resource by stable operational meaning.

Technology tracking identifies changing technical attributes of that resource over time.

These are different concerns and should not be merged into the same identifier.

## Why Separation Is Required

### 1. Hostnames must remain stable

A hostname should survive rebuilds, migrations, and platform changes with minimal change.

If technology details are embedded in the hostname, the hostname becomes unstable whenever any of these change:

- operating system
- operating system release
- database engine
- software version
- hypervisor platform
- Kubernetes version

Example of bad practice:

```text
fra-prd-win22-db-01
zrh-prd-ubu24-api-01
```

Those names become misleading as soon as the system is upgraded or rebuilt.

### 2. Technology data changes faster than logical identity

The logical identity of a system might remain the same for years.

Its technology profile can change many times:

- Windows Server 2022 to Windows Server 2025
- Ubuntu 22.04 to Ubuntu 24.04
- PostgreSQL 15 to PostgreSQL 16
- Kubernetes 1.29 to 1.31

These changes should update inventory records, not naming rules.

### 3. Ambiguity increases when meanings are mixed

Embedding technical metadata in hostnames creates ambiguity.

Example:

```text
zrh-prd-db-01-g24
```

`g24` could be interpreted as:

- generation 24
- year 2024
- Ubuntu 24.04
- Windows Server 2024 or 2025-era naming shortcut

That ambiguity weakens automation and operations.

### 4. Naming and inventory have different consumers

The naming standard is primarily used by:

- operators
- automation
- monitoring
- DNS
- architecture diagrams

Technology tracking is primarily used by:

- asset management
- configuration management
- lifecycle management
- patching and compliance
- vulnerability management
- audit and reporting

### 5. Structured inventory is queryable in ways hostnames are not

A proper inventory can answer questions such as:

- which servers still run Ubuntu 22.04?
- which nodes are on Kubernetes 1.29?
- which Windows devices still expose legacy software?
- which database instances run PostgreSQL 15?

Encoding such data in hostnames makes those questions harder to answer correctly and consistently.

## What Belongs In The Naming Standard

The naming standard should capture stable identity such as:

- location
- security zone
- environment
- architectural tier
- service domain
- role
- instance number
- rebuild generation

See [Field Definitions](../standard/fields.md) for the canonical model.

## What Belongs In Technology Tracking

Technology tracking should capture mutable attributes such as:

- operating system family
- operating system version
- kernel version
- database engine and version
- container runtime
- Kubernetes version
- installed software inventory
- hardware model
- serial number
- CPU and memory profile
- patch level
- lifecycle status
- end-of-support dates

Example record:

```text
Hostname: zrh-prd-data-db-01-g2
Role: Database
Platform family: Linux
OS: Ubuntu 24.04
Database engine: PostgreSQL
Database version: 16
Kernel: 6.8
Owner: Platform Team
Lifecycle state: Active
```

## Recommended Architecture

Use the naming standard as the stable primary identifier and store technology details in one or more dedicated systems.

A practical model is:

1. Hostname as canonical operational identifier.
2. CMDB or asset inventory as the source of mutable technology metadata.
3. Automation or discovery tools to populate and refresh that metadata.
4. Reporting and compliance tooling to query the inventory layer.

## Suggested Implementation Options

The right tooling depends on scope. The examples below are examples, not mandatory standards.

### Option 1. Lightweight inventory with scripts

Suitable for:

- small teams
- lab environments
- early-stage standard adoption

Approach:

- collect host facts with shell or PowerShell scripts
- export normalized JSON or CSV
- publish into Git, object storage, or a lightweight database
- keep hostname as the joining key

Useful collected fields:

- hostname
- location
- environment
- role
- OS name
- OS version
- kernel version
- installed packages
- serial number
- CPU
- memory

### Option 2. CMDB or IT asset inventory

Suitable for:

- mixed server and endpoint environments
- audit-heavy environments
- organizations that need ownership and lifecycle workflows

Examples:

- NetBox for infrastructure inventory and platform modeling
- GLPI for IT asset and service management
- Snipe-IT for asset management with API-driven integrations

### Option 3. Endpoint and device management platforms

Suitable for:

- workstation fleets
- corporate-managed Windows and mobile devices

Example:

- Microsoft Intune for managed device hardware and discovered application inventory

### Option 4. Automation-driven technology tracking

Suitable for:

- server fleets already managed by automation
- environments with strong configuration management discipline

Approach:

- gather facts from Ansible, PowerShell, or shell scripts
- normalize the data
- push results into a CMDB, inventory platform, or reporting dataset

## Suggested Scripts

These are implementation patterns, not required repository artifacts.

### Bash or shell fact collection

Use on Linux systems to collect:

- `/etc/os-release`
- kernel version
- package inventory
- hostname
- CPU and memory

Output format recommendation:

- JSON for machine ingestion
- CSV only for small manual workflows

### PowerShell fact collection

Use on Windows systems to collect:

- computer name
- OS caption and version
- installed features
- installed software
- BIOS or serial details
- CPU and memory

### Scheduled inventory export

Run a scheduled job that:

1. collects host facts
2. validates required fields
3. maps them to the canonical hostname
4. pushes the result to the inventory system

### Agent-based inventory

Where higher coverage is required, use an agent or management platform that can continuously report device metadata rather than relying only on ad hoc scripts.

## Data Quality Rules

- Do not use technology attributes as substitutes for hostname fields.
- Keep one authoritative record per hostname.
- Track collection timestamp for every inventory update.
- Distinguish discovered data from manually curated business metadata.
- Record ownership and lifecycle status explicitly.
- Define which system is authoritative for each field.

## Recommended Minimum Dataset

At minimum, track:

- hostname
- role
- location
- environment
- owner
- OS family
- OS version
- primary application or engine
- lifecycle status
- last inventory update timestamp

## Tooling Notes

The following examples are commonly relevant for technology tracking:

- NetBox models devices, roles, platforms, and physical or virtual infrastructure objects.
- GLPI supports asset management and automatic inventory workflows.
- Snipe-IT provides asset tracking and a REST API suitable for custom integrations.
- Microsoft Intune exposes hardware details and discovered application data for managed devices.

Inference from sources:

NetBox is strongest when the inventory problem is infrastructure-centric, while GLPI, Snipe-IT, and Intune are more directly aligned with asset and endpoint inventory use cases.

## Related Pages

- [Operational Practices](./best-practices.md)
- [Field Definitions](../standard/fields.md)
- [Governance](../governance.md)
- [Contributing](../../CONTRIBUTING.md)

## External References

- [NetBox Device Model Documentation](https://netbox.readthedocs.io/en/stable/models/dcim/device/)
- [NetBox Platform Documentation](https://netbox.readthedocs.io/en/stable/models/dcim/platform/)
- [GLPI Asset Documentation](https://help.glpi-project.org/documentation/modules/assets)
- [GLPI Project](https://glpi-project.org/)
- [Snipe-IT](https://snipeitapp.com/)
- [Microsoft Intune Device Inventory](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/device-inventory)
- [Microsoft Intune Discovered Apps](https://learn.microsoft.com/en-us/mem/intune/apps/app-discovered-apps)

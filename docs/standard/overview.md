# Standard Overview

## Purpose

This document defines the standard naming convention for infrastructure resources.

The objective is to ensure:

- consistent and predictable system naming
- infrastructure clarity for operators
- compatibility with automation and monitoring
- stability across system upgrades and rebuilds
- scalability as the infrastructure grows

For detailed field descriptions, continue to [Field Definitions](./fields.md).

## Design Principles

### Role-based identity

Hostnames represent the logical function of a system, not the implementation technology.

Correct:

```text
zrh-lan-prd-data-db-01-g1
```

Incorrect:

```text
zrh-prd-mysql01
```

### Technology independence

Hostnames must not contain:

- operating system names
- operating system versions
- database engines
- software versions
- application versions

These attributes belong in:

- CMDB
- configuration management
- monitoring systems
- asset inventory

### Stability over time

Hostnames must remain meaningful even if:

- operating systems change
- software platforms change
- systems are rebuilt
- infrastructure migrates to cloud environments

### Automation compatibility

Hostnames must be:

- machine readable
- easy to parse
- predictable for scripts and automation tools
- compatible with monitoring systems

## Full Naming Model

The extended naming model is:

```text
<location>-<zone>-<environment>-<tier>-<domain>-<role>-<instance>-g<generation>
```

Example:

```text
zrh-dmz-prd-edge-web-k8s-01-g1
```

Continue with [Field Definitions](./fields.md) for the meaning of each element, or jump to [Patterns and Resource Naming](./patterns.md) for concrete usage patterns.

## Version

- Version: `1.0`
- Status: `Active`
- Owner: `IT Architecture / DevOps`
- Scope: `All Infrastructure Systems`

## Related Pages

- [Documentation Hub](../index.md)
- [Field Definitions](./fields.md)
- [Patterns and Resource Naming](./patterns.md)
- [Governance](../governance.md)

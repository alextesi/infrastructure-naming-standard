# infrastructure-naming-standard

Standardized infrastructure naming convention for servers, Kubernetes, network devices and cloud resources.

## Overview

This repository contains a modular naming convention standard for infrastructure resources.

It is designed to be:

- technology-independent
- stable across rebuilds and migrations
- easy to parse for automation
- scalable from small environments to enterprise platforms

## Start Here

- [Documentation Hub](./docs/index.md)
- [Standard Overview](./docs/standard/overview.md)
- [Field Definitions](./docs/standard/fields.md)
- [Location Code Catalog](./docs/reference/location-codes.md)
- [Patterns and Resource Naming](./docs/standard/patterns.md)
- [Operational Practices](./docs/operations/best-practices.md)
- [Technology Tracking Separation](./docs/operations/technology-tracking.md)
- [Examples](./docs/reference/examples.md)
- [Role Code Catalog](./docs/reference/role-codes.md)
- [Templates](./docs/templates/index.md)
- [Governance](./docs/governance.md)
- [Contributing](./CONTRIBUTING.md)

## Repository Structure

```text
.
├── README.md
├── CONTRIBUTING.md
└── docs/
    ├── index.md
    ├── governance.md
    ├── operations/
    │   └── best-practices.md
    ├── reference/
    │   ├── examples.md
    │   ├── location-codes.md
    │   └── role-codes.md
    ├── standard/
    │   ├── fields.md
    │   ├── overview.md
    │   └── patterns.md
    └── templates/
        ├── index.md
        ├── appendix-template.md
        └── standard-template.md
```

## Scope

This standard applies to:

- physical servers
- virtual machines
- Kubernetes nodes and clusters
- network devices
- cloud infrastructure resources
- storage systems
- platform infrastructure

## Navigation

If you are reading this repository on GitHub:

1. Start from [Documentation Hub](./docs/index.md).
2. Read [Standard Overview](./docs/standard/overview.md) to understand the model.
3. Use [Field Definitions](./docs/standard/fields.md), [Location Code Catalog](./docs/reference/location-codes.md), and [Role Code Catalog](./docs/reference/role-codes.md) as daily reference material.
4. Use [Contributing](./CONTRIBUTING.md) and [Templates](./docs/templates/index.md) when extending the standard.

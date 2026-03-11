# Operational Practices

This page captures the operational rules that make the naming standard usable over time.

## DNS Best Practices

Applications should never directly reference infrastructure hostnames.

Use DNS service aliases instead.

Example service alias:

```text
db.internal.company
```

Points to:

```text
zrh-prd-data-db-01-g2
```

Benefits:

- transparent infrastructure migrations
- service failover flexibility
- reduced operational risk

## Upgrade and Migration Strategy

Infrastructure upgrades should follow the generation model.

Generation does not represent the year of deployment or the operating system version.

For example:

- `g2` does not mean `2026`
- `g22` should not mean Windows Server 2022
- `g24` should not mean Ubuntu 24.04

Those technology details belong in inventory records, not in hostnames.

Example process:

1. Deploy a new server.
2. Assign the next generation hostname.
3. Install the updated OS and software.
4. Migrate services and data.
5. Switch the DNS service alias.
6. Decommission the previous generation.

Example:

```text
zrh-prd-db-01-g1
zrh-prd-db-01-g2
```

## Technology Tracking

Technology attributes must be tracked in inventory systems, not embedded in hostnames.

Use a dedicated technology tracking process and data store for this purpose.

For rationale, implementation guidance, and example tooling, see [Technology Tracking Separation](./technology-tracking.md).

## Recommended Practices

- Keep codes short, stable, and unambiguous.
- Reuse approved role codes from the [Role Code Catalog](../reference/role-codes.md).
- Avoid encoding temporary project names in hostnames.
- Prefer DNS aliases for service access.
- Review exceptions through architecture or DevOps governance.

## Related Pages

- [Standard Overview](../standard/overview.md)
- [Patterns and Resource Naming](../standard/patterns.md)
- [Technology Tracking Separation](./technology-tracking.md)
- [Governance](../governance.md)

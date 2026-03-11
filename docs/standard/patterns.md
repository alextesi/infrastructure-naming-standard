# Patterns and Resource Naming

This page describes how the naming model is applied across infrastructure types.

## Simplified Naming Model

Smaller infrastructures may use a simplified structure:

```text
<location>-<environment>-<role>-<instance>-g<generation>
```

Example:

```text
zrh-prd-db-01-g1
```

This remains compatible with the extended model described in [Standard Overview](./overview.md).

## Network Device Naming

Network infrastructure should follow the same standard.

Example:

```text
zrh-lan-prd-core-fw-01-g1
```

Recommended network roles are documented in the [Role Code Catalog](../reference/role-codes.md).

Additional examples:

```text
zrh-lan-prd-core-sw-01-g1
zrh-lan-prd-core-sw-02-g1
```

## Kubernetes Naming

### Cluster naming

Recommended format:

```text
<location>-<zone>-<environment>-<domain>-k8s
```

Examples:

```text
zrh-dmz-prd-web-k8s
zrh-lan-prd-api-k8s
```

### Node naming

Nodes follow the infrastructure naming standard.

Examples:

```text
zrh-dmz-prd-edge-web-k8s-01-g1
zrh-dmz-prd-edge-web-k8s-02-g1
zrh-dmz-prd-edge-web-k8s-03-g1
```

### Namespace naming

Namespaces represent applications or services.

Recommended format:

```text
<application>-<environment>
```

Examples:

```text
auth-prd
wms-prd
grafana-prd
```

## Cloud Resource Naming

Cloud resources should follow the same philosophy, with practical adaptation when the provider resource type has its own constraints.

### Virtual machines

Examples:

```text
fra-prd-api-01-g1
fra-prd-web-01-g1
```

### Managed databases

Example:

```text
fra-prd-data-db-01
```

### Storage resources

Examples:

```text
fra-prd-storage-backups
fra-prd-storage-logs
```

## Hostname Length

Keep hostnames as short as practical and preferably well below the DNS single-label limit.

Hard technical limit:

```text
<= 63 characters per DNS label
```

Operational recommendation:

```text
prefer concise names, typically below 30 to 35 characters when possible
```

This improves compatibility and readability across:

- DNS
- Linux
- Windows
- monitoring systems

## Related Pages

- [Standard Overview](./overview.md)
- [Field Definitions](./fields.md)
- [Operational Practices](../operations/best-practices.md)
- [Examples](../reference/examples.md)

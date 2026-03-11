# Field Definitions

This page defines each field used in the extended naming model described in [Standard Overview](./overview.md).

## Naming Structure

```text
<location>-<zone>-<environment>-<tier>-<domain>-<role>-<instance>-g<generation>
```

## 1. Location

Identifies the physical or logical hosting location.

| Code | Location |
| ---- | -------- |
| zrh | Zurich |
| fra | Frankfurt |
| nbg | Nuremberg |
| hel | Helsinki |
| gvl | Gravelines |
| par | Paris |
| aws | AWS region |
| azr | Azure region |
| lab | Internal lab |

Example:

```text
zrh-prd-db-01-g1
```

Additional location examples:

```text
fra-prd-api-01-g1
nbg-prd-web-01-g1
gvl-prd-db-01-g1
```

## 2. Security Zone

Identifies the network security zone.

| Code | Description |
| ---- | ----------- |
| lan | Trusted internal network |
| dmz | Perimeter or exposed network |
| mgmt | Management network |
| sec | Security tooling network |
| pub | Public internet zone |

Example:

```text
zrh-dmz-prd-web-k8s-01-g1
```

## 3. Environment

Defines the operational lifecycle stage.

| Code | Environment |
| ---- | ----------- |
| prd | Production |
| stg | Staging |
| tst | Testing |
| dev | Development |
| lab | Experimental |
| dr | Disaster recovery |

Example:

```text
zrh-lan-dev-api-01-g1
```

## 4. Infrastructure Tier

Defines the architectural layer of the system.

| Tier | Description |
| ---- | ----------- |
| edge | Internet-facing layer |
| platform | Platform services |
| data | Databases and data systems |
| core | Core infrastructure |
| ops | Operations and observability |

Example:

```text
zrh-dmz-prd-edge-web-k8s-01-g1
```

## 5. Service Domain

Identifies the platform or service group.

| Domain | Meaning |
| ------ | ------- |
| core | Core infrastructure |
| auth | Authentication platform |
| web | Web platform |
| api | API platform |
| data | Data services |
| ops | Monitoring and operations |
| sec | Security tooling |
| ai | AI or ML platform |
| int | Integration platform |

Example:

```text
zrh-lan-prd-data-db-01-g1
```

## 6. Role

Defines the technical function of the system.

See the full [Role Code Catalog](../reference/role-codes.md) for the recommended codes.

Example:

```text
zrh-lan-prd-core-dc-01-g1
```

## 7. Instance

Sequential number identifying instances of the same role.

Format:

```text
01
02
03
```

Example:

```text
zrh-prd-web-02-g1
```

## 8. Generation

Identifies the rebuild cycle of a logical system instance.

The generation field is a lifecycle marker, not a technology marker.

It should answer this question:

`How many times has this logical server or node been replaced or rebuilt over time?`

Format:

```text
g1
g2
g3
```

Interpretation:

- `g1` = first deployed incarnation of the logical system
- `g2` = second incarnation after rebuild or replacement
- `g3` = third incarnation after another rebuild or replacement

Generation should change when the logical system is replaced with a new underlying instance, for example during:

- OS refresh
- hardware replacement
- VM recreation
- migration to a new cluster node
- full rebuild during platform modernization

Generation should not be used to encode:

- calendar year such as `25` or `26`
- Windows Server version such as `19`, `22`, or `25`
- Ubuntu release such as `18`, `20`, `22`, or `24`
- product version
- patch level

Incorrect examples:

```text
zrh-prd-db-01-g25
zrh-prd-db-01-g22
```

In those cases, `25` or `22` would be ambiguous because they could mean year, OS release, or something else.

Correct approach:

- keep `generation` as `g1`, `g2`, `g3`, and so on
- track year and OS version in inventory, CMDB, or configuration management

Example lifecycle:

| Hostname | Description |
| -------- | ----------- |
| zrh-prd-db-01-g1 | Initial deployment |
| zrh-prd-db-01-g2 | Rebuilt during an OS refresh |
| zrh-prd-db-01-g3 | Rebuilt again on new infrastructure |

Generation enables safe migrations and infrastructure refresh cycles.

## Related Pages

- [Standard Overview](./overview.md)
- [Patterns and Resource Naming](./patterns.md)
- [Role Code Catalog](../reference/role-codes.md)
- [Examples](../reference/examples.md)

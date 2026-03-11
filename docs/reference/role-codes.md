# Role Code Catalog

This catalog provides an extended baseline set of approved role codes for common infrastructure components.

Teams should prefer these codes instead of inventing local variants.

## Infrastructure Roles

| Role | Description |
| ---- | ----------- |
| dc | Domain controller |
| dns | DNS server |
| ntp | Time server |
| pki | Certificate authority |
| vault | Secret management |
| dhcp | DHCP server |
| bastion | Bastion host |
| proxy | Infrastructure proxy |
| jump | Jump host |
| print | Print service |
| lic | License server |
| repo | Package or artifact repository |
| caa | Certificate automation agent |

## Platform Roles

| Role | Description |
| ---- | ----------- |
| k8s | Kubernetes node |
| vmh | Hypervisor |
| stor | Storage node |
| bkp | Backup server |
| registry | Container registry |
| cicd | CI or CD runner platform |
| tfm | Terraform or infrastructure management node |
| ans | Configuration automation node |
| img | Image build service |
| sched | Job scheduler |
| broker | Platform broker |
| gateway | Platform gateway |

## Application Roles

| Role | Description |
| ---- | ----------- |
| web | Web server |
| api | API server |
| app | Application server |
| db | Relational database |
| cache | Redis or cache service |
| mq | Messaging platform |
| search | Search engine |
| etl | Data pipeline or ETL service |
| batch | Batch processing service |
| worker | Background worker |
| stream | Stream processing service |
| ingest | Data ingestion service |
| report | Reporting service |
| portal | User portal |
| files | File service |
| cms | Content management service |
| authn | Authentication service |
| authz | Authorization service |
| webhook | Webhook receiver |
| engine | Business logic engine |
| git | Source control service |

## Observability Roles

| Role | Description |
| ---- | ----------- |
| mon | Monitoring |
| log | Logging |
| trace | Distributed tracing |
| apm | Application performance monitoring |
| siem | Security event monitoring |
| alert | Alerting service |
| metrics | Metrics storage or query service |
| audit | Audit log service |

## Network Roles

| Role | Description |
| ---- | ----------- |
| fw | Firewall |
| rt | Router |
| sw | Switch |
| lb | Load balancer |
| vpn | VPN gateway |
| wifi | Wireless controller |
| ap | Access point |
| ids | Intrusion detection system |
| ips | Intrusion prevention system |
| waf | Web application firewall |
| nat | NAT gateway |
| sdn | SDN controller |
| adc | Application delivery controller |
| gw | Generic network gateway |
| mux | Network multiplexer |

## Storage and Data Roles

| Role | Description |
| ---- | ----------- |
| nas | Network-attached storage |
| san | Storage area network service |
| obj | Object storage service |
| backup | Backup storage target |
| archive | Archive storage service |
| lake | Data lake platform |
| wh | Data warehouse platform |
| catalog | Data catalog service |

## Security Roles

| Role | Description |
| ---- | ----------- |
| edr | Endpoint detection and response |
| iam | Identity and access management |
| pam | Privileged access management |
| scanner | Vulnerability scanning service |
| keymgmt | Key management service |
| secrets | Secrets management service |
| policy | Policy enforcement service |

## Usage Examples

```text
zrh-lan-prd-core-dhcp-01-g1
zrh-lan-prd-platform-registry-01-g1
zrh-dmz-prd-edge-waf-01-g1
fra-lan-prd-data-lake-01-g1
zrh-sec-prd-sec-siem-01-g1
```

## Usage Guidance

- Keep role codes short and descriptive.
- Reuse an existing code when the function is equivalent.
- Add new codes through formal review to avoid duplication.
- Document new codes in this catalog before operational use.
- Propose new codes through [Contributing](../../CONTRIBUTING.md).

## Related Pages

- [Field Definitions](../standard/fields.md)
- [Examples](./examples.md)
- [Governance](../governance.md)
- [Contributing](../../CONTRIBUTING.md)

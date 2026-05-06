# Network Configuration Manager

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An AI-native, open-source platform for network device configuration versioning, compliance, and change management across multi-vendor estates.

Network Configuration Manager (NCM) is a candidate project to build a modern, standards-based tool for backing up, versioning, validating, and auditing network device configurations. It targets network engineers, NOC teams, MSPs, and regulated enterprises who need multi-vendor configuration control without legacy enterprise pricing or dated tooling.

---

## Why Network Configuration Manager?

- Incumbent enterprise suites (SolarWinds NCM, NetBrain, Cisco NSO) carry legacy node-based pricing that can exceed $50,000/yr and complex onboarding that excludes smaller teams.
- SolarWinds' acquisition history and 2020 security incident have raised concerns about long-term direction, while Infoblox NetMRI is a sunset product (last order April 2025, EOL April 2027).
- Open-source incumbents fill different gaps but none cover the full lifecycle: RANCID is CLI-only with a steep learning curve, Oxidized lacks built-in compliance and approval workflow, rConfig's UI is dated and short on analytics, and Batfish is validation-only.
- ManageEngine NCM positions ~70% cheaper than SolarWinds but still proprietary with a dated UI and limited advanced automation.
- No incumbent combines modern NETCONF/YANG and OpenConfig support, Git-native workflows, AI-driven anomaly detection, and compliance automation in a single permissively licensed package.

---

## Key Features

### Configuration Backup and Versioning

- Multi-vendor configuration backup across 50+ device types
- Configuration versioning with rollback to any prior version
- Git integration for version control and audit trails
- Scheduled and event-driven backup workflows

### Drift Detection and Change Management

- Real-time drift detection against baseline configurations
- Configuration labeling (baseline, stable, custom) for flexible baseline management
- Change audit logs with user, timestamp, and modification type
- Real-time change notifications via email, SNMP traps, Syslog, and ticketing integrations
- Approval workflow for proposed configuration changes

### Compliance and Validation

- Policy-based compliance checking aligned with SOX, HIPAA, PCI DSS, and NIST SP 800-53
- CIS Benchmark templates for routers, switches, and firewalls
- Pre-deployment configuration validation in the spirit of Batfish (forwarding loops, BGP/OSPF sessions, ACL analysis, firewall policy, IPsec)
- Continuous compliance scoring dashboard

### Automation and Integration

- REST API for programmatic automation
- NETCONF/YANG and RESTCONF support for standards-based device interaction
- OpenConfig data model alignment for vendor-neutral configuration
- CI/CD pipeline integration for GitOps-style workflows
- Multi-tenant support for MSPs

---

## AI-Native Advantage

Unlike incumbent NCM suites that rely on hand-authored rules, this project applies AI across the configuration lifecycle: anomaly detection in config diffs to flag security-risky or non-compliant changes without manual rule writing, a natural-language query interface over configuration history (for example, "show me every device where access-list 101 changed in the last 90 days"), AI-assisted remediation that generates corrective config snippets when drift is detected, and predictive impact analysis that models the downstream effects of a proposed change across interdependent device groups before deployment. LLM-powered compliance authoring translates plain-English security policies into vendor-specific configuration templates and audit rules.

---

## Tech Stack & Deployment

Expected deployment modes include self-hosted (on-premises or private cloud) and containerized deployment, following the Docker-based pattern used by Batfish. Device interaction is built on NETCONF/YANG (RFC 6241, RFC 6020), RESTCONF (RFC 8040), and OpenConfig data models, with fallbacks to SSH, Telnet, and SNMP for legacy devices. Integration is API-first with a REST API and Git-backed configuration history, enabling GitOps and CI/CD workflows. A Python API similar to pybatfish is a natural fit for custom queries and validation tests.

---

## Market Context

The broader network management software market is valued at several billion dollars globally, with the NCM sub-segment estimated in the low hundreds of millions and growing alongside network automation and SD-WAN adoption. Incumbent pricing ranges from free open-source (RANCID, Oxidized, rConfig Core) through per-node commercial licences ($50–$200/node/yr) to enterprise bundles exceeding $50,000/yr; SolarWinds NCM lists at roughly $3,000–$15,000/yr per node-based deployment, and ManageEngine prices ~70% lower. Primary buyers are network engineers and NOC teams in mid-to-large enterprises, MSPs managing multi-tenant device estates, and regulated industries (finance, healthcare, utilities) with audit requirements.

---

## Project Status

> This project is in the **research and specification phase**.  
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.

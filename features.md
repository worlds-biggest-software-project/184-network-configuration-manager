# Network Configuration Manager — Feature & Functionality Survey

> Candidate #184 · Researched: 2026-05-03

## Solutions Analysed

| Tool | Type | Licence / Model | URL |
|------|------|-----------------|-----|
| SolarWinds NCM | Commercial | Proprietary / Node-based | https://www.solarwinds.com/network-configuration-manager |
| ManageEngine NCM | Commercial | Proprietary / Subscription | https://www.manageengine.com/network-configuration-manager/ |
| NetBrain | Commercial | Proprietary / Enterprise | https://www.netbrain.com/ |
| Infoblox NetMRI | Commercial (Legacy) | Proprietary / Enterprise | https://www.infoblox.com/products/netmri/ |
| Cisco NSO | Commercial | Proprietary / Enterprise | https://www.cisco.com/site/us/en/products/networking/software/crosswork-network-services-orchestrator |
| Oxidized | Open-source | MIT | https://github.com/ytti/oxidized |
| rConfig | Open-source + Commercial | Free (Core) / Paid cloud | https://www.rconfig.com/ |
| RANCID | Open-source | Custom | https://www.shrubbery.net/rancid/ |
| Batfish | Open-source | Apache 2.0 | https://batfish.org/ |
| Unimus | Commercial | Proprietary / Subscription | https://unimus.net/ |

## Feature Analysis by Solution

### SolarWinds NCM

**Core features**
- Multi-vendor device support (Cisco, Juniper, HP, Dell, Palo Alto, Brocade, ASA, Nexus)
- Automated configuration backup and change tracking
- Config-to-config and baseline-to-config diff views
- Change approval workflow and request management
- Firmware upgrade automation (up to 100 concurrent upgrades)
- Compliance policy reports (SOX, HIPAA, CISP, Cisco Security)
- National Vulnerability Database integration for vulnerability identification
- Cloud or on-premises deployment (Azure SQL, Amazon RDS)

**Differentiating features**
- Mature, enterprise-grade platform with extensive hardware support
- Version 2024.2.1 with EOL dates extending to 2026
- Bulk change deployment with multi-grouping
- Deep compliance reporting with regulatory templates
- Firmware upgrade orchestration
- Legacy integration with Orion suite

**UX patterns**
- Web-based dashboard for configuration management
- Approval workflow UI for change management
- Policy-based compliance reporting
- Remote change execution without device login

**Integration points**
- Network device APIs across 10+ vendors
- Orion suite integration
- Change approval workflow APIs
- Compliance reporting export

**Known gaps**
- High cost (legacy pricing model)
- Complex setup and onboarding
- Acquisition history raises concerns about future direction
- Less suitable for small teams or cloud-native environments

**Licence / IP notes**
- Proprietary SaaS model; no open-source components
- Node-based licensing
- Enterprise contracts

---

### ManageEngine NCM

**Core features**
- Real-time configuration drift detection and baseline comparison
- Automatic configuration labeling (baseline, stable, custom)
- Automatic rollback to baseline or previous versions
- Real-time change notifications (email, SNMP traps, Syslogs, tickets)
- Detailed audit logs with user, timestamp, and modification type
- Multi-vendor device support
- Policy-based compliance management
- Cost-effective alternative to SolarWinds (~70% lower pricing)

**Differentiating features**
- Real-time drift detection with automatic rollback
- Cost-transparent pricing (significantly cheaper than SolarWinds)
- Configuration labeling for flexible baseline management
- Continuous monitoring and comparison against established baselines
- Prompt notifications via multiple channels
- Detailed audit trails for compliance

**UX patterns**
- Dashboard-driven drift monitoring
- Baseline configuration management with labeling
- Real-time notification interface
- Audit log review for compliance

**Integration points**
- Multi-vendor device APIs
- Email and SNMP notification gateways
- Ticketing system integration
- Audit log export APIs

**Known gaps**
- UI feels dated compared to modern alternatives
- Smaller community than SolarWinds
- Limited advanced automation compared to NetBrain
- Less suitable for large-scale environments

**Licence / IP notes**
- Proprietary SaaS model; no open-source components
- Transparent subscription pricing
- No identified patent encumbrances

---

### NetBrain

**Core features**
- Dynamic network mapping ("Digital Twin" of infrastructure)
- AI-driven network troubleshooting and diagnostics
- Intent-based automation without coding
- No-code network automation platform for Day 2 operations
- Automated diagnostic recommendations based on historical data
- Real-time tests and traffic flow analysis
- NetBrain R12 (2025): Geo-location dashboards and enhanced observability
- Proactive change management with AI Bot

**Differentiating features**
- Advanced AI Bot for troubleshooting with reduced MTTR
- Digital Twin dynamic network mapping
- Intent-based automation (no-code platform)
- Enhanced Geo-Location Dashboards (R12 2025)
- AI-powered diagnostic interpretation
- Network visualization with real-time data overlays

**UX patterns**
- Visual network topology with drill-down capabilities
- AI Bot recommendations with human-readable format
- Intent-based workflow definition (no code)
- Color-coded Intents on network maps
- No-code automation builder

**Integration points**
- Device APIs for topology discovery
- Cisco ACI integration
- Real-time monitoring APIs
- Automation API for workflow execution

**Known gaps**
- High setup cost and complexity
- Enterprise-focused (less suitable for SMBs)
- Learning curve for new platforms
- Requires significant onboarding

**Licence / IP notes**
- Proprietary enterprise SaaS
- Custom licensing agreements
- No identified patent encumbrances

---

### Infoblox NetMRI (Legacy Product)

**Core features**
- Multi-vendor network infrastructure tracking
- Automatic configuration policy enforcement
- Compliance auditing (PCI, HIPAA, DISA, STIGs)
- Out-of-the-box compliance policies based on industry best practices
- Historical tracking of network constructs (routes, VLANs, virtual routing)
- Device provisioning automation
- Security operations automation

**Differentiating features**
- Comprehensive compliance policy library
- Automatic compliance enforcement without custom scripting
- Multi-vendor topology and construct tracking

**Important Note (2025)**
- **Last Order Date: April 30, 2025**
- **End of Support: April 30, 2027**
- Infoblox recommends migration to IP Fabric or similar alternatives
- NetMRI is considered legacy/sunset product

**UX patterns**
- Policy-based compliance checking
- Automated enforcement workflows
- Topology visualization

**Integration points**
- Multi-vendor device APIs
- Compliance reporting export

**Known gaps**
- Sunset product with limited future development
- No new feature development expected
- Replacement products must be evaluated

**Licence / IP notes**
- Proprietary enterprise licensing
- Product sunset in 2027

---

### Cisco NSO

**Core features**
- Model-based programmatic configuration management
- Network Element Drivers (NEDs) for 1000+ third-party and Cisco devices
- Device and service lifecycle management
- Single source of truth configuration data store
- Fast, scalable, highly available configuration database
- Real-time device state capture and synchronization
- Service orchestration across multi-vendor networks
- Cloud-native support (2025 releases: NSO SMI 2025.03, 2025.04, 2026.01)

**Differentiating features**
- Support for 1000+ devices via NEDs
- Model-based configuration abstraction
- Single source of truth with 99.99% consistency
- Deep Cisco ecosystem integration
- Cloud-native containerized deployment (2025)
- Full lifecycle service management
- Corrections for inaccurate network data (claims 70% accuracy improvement)

**UX patterns**
- Programmatic API-first design
- Model-driven configuration
- Service abstraction layer
- Cloud-native deployment

**Integration points**
- 1000+ device NEDs (Cisco and third-party)
- Service management APIs
- Cloud-native container orchestration
- Multi-vendor support via NEDs

**Known gaps**
- Heavy Cisco ecosystem lock-in
- Complex configuration and learning curve
- Steep licensing costs
- Primarily designed for service providers
- Less suitable for enterprise-only networks

**Licence / IP notes**
- Proprietary enterprise SaaS
- Custom licensing agreements
- Deep vendor lock-in to Cisco ecosystem

---

### Oxidized

**Core features**
- Configuration backup tool (RANCID successor)
- Support for 130+ operating system types
- Native Git integration with automatic commits on changes
- REST API for programmatic access
- Web interface for visualization
- Node fetch, reload, and version querying via REST
- Configuration diff viewing
- Extensible plugin architecture

**Differentiating features**
- Modern RANCID replacement with better UX
- REST API native support (RANCID lacks this)
- Git-based version control (natural fit for DevOps workflows)
- Lightweight and actively maintained
- Developer-friendly design
- Sub-second API response times for large device inventories

**UX patterns**
- REST API for programmatic access
- Git-based configuration history
- Web UI for browsing configurations
- Declarative configuration management

**Integration points**
- Git for version control and audit trails
- REST API for automation
- Web interface
- Plugin system for custom outputs
- SNMP, SSH, Netconf protocols for device access

**Known gaps**
- No built-in compliance checking
- Limited advanced analytics
- Requires Git familiarity for teams
- No workflow approval system
- Limited graphical configuration management

**Licence / IP notes**
- MIT licence (fully open-source)
- No vendor lock-in
- Community-driven development

---

### rConfig

**Core features**
- Open-source scheduled configuration backup across multiple vendors
- Backup automation and version control
- Multi-vendor device support
- Free core version (rConfig V8 Core)
- Commercial cloud hosting option
- Web-based interface
- Configuration comparison and rollback
- Backup scheduling

**Differentiating features**
- Easy deployment for small-to-medium businesses
- Free core version with commercial cloud option
- Practical approach to backup automation
- Multi-vendor flexibility

**UX patterns**
- Web-based configuration UI
- Scheduled backup workflows
- Simple device group management
- Configuration comparison interface

**Integration points**
- Multi-vendor device APIs
- Cloud hosting option
- Backup scheduling APIs

**Known gaps**
- Dated UI compared to modern tools
- Limited analytics and reporting
- Lacks compliance features
- No approval workflow system
- Smaller ecosystem than commercial tools
- Limited support for newer device types

**Licence / IP notes**
- Open-source core with commercial cloud offering
- Proprietary cloud SaaS model
- Permissive licensing

---

### RANCID

**Core features**
- Veteran open-source configuration backup tool
- VCS integration (CVS, SVN, Git)
- Multi-vendor device support
- CLI-based configuration management
- Battle-tested with decades of production use
- Automated backup scheduling
- Configuration version history

**Differentiating features**
- Longest-running configuration backup tool (production-proven)
- Flexible VCS backend support
- Zero cost
- Deep historical data on device configurations

**UX patterns**
- Command-line interface (CLI-driven)
- VCS-based workflows
- Batch automation via scripts
- Configuration archival

**Integration points**
- CVS, SVN, Git for version control
- SNMP, Telnet, SSH for device access
- Custom scripts for reporting

**Known gaps**
- Steep CLI learning curve
- No GUI (command-line only)
- Limited modern integrations
- No REST API
- Requires scripting knowledge for automation
- Poor onboarding for new users

**Licence / IP notes**
- Custom open-source licence
- No vendor lock-in
- Community-driven development

---

### Batfish

**Core features**
- Network configuration analysis and validation (pre-deployment and current-state)
- Vendor-agnostic analysis (works across all major vendors)
- Requires only configuration files (no device access needed)
- Forwarding loop detection
- BGP/OSPF session verification
- ACL rule set analysis
- Firewall policy verification
- IPsec tunnel validation
- Docker containerized deployment

**Differentiating features**
- Pre-deployment validation without device access
- Vendor-agnostic analysis via internal models
- Academic foundation (Microsoft Research, UCLA, USC)
- Automated testing framework with pre-built queries
- Multi-vendor network validation "almost trivial"
- AWS-managed open-source project

**UX patterns**
- Configuration-only input (no device queries)
- Service-based deployment (Docker container)
- Query-based testing framework
- Integration with CI/CD pipelines

**Integration points**
- Network device configurations (all vendors)
- Docker container runtime
- CI/CD pipeline integration
- Python API (pybatfish) for custom queries
- Git-based workflow integration

**Known gaps**
- Not a full NCM suite (validation-only focus)
- No backup or change management
- No GUI (Python/CLI-based primarily)
- Requires configuration file inputs
- Limited to pre-deployment validation workflows
- No real-time monitoring

**Licence / IP notes**
- Apache 2.0 (fully open-source)
- AWS-managed project
- No vendor lock-in

---

## Cross-Cutting Feature Themes

### Table-Stakes Features

- **Configuration Backup**: Automated, scheduled backup across multi-vendor infrastructure
- **Change Tracking**: Version control and history of all configuration changes
- **Baseline Comparison**: Identify and alert on drift from known good configurations
- **Multi-Vendor Support**: Minimum 50+ device types from 5+ vendors
- **Real-Time Alerting**: Immediate notification of unauthorized or unplanned changes
- **Compliance Reporting**: Audit logs and compliance policy verification (SOX, HIPAA, PCI)
- **Rollback Capability**: Revert to previous configurations safely
- **NETCONF/YANG Support**: Modern standards-based device management

### Differentiating Features

- **AI-Driven Troubleshooting**: Automated diagnostics and remediation suggestions (NetBrain)
- **Dynamic Network Mapping**: Visual topology with real-time data overlays (NetBrain)
- **Intent-Based Automation**: No-code workflow definition (NetBrain)
- **Instant Cache Purging**: Sub-second drift resolution (ManageEngine automatic rollback)
- **Pre-Deployment Validation**: Catch errors before deployment (Batfish)
- **REST API Native Support**: Programmatic automation (Oxidized)
- **Git Integration**: DevOps-native version control (Oxidized)
- **Zero-Cost Open-Source**: Full feature NCM without licensing (Oxidized, rConfig)

### Underserved Areas / Opportunities

- **Unified Multi-Vendor Configuration Abstraction**: No standard abstraction layer for expressing configs portably across vendors (similar to OpenConfig but for operational tools)
- **AI-Powered Anomaly Detection**: Automated flagging of security-risky changes without manual rule authorship
- **Predictive Impact Analysis**: Model downstream effects of config changes before deployment
- **Natural-Language Policy Authoring**: LLM translation of security policies into vendor-specific templates
- **Intelligent Change Recommendations**: AI analysis of network state to suggest optimizations and cost reductions
- **Shadow Configuration Discovery**: Automated detection of unauthorized or undocumented configurations
- **Cost Optimization Analysis**: Recommendations on config changes to reduce licensing/bandwidth costs
- **Real-Time Compliance Scoring**: Continuous compliance percentage with predictive remediation timelines

### AI-Augmentation Candidates

- **Anomaly Detection in Config Diffs**: ML flagging changes introducing security risks or compliance violations
- **Natural-Language Query Interface**: LLM-powered queries ("show me every device where ACL 101 changed in 90 days")
- **AI-Assisted Remediation**: Generate corrective config snippets for detected drift
- **Predictive Impact Analysis**: ML modelling downstream effects of config changes across device groups
- **LLM-Powered Compliance Authoring**: Natural language translation to vendor-specific config templates
- **Intelligent Change Recommendations**: AI analysis suggesting config improvements and risk reductions
- **Automatic Workaround Generation**: AI creating temporary fixes while changes are reviewed/approved

---

## Legal & IP Summary

No significant copyright, licensing, or patent conflicts identified. Commercial platforms (SolarWinds, ManageEngine, NetBrain, Infoblox, Cisco NSO) use standard proprietary licensing without known encumbrances. Open-source projects (RANCID with custom licence, Oxidized with MIT, rConfig core, Batfish with Apache 2.0) use permissive licenses compatible with commercial use. Note: Infoblox NetMRI is sunset product with EOL April 2027.

---

## Recommended Feature Scope

**Must-have (MVP)**
- Multi-vendor configuration backup (50+ device types)
- Real-time drift detection with alerting
- Configuration versioning with rollback capability
- Baseline comparison and compliance checking
- Change audit logs with user and timestamp
- REST API for automation integration
- Git integration for version control
- Support for NETCONF/YANG standards

**Should-have (v1.1)**
- Pre-deployment configuration validation (Batfish-style)
- AI-driven anomaly detection in config changes
- Approval workflow for configuration changes
- Automated compliance policy enforcement
- Predictive impact analysis for proposed changes
- Natural-language policy authoring interface
- Real-time compliance scoring dashboard
- Multi-tenant support for MSPs

**Nice-to-have (backlog)**
- Dynamic network visualization with topology mapping
- Intent-based no-code automation platform
- Shadow configuration discovery
- Cost optimization recommendations
- Automatic remediation suggestion engine
- End-to-end device lifecycle management
- Service orchestration across multi-vendor networks

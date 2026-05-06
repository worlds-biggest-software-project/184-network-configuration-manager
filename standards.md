# Standards & API Reference

> Project: Network Configuration Manager · Generated: 2026-05-03

## Industry Standards & Specifications

### IETF / RFC Standards

**RFC 6241 — Network Configuration Protocol (NETCONF)**
- URL: https://datatracker.ietf.org/doc/html/rfc6241
- The foundational standard for programmatic network device configuration management. Defines a set of protocol operations (get-config, edit-config, copy-config, delete-config, lock, unlock) over XML-encoded data. Any NCM tool targeting modern network devices must support NETCONF as the primary management plane interface.

**RFC 7950 — The YANG 1.1 Data Modeling Language**
- URL: https://datatracker.ietf.org/doc/html/rfc7950
- Defines YANG 1.1, the data modeling language used to specify data sent via NETCONF and RESTCONF. YANG models describe device capabilities, configuration data structures, and state information in a vendor-neutral way. Essential for building configuration templates and compliance policies that span multiple vendors.

**RFC 8040 — RESTCONF Protocol**
- URL: https://datatracker.ietf.org/doc/html/rfc8040
- HTTP-based alternative to NETCONF that exposes YANG-defined data as RESTful resources. Supports XML and JSON encoding. Gaining traction on modern network operating systems (NX-OS, IOS-XE, EOS) as the preferred API for management tooling that favours REST over SSH/NETCONF.

**RFC 8342 — Network Management Datastore Architecture (NMDA)**
- URL: https://datatracker.ietf.org/doc/html/rfc8342
- Defines the architectural framework for multiple datastores (running, startup, candidate, intended, operational) that represent distinct views of a device's configuration and state. Critical for any NCM tool that needs to distinguish between "what is configured" and "what is actually running" — a core requirement for drift detection.

**RFC 8526 — NETCONF Extensions to Support NMDA**
- URL: https://datatracker.ietf.org/doc/html/rfc8526
- Extends RFC 6241 with new `<get-data>` and `<edit-data>` operations to target specific NMDA datastores. Required for NETCONF-based NCM tools that want to query the operational state datastore separately from the running configuration.

**RFC 3411 — SNMPv3 Architecture (STD 62)**
- URL: https://datatracker.ietf.org/doc/html/rfc3411
- Describes the SNMPv3 management framework including security (USM — User-based Security Model) and access control (VACM — View-based Access Control Model). While NETCONF/YANG is preferred for modern devices, SNMPv3 remains the only management protocol supported on a significant proportion of legacy devices in enterprise networks. NCM tools must support SNMPv3 for polling device inventory and receiving traps on configuration change events.

### OpenConfig Standards

**OpenConfig YANG Data Models**
- URL: https://www.openconfig.net/projects/models/ · GitHub: https://github.com/openconfig/public
- Vendor-neutral YANG models authored by network operators (Google, AT&T, British Telecom, etc.) covering interfaces, BGP, OSPF, ACLs, system configuration, and more. Supported by Arista, Cisco, Juniper, Nokia, and others. NCM tooling that adopts OpenConfig models can express configuration templates portably across vendors without per-vendor customisation.

**gNMI — gRPC Network Management Interface**
- Specification: https://www.openconfig.net/docs/gnmi/gnmi-specification/ · GitHub: https://github.com/openconfig/gnmi
- gRPC-based management protocol developed by OpenConfig for both configuration management and streaming telemetry, defined using Protocol Buffers (proto3). Supports Get, Set, Subscribe, and Capabilities RPCs over mutually authenticated TLS. Increasingly adopted in cloud-scale environments (data centres, hyperscalers) alongside or in preference to NETCONF. Relevant for NCM tools targeting SD-WAN, cloud-managed networking, and modern campus infrastructure.

### Security & Compliance Standards

**NIST SP 800-53 Rev. 5 — Security and Privacy Controls for Information Systems**
- URL: https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final
- Updated to Release 5.2.0 in August 2025. The Configuration Management (CM) control family (CM-1 through CM-14) directly mandates establishing, documenting, and enforcing security configuration baselines for network devices. NCM tooling used by US federal agencies and DoD contractors must demonstrate alignment with CM-2 (Baseline Configuration), CM-3 (Configuration Change Control), CM-6 (Configuration Settings), and CM-8 (System Component Inventory).

**CIS Benchmarks — Network Device Configuration Baselines**
- URL: https://www.cisecurity.org/cis-benchmarks/
- The Center for Internet Security publishes hardening baselines for major network device platforms (Cisco IOS, Juniper JunOS, Palo Alto PAN-OS, etc.). These are the de-facto compliance baselines used in enterprise and government environments. CIS Controls v8.1 is fully mapped to NIST SP 800-53 Rev 5. NCM compliance modules should ship with pre-built CIS benchmark policies as first-class citizens.

**DISA STIGs — Security Technical Implementation Guides**
- URL: https://www.cyber.mil/stigs/
- Configuration security standards published quarterly by the Defense Information Systems Agency (DISA) for DoD networks. STIGs exist for specific network device platforms (routers, switches, firewalls) and are mandatory for all DoD systems and defence contractors. NCM tools targeting the US public sector must include STIG compliance checking and evidence collection.

**PCI DSS v4.0.1 — Network Security Controls**
- URL: https://www.pcisecuritystandards.org/
- As of March 31, 2025, all 51 future-dated PCI DSS v4.0 requirements are mandatory. Requirement 1 (Install and Maintain Network Security Controls) directly applies to NCM tooling: organisations must document, review, and enforce firewall/router configurations and must capture all configuration changes with user attribution. Service providers must review and confirm their PCI DSS scope every six months, making automated change tracking and audit logs essential.

**HIPAA Security Rule — Audit Controls (45 CFR § 164.312(b))**
- URL: https://www.hhs.gov/hipaa/for-professionals/security/index.html
- Requires healthcare organisations to implement mechanisms that record and examine activity in information systems containing ePHI, including network devices. HIPAA mandates audit log retention of at least six years. NCM tools deployed in healthcare must support immutable audit trails, individual user attribution, and long-term log retention.

**SOX (Sarbanes-Oxley Act) — IT General Controls**
- Section 404 requires documented and auditable controls over IT systems, including network infrastructure. SOX audit logs must be retained for seven years. NCM change approval workflows, immutable diff history, and audit exports are core requirements for financial services compliance.

**ISO/IEC 20000-1 — IT Service Management**
- URL: https://www.iso.org/standard/70636.html
- The international standard for IT service management, closely aligned with ITIL. The Change Management and Configuration Management process requirements in ISO 20000-1 define what an NCM tool must support to underpin a compliant ITSM programme: RFC (Request for Change) tracking, configuration item (CI) records, change approval workflows, and post-change verification.

### Data Model & API Specification Standards

**OpenAPI Specification 3.1 / 3.2**
- URL: https://spec.openapis.org/oas/v3.2.0.html
- The industry-standard format for describing RESTful APIs in YAML or JSON. An NCM tool exposing a REST API should publish an OpenAPI 3.1+ specification to enable automatic client library generation, interactive documentation (Swagger UI/Redoc), and integration with API gateways. Fully compatible with JSON Schema Draft-07.

**JSON Schema**
- URL: https://json-schema.org/
- Used to validate the structure of configuration payloads, device inventory records, and compliance rule definitions. JSON Schema is embedded in OpenAPI 3.1 and is the basis for YANG-to-JSON serialisation via RFC 7951.

**RFC 7951 — JSON Encoding of YANG Data**
- URL: https://datatracker.ietf.org/doc/html/rfc7951
- Defines how YANG-modelled data is encoded in JSON format for use with RESTCONF and other JSON-native management protocols. Essential for any NCM tool that stores or transmits configuration data in JSON rather than XML.

### Authentication & Security Standards

**OAuth 2.0 (RFC 6749) & OpenID Connect**
- URL: https://oauth.net/2/ · https://openid.net/connect/
- Standard delegated authorisation framework. NCM APIs exposed to external integrations (CI/CD pipelines, ITSM platforms, custom dashboards) should support OAuth 2.0 bearer tokens with JWT access tokens (RFC 9068) for machine-to-machine authentication. OpenID Connect provides the identity layer for user-facing SSO.

**mTLS — Mutual TLS Authentication**
- RFC 8705 (OAuth 2.0 Mutual-TLS Client Authentication). gNMI mandates mutual TLS for all sessions. NETCONF over SSH implicitly provides mutual authentication. NCM tools managing sensitive network infrastructure should support mTLS for device-facing connections.

---

## Similar Products — Developer Documentation & APIs

### SolarWinds Network Configuration Manager (NCM)

- **Description:** Enterprise-grade multi-vendor NCM with configuration backup, drift detection, compliance reporting, and firmware upgrade orchestration. Part of the broader SolarWinds Orion platform.
- **API Documentation:** https://documentation.solarwinds.com/en/success_center/ncm/content/ncm_documentation.htm
- **SDK / Developer Resources:** SolarWinds Platform SDK (SWIS — SolarWinds Information Service); SWQL Studio for querying the schema. SDK wiki: https://github.com/solarwinds/OrionSDK
- **Developer Guide:** https://documentation.solarwinds.com/en/success_center/ncm/content/ncm_getting_started_guide.htm
- **Standards:** REST/JSON over HTTPS; SWIS uses a proprietary query language (SWQL, similar to SQL). Swagger documentation available on the Orion platform.
- **Authentication:** API key (passed as header or query parameter); integrations via Orion REST API at `https://<server>:17778/SolarWinds/InformationService/v3/Json/`.

---

### ManageEngine Network Configuration Manager

- **Description:** Commercial NCM offering real-time drift detection, automatic rollback, compliance auditing, and multi-vendor configuration backup. Positioned as a cost-effective SolarWinds alternative.
- **API Documentation:** https://www.manageengine.com/network-configuration-manager/help/rest-api-ncm.html
- **REST API Overview:** https://www.manageengine.com/network-configuration-manager/restapi.html
- **REST Configlets API:** https://www.manageengine.com/network-configuration-manager/help/rest-configlets-v12.html
- **Standards:** REST/JSON; OpenAPI specification not confirmed publicly. Sample URL format: `http://localhost:<port>/api/json/<Module>/<APIName>?param=value`.
- **Authentication:** API key generated per account via Settings → REST API. Key passed as query parameter in every request.

---

### NetBrain

- **Description:** Enterprise network automation platform with dynamic topology mapping (Digital Twin), AI-assisted troubleshooting, intent-based no-code automation, and change management. R12 released 2025.
- **API Documentation:** https://www.netbrain.com/docs/12tp0fe0ge/help/HTML/rest-api-reference.html
- **SDK / GitHub:** https://github.com/NetBrainAPI/NetBrain-REST-API-R11.1b (latest public version)
- **Developer Guide:** REST API versioned per release; GitHub repositories maintained for V8.x through R11.1b.
- **Standards:** REST/JSON. API covers topology retrieval, device management, automation triggers, and diagnostic workflows.
- **Authentication:** Token-based authentication; bearer token obtained via login endpoint.

---

### Cisco Network Services Orchestrator (NSO)

- **Description:** Model-driven service orchestration and configuration lifecycle management supporting 1,000+ device types via Network Element Drivers (NEDs). Cloud-native deployment available from NSO 2025.x releases.
- **API Documentation:** https://developer.cisco.com/docs/nso/
- **SDK API Reference:** https://developer.cisco.com/docs/nso/api/
- **NETCONF Server Guide:** https://developer.cisco.com/docs/nso/guides/the-nso-netconf-server/
- **SDKs:** Java, Python, and Erlang language bindings. NED SDK for building custom device drivers.
- **Standards:** NETCONF (RFC 6241), RESTCONF (RFC 8040), YANG (RFC 7950), JSON-RPC. NSO exposes its own CDB (Configuration Database) via MAAPI (Management Agent API).
- **Authentication:** RESTCONF and NETCONF sessions authenticated via username/password or certificates; API supports OAuth 2.0 in enterprise deployments.

---

### Oxidized

- **Description:** Open-source (MIT) network device configuration backup tool, actively maintained RANCID successor. Supports 130+ OS types. Native Git integration and REST API.
- **API Documentation:** https://github.com/ytti/oxidized/blob/master/docs/Ruby-API.md
- **GitHub:** https://github.com/ytti/oxidized
- **Configuration Docs:** https://github.com/ytti/oxidized/blob/master/docs/Configuration.md
- **Standards:** REST/JSON provided via the `oxidized-web` gem. Git-backed version control (any Git remote). SNMP, SSH, and NETCONF used for device access.
- **Authentication:** HTTP Basic Auth or API token (configured per deployment). Integration via REST hooks triggered by syslog events.

---

### rConfig V8

- **Description:** Open-source (core) and commercial (Pro/Enterprise) NCM platform built on a modern Laravel/PHP stack. V8 Core released 2025 with a fully modernised architecture. REST API and GraphQL support in Pro/Enterprise tiers.
- **API Documentation:** https://docs.rconfig.com/developers/api/
- **GitHub:** https://github.com/rconfig/rconfig
- **Full Documentation:** https://docs.rconfig.com/
- **Standards:** REST/JSON with OpenAPI (Swagger) specification; GraphQL support in Pro tier. Standard HTTP methods and JSON payloads.
- **Authentication:** API key authentication. Pro/Enterprise tiers support OAuth 2.0.

---

### Batfish (pybatfish)

- **Description:** Open-source (Apache 2.0) network configuration analysis and pre-deployment validation tool. Operates entirely on configuration files — no device access required. AWS-managed project with academic roots (Microsoft Research, UCLA, USC).
- **API Documentation:** https://batfish.readthedocs.io/en/latest/
- **Python SDK (pybatfish):** https://github.com/batfish/pybatfish · https://pypi.org/project/pybatfish/
- **GitHub:** https://github.com/batfish/batfish
- **Standards:** REST/JSON internal service API wrapped by pybatfish client library. Docker container deployment. Integrates with pytest and CI/CD pipelines.
- **Authentication:** No authentication on the service API by default (assumes local or network-isolated deployment). TLS and auth can be configured for production deployments.

---

### Unimus

- **Description:** Commercial network automation platform supporting 400+ device types across 150+ vendors. Per-device subscription model. REST API available from v1.7+; APIv3 (Swagger UI) introduced in v2.2.0.
- **API Documentation (v3):** https://wiki.unimus.net/display/UNPUB/Full+API+v.3+documentation
- **API Documentation (v2):** https://wiki.unimus.net/display/UNPUB/Full+API+v.2+documentation
- **Swagger UI:** Available at `http://<unimus-ip>:8085/api/v3/ui` on any running Unimus instance.
- **Standards:** REST/JSON. Paginated responses (max 50 items per page). Supports GET, POST, PATCH, DELETE.
- **Authentication:** API key passed as a request parameter. Keys generated per user in account settings.

---

### IP Fabric

- **Description:** Vendor-neutral network assurance platform that automates discovery, verification, visualisation, and documentation of large-scale enterprise networks. Recommended migration target for Infoblox NetMRI customers.
- **API Documentation:** https://docs.ipfabric.io/latest/IP_Fabric_API/
- **Python SDK:** https://pypi.org/project/ipfabric/
- **GitHub (docs):** https://github.com/ipfabric/docs
- **Awesome List:** https://github.com/ipfabric/awesome-ipfabric-list
- **Standards:** REST/JSON with OpenAPI specification. Python SDK supports Python 3.10+. Vendor API discovery uses exponential backoff for resilient device polling.
- **Authentication:** API token authentication. Bearer token passed in Authorization header.

---

## Notes

**Emerging standards to watch:**

- **gNMI / OpenConfig** adoption is accelerating in cloud-native networking and SD-WAN environments. Tools targeting hyperscaler or cloud-campus environments should prioritise gNMI alongside NETCONF.
- **gNOI (gRPC Network Operations Interface)** — a companion to gNMI for operational tasks (file transfer, system reset, certificate management). Specification at https://github.com/openconfig/gnoi. Not yet widely adopted but increasingly relevant for full device lifecycle management.
- **YANG Catalog** — a community-maintained repository of YANG modules at https://yangcatalog.org/ that can be queried to discover which YANG modules a given vendor/platform supports. Useful for building multi-vendor config template engines.
- **Network Automation Forum (NAF) / IETF OPSAWG** — active working groups developing best-practice guidance for network automation and configuration management. Relevant drafts include IETF YANG Push (RFC 8641) for streaming configuration change notifications.

**RFC 8641 — Subscription to YANG Notifications for Datastore Updates (YANG Push)**
- URL: https://datatracker.ietf.org/doc/html/rfc8641
- Enables clients to subscribe to streaming notifications when datastore content changes. Directly relevant for real-time configuration drift detection without requiring polling: devices emit change events that the NCM tool can consume to trigger immediate diff analysis.

**Gaps in current standardisation:**
- No standard API for cross-vendor compliance policy expression — each tool uses a proprietary policy language or rule engine. This represents a significant opportunity for an open standard or open-source common policy format.
- No standard change workflow API — approval, staging, and rollout steps are vendor-specific in all current NCM tools.

# CSIT302 Cybersecurity — Security Policy & Vulnerability Management Notes

---

## 1. What is a Security Policy?

According to NIST, a security policy is:
- A set of **criteria** for the provision of security services
- The **statement** of required protection for information objects
- A set of **rules** governing all aspects of security-relevant system and component behaviour
- A definition of **objectives and constraints** for the security program

---

## 2. Reviewing Security Policy

### Key Questions to Ask
- Do you have a security policy in place?
- Do you enforce this policy?
- How often do you review and improve it?

> Security policy is a **living document** — it must be revised and updated regularly or on-demand.

### What Security Policies Should Include
- **Industry standards, procedures, and guidelines** — necessary to support information risks in daily operations
- **Well-defined scope** — must state whether the policy applies to a specific group or all users including contractors
- **Foundation in the CIA Triad** — policies must protect Confidentiality, Integrity, and Availability

### User Requirements
- Users must protect and uphold the CIA triad in data and systems
- Users must be aware of their responsibilities and the **consequences of violating policies**

---

## 3. Policy Document Hierarchy

```
Policy → Procedure / Standard → Guidelines / Best Practices
  (High Enforcement, Less Technical) ←→ (Low Enforcement, More Technical)
```

| Document | Description |
|---|---|
| **Policy** | High-level expectations; guides decisions and outcomes; must be non-technical and enforced by proper authority |
| **Procedure** | Step-by-step document outlining how something must be done |
| **Standard** | Establishes mandatory technical requirements; must cover policy requirements needing technical specs |
| **Guidelines** | Optional or recommended guidance; aligned with policy and standards; includes practical examples and best practices |
| **Best Practices** | Company-wide or role-specific practices; can be part of guidelines (e.g. all web servers must apply vendor security hardening before deployment) |

> To keep all documents synchronised and management-sponsored, an **organisation-wide security program** is needed (e.g. NIST SP 800-53).

---

## 4. NIST SP 800-53

- **NIST Special Publication 800 series**: guidelines, recommendations, technical specifications, and annual reports on cybersecurity
- **NIST SP 800-53** ("Security and Privacy Controls for Federal Information Systems and Organizations") is linked to FIPS Publication 200 — a **mandatory federal standard** developed in response to FISMA
- Organisations have **flexibility** in applying the baseline security controls

### NIST SP 800-53 Security Program Areas

| Management | Privacy | Operational | Technical Controls |
|---|---|---|---|
| Awareness training | Authority | Certification & accreditation | Access control |
| Personnel security | Data accountability & audit | Contingency planning | Audit & accountability |
| Planning | Data minimisation | Incident response | Configuration management |
| Risk assessment | Data quality & integrity | Maintenance | Identification & authentication |
| System & services acquisition | Data security | Media protection | System & communication protection |
| | Data use limitation | Physical & environmental protection | System & information integrity |

---

## 5. Educating End Users

### Security Awareness Training
- Part of **management control** (per NIST SP 800-53)
- One of the most critical components — an uneducated user can cause **tremendous organisational damage**
- Should be delivered to **all employees** and **continuously updated** with new attack techniques
- Ideally online (company intranet), with rich visuals and **self-assessments**

### Training Content Should Include
- **Real-world examples** — e.g. showing what phishing emails actually look like
- **Practice** — interactive exercises such as identifying spear phishing or fake social media campaigns

### Training Outcomes
- Users acknowledge completion of training
- Users are aware of security threats and countermeasures
- Users understand the consequences of not following security policy

### BYOD (Bring Your Own Device)
- Personal devices are **easy targets** for hackers
- A compromised personal device is often a direct path to company data (usually not isolated)
- Ideally, BYOD should be **prohibited** in high-confidentiality environments — but enforcement is resource-intensive

### Social Media Guidelines
- Social media is heavily used in **social engineering attacks**
- Policy must align with HR and legal requirements
- Must define **appropriate business behaviour** and state disciplinary actions clearly
- Guidelines must address: defamatory posts, pornographic content, proprietary issues, harassment, and hostile work environment content

---

## 6. Policy Enforcement

### Understanding the Network First
To enforce policy effectively, you must understand:
- What the **endpoints** are
- What **servers** the organisation has
- How **information flows**
- Where **information is stored**
- Who **has** and who **should have** data access

> Many companies fail to enforce policies because they only focus on endpoints and servers — a **holistic approach** is required, covering switches, printers, and IoT devices.

### Group Policy (Active Directory)

**Active Directory** organises network objects (users, computers, printers, shared folders) into a logical hierarchical structure and provides authentication/authorisation.

Key concepts:

| Term | Definition |
|---|---|
| **Domain** | A collection of objects in an Active Directory network |
| **OU (Organisational Unit)** | A container (subdomain) for objects; reflects org structure |
| **Domain Tree** | Multiple domains; root domain is parent to child domains |
| **Trust Relationship** | Default parent↔child = transitive two-way trust; alternatives: one-way, non-transitive |
| **Group Policy (GP)** | Feature that centrally controls user/computer account environments |
| **GPO (Group Policy Object)** | A collection of settings defining system behaviour for a defined group; distributed via AD to OUs |

GPOs can be **segmented per OU** — e.g. HR servers can have a custom policy different from Research Lab servers.

### Important GPO Settings for Security

| # | Setting | Purpose |
|---|---|---|
| 1 | Limit Control Panel access | Prevent non-admin users from modifying system configurations |
| 2 | Prevent LAN Manager Hash storage | Prevent pass-the-hash attacks |
| 3 | Control Command Prompt access | Prevent high-level access exploitation |
| 4 | Disable forced system restarts | Prevent loss of settings/unsaved work |
| 5 | Disallow removable media (DVDs/CDs) | Prevent malware infection via removable drives |
| 6 | Restrict software installations | Prevent unapproved/malicious software |
| 7 | Disable guest account | Prevent attacker access via guest credentials |
| 8 | Set minimum password length | Admins: ≥15 chars; Regular users: ≥12 chars |
| 9 | Set maximum password age | Recommendation: 42 days |
| 10 | Disable Anonymous SID enumeration | Prevent attackers from querying user/group SIDs |

### Application Whitelisting
- Only **licensed and IT-authorised** software should run on user machines
- Policy enforcement ensures only **approved applications** can execute
- Reference: NIST Publication 800-167

### Common Configuration Enumeration (CCE)
- CCE provides standard identifiers for system configuration issues
- Helps organisations apply and verify secure configurations consistently (system hardening)

---

## 7. ISO 27001 — Information Security Management Framework

- Full title: *"ISO/IEC 27001 — Information technology — Security techniques — Information security management systems — Requirements"*
- Provides a framework for organisations of **any size or industry** to protect information systematically and cost-effectively via an **ISMS (Information Security Management System)**
- Originally published 2005; revised 2013 and 2017

### Basic Goal: Protect the CIA Triad
- **Confidentiality** — keep information private from unauthorised parties
- **Integrity** — maintain information in its original purpose and meaning
- **Availability** — ensure information and resources are accessible to authorised users

### What ISMS Involves
- Identifying stakeholder expectations around information security
- Identifying information security risks
- Defining controls and mitigation methods
- Setting clear security objectives
- Implementing controls and risk treatments
- Continuously measuring control effectiveness
- Making continuous improvements

### Why Organisations Need ISO 27001
- **Legal compliance** — meets requirements of laws, regulations, and contracts
- **Competitive advantage** — certification signals trustworthiness
- **Lower costs** — preventing incidents is cheaper than responding to them
- **Better organisation** — clear procedures and processes for security

### How ISO 27001 Works
```
Risk Assessment and Treatment → Safeguard Implementation
```
Core function: identify risks, then systematically treat them through security controls (safeguards).

### 14 Domains of ISO 27001
1. Information security policies
2. Organisation of information security
3. Human resources security
4. Asset management
5. Access control
6. Cryptography
7. Physical and environmental security
8. Operations security
9. Communications security
10. System acquisition, development and maintenance
11. Supplier relationships
12. Information security incident management
13. Information security aspects of business continuity management
14. Compliance

### 114 Controls Span Five Areas
- **Technical** — e.g. backup, antivirus
- **Organisational** — e.g. access control policy, BYOD policy
- **Legal** — e.g. NDA, SLA
- **Physical** — e.g. CCTV, locks, alarms
- **Human resource** — e.g. security awareness training, ISO 27001 auditor training

---

## 8. NIST Cybersecurity Framework (CSF)

- A set of **guidelines and best practices** to help organisations build and improve their cybersecurity posture
- Enables organisations to better **identify, detect, respond to, prevent, and recover from** cyber attacks
- Considered an **essential standard** for building a cybersecurity program
- Version 1.0 (2014) → Version 1.1 (2018)

### Five Core Functions

| Function | Description |
|---|---|
| **Identify** | Recognise processes and assets that need protection |
| **Protect** | Implement appropriate safeguards for enterprise assets |
| **Detect** | Implement mechanisms to identify cybersecurity incidents |
| **Respond** | Develop techniques to contain impacts of cybersecurity events |
| **Recover** | Implement processes to restore impaired capabilities and services |

---

## 9. Vulnerability Management

### Benefits of a Vulnerability Management Strategy
- Enables **orderly scheduling** of all vulnerability mitigation processes
- Helps targets and victims **mitigate damage** from cybersecurity incidents
- Ensures the right counteractions are performed **at the right time**, before attackers can exploit vulnerabilities

### Five Phases of Vulnerability Management

#### Phase 1: Asset Inventory
- A list of all computing devices for tracking and patching
- Managed by a small, responsible group
- Enables administrators to quickly find and patch systems
- **Consequences of poor inventory**: devices missed during updates; incorrect security spending (under or overspend)
- **Challenges**: poor change management; lack of effective tracking tools

#### Phase 2: Information Management
- Plan how to **control information flows** in and out of the organisation
- **Network security**: prevent threats entering/leaving the network
- **Data security**: protect trade secrets, customer PII — exposure can cause reputational damage and regulatory fines
- Tools: CSIRT (Computer Security Incident Response Team), **least privilege policy** ("need-to-know"), endpoint data controls

#### Phase 3: Risk Assessment (6 Stages)
1. **Scope identification** — define what is being assessed
2. **Collecting data** — gather relevant system and network data
3. **Analysis of policies and procedures** — review existing documentation
4. **Vulnerability analysis** — identify weaknesses in systems
5. **Threat analysis** — identify potential threats that could exploit vulnerabilities
6. **Analysis of acceptable risks** — determine which risks the organisation can tolerate

> In this phase, the organisation must **prioritise vulnerabilities** and allocate resources accordingly.

#### Phase 4: Reporting and Remediation Tracking
- Separate reports for technical (IT) and non-technical (management) audiences
- Track whether identified vulnerabilities have been resolved
- Tools: Foundstone's Enterprise Manager, Latis Reporting Tool

#### Phase 5: Response Planning
- Resolution, eradication, cleansing, and repair activities
- Patches and system upgrades applied here
- Primarily done through **documentation** (guides patching, supports new staff, prevents mistakes in emergencies)

---

## 10. Vulnerability Management Tools

| Phase | Example Tools |
|---|---|
| Asset inventory | Peregrine tools, LANDesk Management Suite, StillSecure |
| Information management | CERT Coordination Center, Security Focus, Symantec Security Response |
| Risk assessment | In-house checklists, ArcSight Enterprise Security Manager (ESM) |
| Vulnerability analysis | **Nessus** (deep assessment), **Nmap** (network mapping + basic scripting) |
| Reporting & remediation | Foundstone's Enterprise Manager, Latis Reporting Tool |
| Response planning | Documentation (no dominant commercial tool) |

### Nessus vs Nmap
- **Nmap**: quickly maps networks, identifies connected assets and basic vulnerabilities
- **Nessus**: in-depth vulnerability assessment — detects OS versions, missing patches, relevant exploits, and ranks by threat level

### Risk Assessment Checklist Questions
- How can identified vulnerabilities impact the organisation?
- Which business resources are at risk of compromise?
- Is there a risk for remote exploitation?
- What are the consequences of an attack?
- Is the attack reliant on tools or scripts?
- How can the attack be mitigated?

---

## 11. Common Vulnerabilities and Exposures (CVE)

- A **publicly maintained catalog** of known information security vulnerabilities and exposures
- Supported by US-CERT, US Homeland Security Department, and MITRE

### Definitions
- **Vulnerability**: The state of being exposed to an attacker who can maliciously gain **full access** to a network or system
- **Exposure**: A mistake in software code or configuration that provides an attacker with **indirect access** to a network or system

### Purpose of CVE
- **Standardise** identification of known vulnerabilities
- Provide security administrators with **quick, cross-source access** to technical information about specific threats

### CVE Entry Structure
| Field | Description |
|---|---|
| `CVE-ID` | Identifier format: `CVE-YEAR-DIGITS` (e.g. CVE-2012-2234) |
| `Description` | Text description of the issue |
| `References` | URLs and additional information |
| `Date Entry Created` | When the entry was added |
| `Phase/Votes/Comments` | Status and community input |

---

## 12. Best Practices for Vulnerability Management

### Asset Inventory
- Establish a **single point of authority** for the inventory
- Use **consistent abbreviations** across all data entries
- **Validate the inventory at least once per year**

### Information Management
- Allow employees to **subscribe to security mailing lists**
- Have the incident response team **publish reports and advisories** on an internal site
- Hold **periodic conferences** on new vulnerabilities, malware, and social engineering
- Use a **standardised email template** for security communications — visually distinct from normal emails

### Risk Assessment
- Document processes for **reviewing new vulnerabilities immediately** when they appear
- **Publish risk ratings** to users/public
- Ensure asset inventories are **current and accessible** during risk assessment
- Maintain a **strict change management process** to brief incoming staff on security posture

### Vulnerability Analysis
- Always **seek permission** before extensive network testing (to avoid disruption or damage)
- Choose **appropriately scoped scanning tools** — neither too shallow nor unnecessarily deep

### Reporting and Remediation Tracking
- Use reliable tools to **notify asset owners** of vulnerabilities and resolution status
- Agree with management on **remediation timeframes and resources**
- Make **consequences of non-remediation** clear
- Prioritise remediation by **hierarchy of severity**

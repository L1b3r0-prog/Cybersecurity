# CSIT302 Cybersecurity — Security Policy & Vulnerability Management Notes

## What is a Security Policy?

According to NIST, a security policy is:
- A set of **criteria** for the provision of security services
- The **statement** of required protection for information objects
- A set of **rules** governing all aspects of security-relevant system and component behaviour
- A definition of **objectives and constraints** for the security program

---

## Reviewing Security Policy

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

## Policy Document Hierarchy

```
Policy → Procedure / Standard → Guidelines / Best Practices
  (High Enforcement, Less Technical) ←→ (Low Enforcement, More Technical)
```

Policy
- Basis of everything and set high level expectation. It will also be used to guide decisions and achieve outcomes
- For all participants so it can't be too technical
- Must be enforced by proper authority

Procedure
- Doc that has procedural steps that outline how something must be done

Standard
- Doc establishes tech requirements that must be followed
  - Everyone must compy with certain standard that were previously established
- Must provide enough tech details to give accurate and detailed explanation of requirements to the relevant personals (sec engineers or sec management officers)

Guidelines
- Optional but can also be additional recommended guidance
  - Each company has freedom to define whether the guidelines are optional or needed
- Guidelines must be aligned with policy and standard docs
  - Usually written to give more specific details with practical examples such as best practices
- Can be used to guide someone who has substantial knowledge of info tech but not specialized on cybersecurity domain

Best practices
- Implemented by entire company or some departments
- Can be established per role
- Can be part of guidelines

| Document | Description |
|---|---|
| **Policy** | High-level expectations; guides decisions and outcomes; must be non-technical and enforced by proper authority |
| **Procedure** | Step-by-step document outlining how something must be done |
| **Standard** | Establishes mandatory technical requirements; must cover policy requirements needing technical specs |
| **Guidelines** | Optional or recommended guidance; aligned with policy and standards; includes practical examples and best practices |
| **Best Practices** | Company-wide or role-specific practices; can be part of guidelines (e.g. all web servers must apply vendor security hardening before deployment) |

> To keep all documents synchronised and management-sponsored, an **organisation-wide security program** is needed (e.g. NIST SP 800-53).

---

## NIST SP 800-53

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

## Educating End Users

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

## Policy Enforcement

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

## ISO 27001 — Information Security Management Framework

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

## NIST Cybersecurity Framework (CSF)

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


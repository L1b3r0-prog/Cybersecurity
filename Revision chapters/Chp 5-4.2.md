## Vulnerability Management

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

## Vulnerability Management Tools

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

## Common Vulnerabilities and Exposures (CVE)

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

## Best Practices for Vulnerability Management

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

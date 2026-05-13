# CSIT302 Cybersecurity – Threat Intelligence & Investigating an Incident

---

## 1. Intelligence – Data vs Information vs Intelligence

These three terms are often incorrectly used interchangeably.

- **Data** – Simple facts available in large volumes. In cybersecurity, examples include IP addresses or logs. Raw data alone is of limited utility.
- **Information** – Produced when data is collated to provide a useful output. Example: a series of logs showing a spike in suspicious activity.
- **Intelligence** – Comes from the processing and analysis of information, used to inform decision-making. Example: collated log data contextualised with prior incident reports, allowing a mitigation strategy to be developed.

The pipeline is: **Collection → Processing → Analysis → Intelligence**

---

## 2. Introduction to Threat Intelligence

**Key definitions:**
- CIA: Intelligence is knowledge and foreknowledge of the world — the prelude to decision and action.
- NCA (UK): Intelligence is information collected to answer specific questions on who, what, where, when, how, and why.
- NIST SP 800-150: Threat intelligence is threat information that has been aggregated, transformed, analysed, interpreted, or enriched to provide the necessary context for decision-making.

**Intelligence Collection Disciplines:** OSINT, HUMINT, SIGINT, GEOINT, IMINT

In cybersecurity, threat intelligence specifically refers to **Cyber Threat Intelligence (CTI)**.

### Why CTI Matters
- Brings more meaningful results from collected data, revealing actions not detectable by traditional sensors
- Enables a **proactive** approach against both known and unknown threats
- Key principle: **The targeted attacks need the targeted defense!**
- Ensures organisations can **prevent, detect, and respond** to realistic, contemporary attacks

### Intelligence-Led Testing Frameworks
The Bank of England's **CBEST** was the first intelligence-led cyber security testing framework. It ensures security testers and threat intelligence providers work together, replicating real attacks from sophisticated adversaries. Expanded frameworks include:

- **TIBER-NL** – Dutch financial sector
- **TBEST** – UK telecoms sector
- **TIBER-EU** – European financial sector
- **iCAST** – Hong Kong's financial sector
- **GBEST** – UK government departments
- **ATTEST** – UK aviation industry

---

## 3. Areas Where Cyber Threat Intelligence Can Be Used

### Profiling Motivations
Detection can be improved by learning more about adversaries. The three main attacker motivations are:

- **Cybercrime** – Primary motivation is financial gain.
- **Hacktivism** – Broader motivation; ranges from political expression to support for a particular cause.
- **Cyber espionage / State-sponsored** – Growing number of cases as part of larger state-sponsored campaigns.

> Key question to ask: **Which type of attacker is most likely to target our organisation?**

Threat intelligence helps scope data based on the adversary. For example, a financial institution should obtain intelligence from adversaries actively attacking the financial industry.

Without an intelligence-led approach, organisations will either defend against too little (because they don't understand the threats) or try to defend against everything — an unsustainable approach that can impair operations.

### Analysing Attacker Tactics
Understanding attacker methodologies, tools, and strategies.

### Analysing Techniques (of Attacks)
Identifying indicators of specific malware.

### Assessing Operations
Assessing an organisation's ability to determine future cyber threats.

---

## 4. Levels of Cyber Threat Intelligence

Each level differs in the nature and format of the material conveyed, its intended audience, and its application.

| Level | Focus | Audience | Format |
|---|---|---|---|
| **Strategic** | High-level, changing risk landscape | Senior decision makers | Plain language, business risk focus, less frequent |
| **Tactical** | TTPs (Tactics, Techniques, Procedures) + IOCs | Network defenders (NOCs) | Combination of machine-readable (IOCs) and human-readable (TTPs) |
| **Operational** | Specific impending attacks | Network defenders | Large volume, machine and human readable, real-time |
| **Technical** | Indicators of specific malware | Technical analysts | Low-level, machine-readable |

### Operational Threat Intelligence
- Collects data and information to respond to a threat **as it is in progress**
- Provides real-time alerts to help security teams understand attack scope
- Relates to details of potential impending operations against an organisation
- Example: chatter from cyber activists discussing targets, or data leaked on dark web forums

### Tactical Threat Intelligence
- Covers TTPs used by threat actors; **IOCs (Indicators of Compromise)** are the main deliverable
- Useful for updating signature-based defence systems and for proactive measures like threat hunting
- Particularly valuable for Network Operations Centers (NOCs)
- IOCs supplied in machine-readable formats; TTPs in human-readable formats requiring human action

### Strategic Threat Intelligence
- Informs senior decision makers of broader changes in the threat landscape

---

## 5. Microsoft Threat Intelligence (Example)

Microsoft consumes threat intelligence through:
- **Microsoft Threat Intelligence Center**, aggregating data from:
  - Honeypots, malicious IP addresses, botnets, and malware detonation feeds
  - Third-party sources (threat intelligence feeds)
  - Human-based observation and intelligence collection
- Intelligence from consumption of their own services
- Intelligence feeds generated by Microsoft and third parties

---

## 6. Open Source Tools for Threat Intelligence (Tactical)

- **Quick IP validation:** https://fraudguard.io/
  - Returns geolocation, threat type, risk level, and discovery date for a given IP
  - Example: IP `220.227.71.226` returned risk level 5, threat type `honeypot_tracker`, located in Mumbai, India
- **Malware inspection:** https://vms.drweb.com/
- **Threat intelligence exchange:** https://otx.alienvault.com/
  - Provides Indicators of Compromise (IOCs) including file hashes, URLs, and domain information

---

## 7. Leveraging Threat Intelligence to Investigate Suspicious Activity

### The Challenge of Alert Volume
- An average large organisation processes ~17,000 malware alerts per week (Microsoft *Lean on the Machine* report)
- On average it takes **99 days** to discover a security breach
- Overload leads to random prioritisation or ignoring alerts entirely

### Threat Intelligence Assisting Incident Response
- The Blue Team (focused on defence) collaborates with the incident response team by providing the right data to find the **root cause** of an issue

### Alert Triage
Alert triage is the process of **determining the most important threat that must be alerted**. Failing or delaying this leads to a domino effect — if triage fails, the operation fails. Alert triage typically occurs at the **Network Operations Center (NOC)**.

### Key Questions at the End of a Threat Intelligence Investigation
- Which systems were compromised?
- Where did the attack start?
- Which user account was used to start the attack?
- Did it move **laterally**? If so, which systems were involved?
- Did it **escalate privilege**? If so, which privileged account was compromised?
- Did it try to communicate with **command and control (C2)**? If successful:
  - Did it download anything from C2?
  - Did it send anything to C2?
- Did it try to **clear evidence**? Was it successful?

---

## 8. Investigating an Incident

### Scoping the Issue
**Scoping** is the process of determining whether a given incident is security-related. Not every incident is security-related — it is vital to scope before beginning a full investigation, as symptoms may initially appear security-related but turn out to be non-security issues.

**Scoping guidelines:**
- Example: users reporting slow systems → conduct basic performance troubleshooting first, not a full security investigation
- Determine the **frequency** of the issue during scoping
- If the issue is not currently occurring, configure the environment to collect data when reproducible
- **Document all steps** and provide an accurate action plan

---

## 9. Key Artifacts

More data does not mean a better investigation. Data collection should focus on **vital and relevant artifacts** from the target system. Too much data can distract from the root cause.

### Key Artifacts in a Windows System
Stored in the **registry key**, retrievable via PowerShell (e.g., `Get-ItemProperty`):
- Location (time zone) of the machine
- Networks the machine visited
- USB usage history
- Malicious software configured to start at Windows startup

For **live investigations**, traffic captures and process dumps can also be collected.

### Security Events That Can Be Captured
**Process/System events:**
- Audit log was cleared
- Logon success or failure
- A registry value was modified
- Unauthorised access attempt to an object (file system) — can identify who made the change
- A new process was created — malware/ransomware often spawn `cmd.exe` processes
- A scheduled task was enabled or updated

**User account events:**
- Account enabled, created, or locked out
- Password reset
- Denied remote access

**Policy events:**
- Log policy changed
- Domain policy changed
- Changes in security-enabled global or local group

**Firewall events:**
- A change was made to the Windows Firewall exception list

---

## 10. Case Study: On-Premises Compromised System

### Attack Vector: Phishing Email
1. Victim received a phishing email with an embedded image containing a hyperlink
2. Victim clicked the image, saw a briefly opening/disappearing window
3. Victim ignored the email

### Detection
- Days later, IT sent an automated report flagging that the victim's machine had accessed a suspicious site
- Victim submitted the email as evidence

### Investigation Steps
- The linked URL was checked against threat intelligence tools — **3/65 engines flagged it as malware** (BitDefender, Fortinet, Sophos AV all flagged it as malicious)
- Event logs were reviewed and revealed three key malicious processes:
  - **`mimikatz.exe`** – Used to perform a **pass-the-hash attack**
  - **`PsExec.exe`** – Used to perform **privilege escalation**
  - **`procdump.exe`** – Used to **dump credentials**
- A log also showed **the audit log was cleared** (Event ID 1102), hiding how privilege escalation was achieved

### Summary
- Attack chain: phishing email → hyperlink → download malicious package → extract tools (mimikatz, procdump, psexec)
- Because the computer was not part of the domain, only **local credentials** were compromised

---

## 11. Case Study: Compromised System in a Hybrid Cloud

### Setup
- Compromised system is on-premises; company uses a cloud-based monitoring system (Azure Security Center)
- Same attack vector: phishing email → clicked hyperlink → compromised

### Key Difference
- An **active sensor** (Azure Security Center) monitored the system and immediately triggered an alert to SecOps
- Users don't wait days to find out — the response is **faster and more accurate**

### Four Events Recorded (Azure Security Center)
| Event | Severity |
|---|---|
| Antimalware Action Taken | Low |
| Suspicious process name detected | Medium |
| Suspicious Process Execution Activity Detected | Medium |
| Suspicious process executed | **High** |

- Although antimalware captured the initial malware, the attacker continued and succeeded
- The high-severity event corresponded to **mimikatz** running under an admin account (`EMSAdmin`), confirming privilege escalation was achieved

### Managing Alert Volume
In real-world scenarios, sensor and monitoring data is overwhelming. The platform used must:
- Aggregate all logs and rationalise results
- Provide strong **searching capabilities** to dig for important information
- Offer efficient **visualising and searching interfaces**

---

## 12. Lessons Learned

After every incident closes:
- **Document** each step taken during the investigation
- **Identify** key aspects to review, improve, or fix
- The Blue Team should produce an **extensive report** documenting lessons learned and how they will improve defence controls

### Lessons from the Phishing Case Studies
Attacks against user credentials are a growing threat. The solution is a combination of tasks:
- **Reduce administrative accounts** — regular users should not be local admins on their own workstations
- **Use multifactor authentication (MFA)** as widely as possible
- **Restrict login rights** through security policy adjustments
- **Periodically reset the Kerberos TGT (KRBTGT) account** — this account is exploited in a **golden ticket attack**

---

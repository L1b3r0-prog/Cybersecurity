Chp 1-2
══════════════════════════════════════════════════════

## Incident Response (IR) Process
- **Detection:** how to handle security incidents
- **Response:** how to rapidly respond to them

At point 7, IR process will:
- Take over the incident case
- Document every single step of the process
- Incorporate lessons learned to enhance overall security posture

> ⚠️ Without IR process: Bad security posture + waste of human resources

### Creating a Successful IR Process
- All IT personnel trained to handle security incidents
- All users trained on core security fundamentals
- Integration between help desk system and incident response team
- Good sensors (IDS) at Network + Host level for quick detection
- IR process must comply with laws and industry regulations

---

## Fundamental Areas of IR Process

### Objective
- Clearly define the purpose of the process
- Everyone must be aware of what the process is trying to accomplish

### Scope
- Company-wide scope vs departmental scope

### Define/Terminology
- Define what constitutes a security incident with examples
- Create a glossary using clearly defined terminology

### Roles and Responsibilities
- Define users/groups with authority
- Make entire company aware

### Priorities/Severity Level
- Functional impact of incident on the business
- Type of info affected
- Recoverability
- Interaction with 3rd parties, partners and customers

---

## NIST Incident Response Lifecycle

### 1. Preparation
- Implement security controls based on initial risk assessment
- Implement endpoint protection, malware protection and network security
- Not static — receives input from post-incident activity

### 2. Detection & Analysis
- Detection system must be aware of attack vectors
- Dynamically learn about new threats and behaviours
- Triggers alert on suspicious activity
- Leverage security intelligence and advanced analytics to reduce false positives
- Detection and analysis sometimes run in parallel
- Manual info gathering required, in compliance with company policy
- Data integrity must be guaranteed to bring evidence to court
- Correlate the following to identify IoC:
  - Endpoint protection and OS logs → phishing email, lateral movement
  - Server logs and network captures → unauthorized or malicious process
  - Firewall logs and network capture → data extraction and submission

### 3. Containment
- **Short-term:** isolate portion of network under threat
- **Long-term:** temp adjustments to allow production use while rebuilding clean systems
- Restores affected systems in minimum time

### 4. Eradication
- Remove malware from all infected devices
- Acknowledge root cause and take steps to prevent similar attacks

### 5. Recovery
- Put affected production systems back online carefully
- Test, check and track affected systems to ensure normal operation

### 6. Post-Incident Activity
- **Lessons Learned** (most valuable output):
  - Full detailed timeline of incident
  - Steps taken, what happened, how it was resolved
  - Questions to answer:
    - Who identified the issue — user or detection system?
    - Was correct priority assigned?
    - Was initial assessment correct?
    - Was data analysis correct?
    - Were containment, eradication and recovery done correctly?
    - What could be improved?
    - How long did resolution take?
- **Evidence Retention:**
  - Store all artifacts per company retention policy
  - Keep evidence intact until legal actions fully settled

---

## IR Cloud Updates

| Phase | Update Required |
|-------|----------------|
| Preparation | Add cloud provider contact info and on-call process |
| Detection | Include cloud provider detection solutions |
| Containment | Use cloud provider capabilities to isolate incidents (e.g. isolate compromised VM) |

---

## 6 Phases of Threat Life Cycle Management

### Phase 1 — Forensic Data Collection
- Threats come through 7 IT domains:
  - User, Workstation, LAN, LAN-to-WAN, Remote Access, WAN, System/Application
- Collect: security event/alarm data, log/machine data, forensic sensor data

### Phase 2 — Discovery
- **Search analytics:** software-aided, reviews reports — labour intensive, not sole method
- **Machine analytics:** ML-based, autonomously scans large data, gives simplified results

### Phase 3 — Qualification
- Assess threats for: potential impact, urgency of resolution, mitigation approach
- Inefficient qualification → true positives missed, false positives included

### Phase 4 — Investigation
- Fully investigate qualified threats to determine if a security incident occurred
- Check for damage done before tools detected the threat
- Mostly automated, requires continuous forensic data access

### Phase 5 — Neutralization
- Eliminate or reduce impact of identified threat
- Automated to ensure higher throughput and easier collaboration

### Phase 6 — Recovery
- After threats neutralized and risks controlled
- Restore org to pre-attack position
- Backtrack changes made by attacker
- Use automated recovery tools to restore from backup
- Ensure no backdoors remain

---

## Cybersecurity Kill Chain (5 Steps)

### Step 1 — External Reconnaissance
- Harvest as much info as possible to find vulns
- Info gathered outside target's network:
  - Supply chain, obsolete device disposal, employee social media
- Social engineering (phishing) used to gain entry point
- Anyone in org can be targeted including suppliers and customers

### Step 2 — Compromising the System
- Entry gained through stolen passwords or malware infection
- Stolen pw → direct access to PCs, servers, devices
- Malware → infects more systems, brings them under hacker's command

### Step 3 — Lateral Movement
Scanning tools used to find exploitable loopholes:

| Category | Tools |
|----------|-------|
| Framework | Metasploit, Kali Linux |
| Network | Wireshark, Nmap, Aircrack-ng, Kismet, OWASP Zap |
| Password Cracking | John the Ripper, THC Hydra, Cain & Abel |

- **Aircrack-ng attacks:**
  - FMS: attacks RC4 encrypted keys
  - KoreK: attacks WEP encrypted WiFi
  - PTW: hacks WEP and WPA secured WiFi

### Step 4 — Privilege Escalation

#### Vertical Escalation
- Moves to account with higher auth level (admin/super user)
- Can run unauthorized code (malware & ransomware)
- Requires kernel-level operations
- Buffer overflow commonly used
- EternalBlue vuln used in WannaCry

#### Horizontal Escalation
- Uses same privilege level to access other users' accounts
- Methods: session/cookie theft, XSS, weak password guessing, keylogging
- Result: remote access entry points, access to multiple accounts, avoids detection

### Step 5 — Concluding the Mission

#### Exfiltration
- Extracts trade secrets, usernames, passwords, PII, top-secret docs
- Stolen data put up for sale
- Files on compromised systems can be erased or modified

#### Sustainment
- Attacker remains silent after exfiltration
- Rootkit malware installed to maintain access
- Security tools ineffective at this point
- Multiple access points maintained

#### Assault
- Permanently damages data and software
- Disables or alters hardware
- Example: Stuxnet attack on Iranian nuclear facility

#### Obfuscation
- Covers tracks to confuse/divert forensic investigation
- Attacks outdated servers in small orgs then moves laterally
- Uses free/public WiFi (less protected)
- Dynamic code obfuscation bypasses signature-based AV and firewalls
Chp 1-1
══════════════════════════════════════════════════════

## Goals of Cybersecurity

### Secrecy
- Effect of mechanisms used to limit number of principals who can access info
- Examples: cryptography and access control

### Confidentiality
- Obligation to protect person/org secrets if you know them

### Privacy
- Ability and/or right to protect personal info
- Extends to prevent invasions of personal space

> ⚠️ Caution: Privacy is secrecy for the benefit of the **individual**
> while Confidentiality is secrecy for the benefit of the **organisation**

---

## What is Security Posture

Solidifying protection system for org security isn't enough.
All three pillars must work together: **Detection | Protection | Response (DPR)**

### Detection
- Enhancing detection systems to quickly identify attacks

### Protection
- Implementing security controls to prevent breaches

### Response
- Enhancing effectiveness of response process
- Reduce time between infection and containment

---

## Threat Landscape
Continuously expanding as orgs allow working flexibility

### On-Premises
- Org uses its own physical infrastructure and servers within its own facilities
- Requires securing the internal network boundary directly

### Remote Access
- Using own infrastructure to access company's resources

### BYOD (Bring Your Own Device)
- Failures happen due to poor planning and network architecture
- Leads to insecure implementation

### Entry Points (based on connectivity)
1. Between On-premises and Cloud
2. Between BYOD devices and Cloud
3. Between On-premises and BYOD
4. Between Cloud and Personal devices

---

## Credentials

### Multi Factor Authentication (MFA)
- Uses multiple factors for authentication
- Example: ID/Password + One Time Password (OTP)
- OTP delivered through registered mobile number after initial authentication
- Other factors: biometric info (fingerprints, irises, face recognition)

### Continuous Monitoring
- New tech that uses a person's behaviour to continuously verify identity
- Verifies throughout a session, not just at entry point

### Security Considerations for Apps
- **In-house apps:** ensure apps use secure framework throughout SW dev lifecycle
- **Paid service apps:** check vendor security and compliance policy against company requirements

---

## Cybersecurity Challenges

### Top Causes of Breaches
1. Malware (viruses and trojans)
2. Lack of diligence and untrained employees
3. Phishing and social engineering
4. Targeted attack
5. Ransomware
6. Government-sponsored attack

### Causes 1, 2, 3 — Human Error
- May start with phishing email using social engineering
- Tricks employee to download virus, malware or trojan

### Cause 4 — Targeted Attack
- Attacker has specific target in mind
- Spends lots of time and resources on public reconnaissance
- Key attribute: **longevity** — maintains persistent access and moves laterally

### Cause 5 — Ransomware
- Companies failing to implement effective vulnerability management programs

### Cause 6 — Government-Sponsored Attack
- Intent to steal info to be used against another party
- Private sector shouldn't ignore these signs
- Orgs invest more into threat intelligence, ML and analytics

---

## Red and Blue Team

### Red Team
- Performs attacks and pen tests the environment against current security controls
- Composed of highly trained individuals with different skill sets
- Must be aware of current threat landscape and trends
- Must have coding skills to create and customize their own exploits

### Blue Team
- Ensures assets are secure
- If Red Team finds and exploits a vuln, Blue Team must rapidly remediate and document it

---

## Performance Metrics

### Red Team Metrics
| Metric | Description |
|--------|-------------|
| MTTC (Mean Time to Compromise) | From attack initiation to successful compromise |
| MTPE (Mean Time to Escalate) | From attack initiation to full admin privilege on target |

### Blue Team Metrics
| Metric | Description |
|--------|-------------|
| ETTD (Estimated Time to Detection) | Time taken to detect the attack |
| ETTR (Estimated Time to Recovery) | Time taken to recover from attack |

### Blue Team Response Steps
1. **Save evidence** — ensure tangible info to analyse and act on
2. **Validate the evidence** — catalogue valid attempts as Indication of Compromise (IoC)
3. **Engage necessary teams** — know what to do with IoC and who to inform
4. **Triage incident** — may involve law enforcement or warrants
5. **Scope the breach** — determine full extent of compromise
6. **Create remediation plan** — plan to isolate or evict adversary
7. **Execute and recover**
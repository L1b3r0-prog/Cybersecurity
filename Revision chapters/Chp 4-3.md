## Traditional Defender Mindset vs New Mindset

### Traditional Defender Mindset
- Focuses mainly on monitoring:
  - High-profile users
  - Administrators
  - Privileged accounts
- Relies heavily on:
  - Signature detection
  - Static rules
  - Manual investigation
- Problems:
  - High number of false positives
  - Limited visibility across regular users
  - Difficulty detecting modern attacks that stay hidden

---

### New Defender Mindset
Modern security monitoring focuses on **all users and devices**, not just privileged accounts.

### Key Concepts
- Profile normal user behavior
- Monitor:
  - All accounts
  - All devices
  - Multiple locations
- Detect:
  - Lateral movement
  - Dormant attackers
  - Privilege escalation
  - Insider threats

### Modern Detection Techniques
- Data correlation
- Profiling
- Behavior analytics
- Anomaly detection
- Activity evaluation
- Machine learning

### Why This Is Important
Attackers often:
1. Compromise regular users first
2. Stay hidden in the network
3. Move laterally
4. Escalate privileges later

---

# Indicator of Compromise (IoC)

## Definition
An **Indicator of Compromise (IoC)** is evidence or an artifact showing that a system or network may have been breached.

Examples:
- Malicious IP addresses
- Suspicious files
- Unusual traffic patterns
- Abnormal user activity

### Purpose of IoCs
- Detect attacks early
- Identify attacker behavior
- Prevent or limit damage
- Improve incident response speed

---

# Major IoCs

## 1. Unusual Outbound Traffic
- Systems communicating with unknown external servers
- May indicate:
  - Command-and-Control (C&C) communication
  - Data exfiltration

### Example
- A workstation suddenly sends encrypted traffic to unknown overseas IPs.

---

## 2. Anomalies in Privileged User Activity
Changes in:
- Login times
- Systems accessed
- Volume of data accessed
- User behavior patterns

### Example
- Admin account accessing systems at 3 AM unexpectedly.

---

## 3. Geographical Irregularities
Login attempts or access from unusual countries or locations.

### Example
- Employee account logs in from Singapore and then Russia shortly after.

---

## 4. Login Red Flags
Indicators include:
- Multiple failed logins
- After-hours access
- Sudden successful login after repeated failures

### Possible Meaning
- Brute force attack
- Credential stuffing
- Unauthorized access attempt

---

## 5. Sudden Increase in Database Read Volume
Large amounts of database reads may indicate:
- Data harvesting
- Data exfiltration attempts

### Example
- Massive download of customer records.

---

## 6. Large Number of Requests for the Same File
Repeated requests may indicate:
- Exploit attempts
- Vulnerability scanning

### Example
- 500 requests to `join.php` from one IP address.

---

## 7. Mismatched Port-Application Traffic
Applications using incorrect ports suspiciously.

### Example
- DNS traffic running over port 80 instead of port 53.

---

## 8. DNS Request Anomalies
Indicators:
- Sudden spike in DNS requests
- Repeated requests to suspicious domains

### Possible Meaning
- Malware beaconing
- C&C communication

---

## 9. Suspicious Registry or System File Changes
Attackers modify:
- Registry entries
- Critical system files

### Goal
- Persistence
- Privilege escalation

---

## 10. Mobile Device Profile Changes
Unexpected configuration profiles may indicate compromise.

### Example
- Malicious profile installed through phishing.

---

## 11. Wrong Placement of Data
Sensitive data stored in unusual locations.

### Example
- Files hidden inside recycle bin folders.

---

## 12. Web Traffic with Unhuman Behavior
Indicators:
- Extremely high browsing activity
- Automated browsing patterns

### Example
- 40 browser tabs opening automatically.

---

# Host-Based IDS (HIDS) vs Network-Based IDS (NIDS)

| Feature | HIDS | NIDS |
|---|---|---|
| Location | Installed on individual hosts | Installed on network segments |
| Monitors | Single device activity | Entire network traffic |
| Focus | File changes, logs, host behavior | Packets and network traffic |
| Scope | Local system only | Multiple devices |
| Advantage | Deep visibility into host | Broad network visibility |
| Limitation | Only protects one device | Cannot see encrypted host activity well |

---

## Host-Based IDS (HIDS)

### Characteristics
- Runs directly on hosts/devices
- Monitors:
  - System files
  - Logs
  - Inbound/outbound traffic
- Compares system snapshots for changes

### Example Use Cases
- Critical servers
- Mission-critical systems

### Strength
- Detects unauthorized file modifications

---

## Network-Based IDS (NIDS)

### Characteristics
- Monitors network traffic
- Positioned strategically in the network
- Detects:
  - Known attacks
  - Suspicious traffic patterns

### Important Placement Areas
- DMZ
- Core network
- Wireless networks
- Virtualization networks

### Strength
- Monitors multiple systems simultaneously

---

# Signature-Based IDS vs Behavior-Based IDS

| Feature | Signature-Based IDS | Behavior-Based IDS |
|---|---|---|
| Detection Method | Known attack signatures | Detects abnormal behavior |
| Best At | Known threats | Unknown threats |
| Requires Updates | Yes | Baseline training |
| False Positives | Lower | Higher |
| Can Detect Zero-Day Attacks | No | Yes |

---

## Signature-Based IDS

### How It Works
- Compares activity against:
  - Known malware signatures
  - Known attack patterns

### Advantages
- Accurate for known threats
- Fast detection

### Disadvantages
- Cannot detect unknown attacks
- Requires constant updates

---

## Behavior-Based IDS (Anomaly-Based IDS)

### How It Works
- Builds a baseline of normal behavior
- Detects deviations from that baseline

### Uses
- Machine learning
- Statistical analysis

### Advantages
- Detects:
  - Zero-day attacks
  - Unknown malware
  - Insider threats

### Disadvantages
- Higher false positives
- Requires learning period

---

# IDS vs IPS

| Feature | IDS | IPS |
|---|---|---|
| Main Function | Detects attacks | Detects and blocks attacks |
| Action Taken | Generates alerts | Automatically prevents threats |
| Traffic Position | Passive monitoring | Inline with traffic |
| Risk | Less disruptive | May accidentally block valid traffic |

---

## Intrusion Detection System (IDS)

### Purpose
- Detect suspicious activity
- Alert administrators

### Does NOT
- Automatically stop attacks

### Main Role
- Monitoring and alerting

---

## Intrusion Prevention System (IPS)

### Purpose
- Detect and prevent attacks

### Actions IPS Can Take
- Block traffic
- Drop malicious packets
- Terminate sessions
- Prevent exploitation attempts

### Types
- HIPS (Host-based IPS)
- NIPS (Network-based IPS)

---

# Anomaly-Based IPS

## Definition
An IPS that:
1. Learns normal traffic behavior
2. Detects deviations
3. Automatically takes action

---

## How It Works
- Collects traffic samples
- Builds behavior baseline
- Compares future activity against baseline

### If Activity Is Abnormal
- Generate alert
- Block traffic
- Trigger security response

---

## Advantages
- Detects unknown attacks
- Detects insider threats
- Identifies suspicious patterns early

---

## Disadvantages
- Higher false positives
- Requires training period
- Complex tuning

---

# Behavior Analytics

## Definition
Behavior analytics studies user and system behavior to identify suspicious activities.

### Goal
Detect:
- Insider threats
- Advanced Persistent Threats (APTs)
- Financial fraud
- Compromised accounts

---

# User and Entity Behavior Analytics (UEBA)

## Definition
UEBA tracks normal behavior of:
- Users
- Devices
- Systems
- Applications

Then detects anomalies.

---

## Example
Normal behavior:
- User downloads 10 MB daily

Anomaly:
- Same user suddenly downloads 5 GB

Result:
- UEBA triggers alert

---

## Advantages of UEBA
- Early attack detection
- Detects insider threats
- Detects compromised accounts
- Uses machine learning and analytics

---

# Importance of Behavior Analytics

## Why Organizations Use It
Attackers often:
- Stay hidden
- Move laterally
- Escalate privileges quietly

Behavior analytics helps detect:
- Suspicious patterns
- Abnormal actions
- Reconnaissance activities

---

# Example: Credit Card Fraud Analogy

Behavior analytics works similarly to bank fraud detection systems.

### Example
If your credit card:
- Is used in a new country
- Spends unusually high amounts
- Behaves differently

The bank:
- Detects anomaly
- Flags transaction
- Contacts user

Cybersecurity systems do the same with user activity.

---

# Key Takeaways

- Modern defense requires monitoring all users and devices
- IoCs help identify compromise early
- HIDS protects hosts while NIDS protects network segments
- Signature-based systems detect known threats
- Behavior-based systems detect unknown threats
- IDS detects attacks while IPS blocks attacks
- Behavior analytics and UEBA are critical against modern stealth attacks
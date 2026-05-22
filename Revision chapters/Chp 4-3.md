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

### New Defender Mindset
- Focuses on everything
  - All users
  - All devices
  - All accounts
- Relies on
  - Data correlation
  - Profiling
  - Behaviour analytics
  - Anomaly detection
  - Activity evaluation
  - Machine learning
- Detects
  - Lateral movement
  - Dormant attackers
  - Privilege escalation
  - Insider threats

This Shift is due to how attackers start
- First by compromising regular users first
- Staying hidden in the network
- Moving laterally
- Escalating privileges

Traditional mindeset focuses on privileged accounts only which would miss this entirely

---

# Indicator of Compromise (IoC)

## Definition
An Indicator of Compromise (IoC) is an artifact that is observed on a network or in an OS that indicates a computer intrusion with high confidence

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

## Host-Based IDS (HIDS)

### Characteristics
- Runs on individual hosts/devices
- Monitors inbound and outbound packets from device only
  - Will alert User/Admin if suspicious activity is detected
- Takes and compares system snapshots for changes
  - If critical system files were modified/deleted, alert is sent to admin

### Example Use Cases
- Critical servers
- Mission-critical systems

### Strength
- Detects unauthorized file modifications

## Network-Based IDS (NIDS)

### Characteristics
- Monitors network traffic for the network segment it is installed in
- Positioned at strategic point or points in the network
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

## HIDS vs NIDS
| Feature | HIDS | NIDS |
|---|---|---|
| Location | Installed on individual hosts | Installed on network segments |
| Monitors | Single device activity | Entire network traffic |
| Focus | File changes, logs, host behavior | Packets and network traffic |
| Scope | Local system only | Multiple devices |
| Advantage | Deep visibility into host | Broad network visibility |
| Limitation | Only protects one device | Cannot see encrypted host activity well |
| Best use cases | Critical servers, mission-critical systems | DMZ, core network, wireless networks, virtualization networks |
| Key strength | Detects unauthorized file modifications | Monitors multiple systems simultaneously |


---

# Signature-Based IDS vs Behavior-Based IDS

## Signature-Based IDS

### How It Works
Queries database of previous attack's signature (footprint) such as 
- Byte sequences in network traffic
- Known malicious instruction sequences

Then it decides whether an alert must be triggered

Used for identifying known threats

Database however requires constant update in order to have the latest version

---

## Behavior-Based IDS (Anomaly-Based IDS)

### How It Works
Creates a baseline model of trustworthy activity through machine learning and then comparing new behaviour against the model

Introduced to detect unknown attacks due to rapid dev of malware

May suffer from false positives due to prev unknown legit activity which may be classified as malicious

### Two major anomaly-based IDS
- User and Entity Behaviour Analytics (UEBA)
- Network Traffic Analysis (NTA)

## SBIDS vs BBIDS

| Feature | Signature-Based IDS | Behavior-Based IDS |
|---|---|---|
| Detection Method | Known attack signatures | Detects abnormal behavior |
| Best At | Known threats | Unknown threats |
| Requires Updates | Yes | Baseline training |
| False Positives | Lower | Higher |
| Can Detect Zero-Day Attacks | No | Yes |

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

# IDS and IPS

## Intrusion Detection System (IDS)
Monitors network or system for malicious activity or policy violations and triggers and alert

Requires help from humans for automated system to interpret results and decide whether to act

## Intrusion Prevention System (IPS)

Uses the same concept of IDS but prevents intrusion by taking corrective action

Primarily focused on identifying possible incidents, logging info on them and reporting attempts

Orgs can use for other purposes
- Identifying problems with security policies
- Documenting existing threats
- Deterring individuals from violating security policies

### Actions IPS Can Take
- Block traffic
- Drop malicious packets
- Terminate sessions
- Prevent exploitation attempts

### Types
- HIPS (Host-based IPS)
- NIPS (Network-based IPS)

## IDS vs IPS

| Feature | IDS | IPS |
|---|---|---|
| Main Function | Detects and monitors intrusions | Detects and prevents intrusions |
| Action Taken | Generates alerts only | Automatically takes corrective action |
| Response | Needs human or automated system to act | Acts on its own |
| Risk | Less disruptive | May accidentally block valid traffic |
| Types | HIDS, NIDS | HIPS, NIPS |
| Detection Modes | Signature-based, Behavior-based | Rule-based, Anomaly-based |
| **Shared** | Both analyze traffic and compare it to known threats ||

---

# Anomaly-Based IPS

An extension of anomaly based IDS that:
1. Learns normal traffic behavior
2. Detects deviations
3. Automatically takes action

Depends on what the IPS categorizes as anomalous

Takes samples of network traffic at random times, performs comparison with baseline
- If samples fits outside of baselines, alert and action is taken

User behavior analytics plays an important role

---

# Behavior Analytics

## Definition
Behavior analytics studies user and system behavior to identify suspicious activities.

Looks at patterns of human behaviours and then applying algorithms and statistical analytics to detect meaningful anomalies from those patterns
- This is to find anomalies that indicate potential threats

Instead of tracking devices or security events, it tracks system's users

---

# User and Entity Behavior Analytics (UEBA)

## Definition
UEBA tracks normal behavior of:
- Users
- Devices
- Systems
- Applications

Then detects anomalies.

## Example
Normal behavior:
- User downloads 10 MB daily

Anomaly:
- Same user suddenly downloads 5 GB

Result:
- UEBA triggers alert

## Advantages of UEBA
- Early attack detection
- Detects insider threats
- Detects compromised accounts
- Uses machine learning and analytics

Placement of UEBA is according to company's needs and vendor's requirements

---

# Importance of Behavior Analytics

Stuff like core business, critical data and key assets are located on-premises

## Why Organizations Use It
Attackers often infiltrate on-premises networks by:
- Staying hidden
- Moving laterally
- Escalate privileges quietly
- Maintain command and control until mission is executed

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
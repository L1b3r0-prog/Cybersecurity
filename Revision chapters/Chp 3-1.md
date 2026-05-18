Chp 3-1
══════════════════════════════════════════════════════

## Malware Classification
Malware is a program inserted into a system, usually covertly, with the intent of
compromising **confidentiality, integrity or availability** of victim's data, applications or OS

**Malware carries out:**
- Nation-state cyberwar
- Cybercrime
- Fraud
- Scam

---

## Types of Malware
- Virus
- Worms
- Trojans
- Spyware
- Botnet Malware
- Ransomware

### Classification Categories

| Category | Group A | Group B |
|----------|---------|---------|
| Needs host program | Viruses | Worms & Bots (standalone) |
| Can replicate | Viruses & Worms | Trojans & Spam emails (cannot) |
| Payload type | Corruption of files | Theft of service / Theft of info |

---

## Virus
Piece of software that infects other programs or executable content by modifying them
**Requires a host program or file to execute**

### Main Components
| Component | Description |
|-----------|-------------|
| Infection mechanism | How virus spreads/propagates (infection vector) |
| Trigger | Event/condition that activates/deactivates payload (logic bomb) |
| Payload | What virus does beyond spreading — damage or noticeable activity |

### Virus Phases
| Phase | Description |
|-------|-------------|
| Dormant | Idle, waiting for trigger |
| Propagation | Places copy of itself into other programs or disk areas |
| Triggering | Activated to perform intended function |
| Execution | Function is performed |

### Classification of Virus

**By Target:**
| Type | Description |
|------|-------------|
| Boot sector infector | Infects master boot record — spreads when system boots from infected disk |
| File infector | Infects executable files |
| Macro virus | Infects files with macro/scripting code interpreted by an application |
| Multipartite virus | Infects files in multiple ways across multiple file types |

**By Concealment Strategy:**
| Type | Description |
|------|-------------|
| Stealth | Hides entire virus (not just payload) from antivirus detection |
| Encrypted | Uses encryption to obscure content |
| Polymorphic | Changes form each time it is inserted into another program |
| Metamorphic | Higher order — changes form AND can be completely rewritten |

---

## Worms
Self-propagating program that replicates across systems by arranging to execute itself immediately

- Exploits software vulnerabilities in client/server programs
- **Standalone — does not need a host program**

### Replication Methods
| Method | Description |
|--------|-------------|
| Email/IM | Emails copy of itself or sends as attachment |
| File sharing | Copies itself or infects files on removable media (e.g. USB) |
| Remote execution | Executes copy on another system via remote facility or exploiting network service flaw |
| Remote file transfer | Copies itself using remote file access/transfer services |
| Remote login | Logs onto remote system as user and copies itself |

### Worm vs Virus Propagation
| | Worm | Virus |
|-|------|-------|
| Speed | Faster — parallelizes propagation | Slower — requires user action to trigger each propagation |
| Host needed | No | Yes |

---

## Trojan Horse
Software that appears to perform a desirable function but secretly performs malicious functions
**Does not self-replicate**

### Concealment Methods
- Renames itself to the name of a valid system file
- Can be encrypted and polymorphic
- Installs itself in different ways to escape detection

---

## Backdoor
Secret entry point allowing access without going through normal security procedures

- Originally used by programmers to debug and test programs
- Can be exploited for unauthorized access
- Usually implemented as a **network service listening on a non-standard port**
- Attacker connects and issues commands to be run on the compromised system
- Difficult to implement OS controls for backdoors in applications

---

## Ransomware
Attacks **availability** of data by encrypting files and demanding payment for the decryption key

---

## Extras

### Potentially Unwanted Programs (PUP)
- Code that is part of a useful program but collects user data without consent
- Sits in legal grey area but considered malware from a cybersecurity standpoint

### Logic Bomb
- Performs malicious action when a specific external event occurs
- **Triggers include:**
  - Presence or absence of certain files/devices
  - Particular day/date
  - Particular software version or config
  - Particular user running the app
- Once triggered: may alter/delete data, cause machine damage

---

## Countermeasures for Malware

### How Malware Works
- Acts as both **data and instructions**
  - Inserts code (instructions) into another program
  - Executes itself where the instructions are treated as executable
- **Protection:** treat all programs as data by default
  - Only allow execution after trusted certifying authority verifies them

### Against Malicious Code Assuming User Identity
- Limit objects accessible to a process run by the user
  - Reduce rights
  - **Sandboxing** — virtual environment to contain malicious behaviour

### Restrict Domain Sharing
- Prevent users in different protection domains from sharing programs or data

---

## Detection Methods

| Method | How It Works | Strength | Weakness |
|--------|-------------|----------|---------|
| Behaviour monitoring | Monitors system for abnormal behaviour | Works for all viruses, detects before full infection | High sensitivity → many false alarms |
| Signature scanning | Matches activity against known virus signature library | Simple and effective for known threats | Cannot detect new viruses or polymorphic viruses |
Chp 2-2
══════════════════════════════════════════════════════

## Lateral Movement
Attackers move from device to device after initial intrusion to access high-value data

- Looks for ways to gain additional control of victim's network
- Tries not to trigger alarms or raise alerts
- Carried out within org network, systems and premises
- Can take up to **several months** before reaching desired target
- Involves: scanning for resources, collecting/exploiting credentials, gathering info for exfiltration

---

## Sniffing Tools

| Tool | Description |
|------|-------------|
| Wireshark | Most popular — captures and interprets packets |
| Tcpdump | Powerful packet-filtering, selective capture |
| Nmap | Network mapping and host discovery |
| Nessus | Vulnerability scanner |

---

## Nmap (Network Mapper)
Uses raw IP packets to determine network information

**Basic command:** `nmap <option> <target IP>`

### What Nmap Can Determine
- Hosts available on network
- Services (application name and version) hosts are offering
- OS and versions running
- Type of packet filters/firewalls in use

### Scan Types
| Option | Scan Type |
|--------|-----------|
| `-sS` | TCP SYN scan |
| `-sU` | UDP scan |

**Scan outputs:** open, closed, filtered, unfiltered or combination

### Timing Options (-T)
| Level | Name |
|-------|------|
| 0 | Paranoid |
| 1 | Sneaky |
| 2 | Polite |
| 3 | Normal |
| 4 | Aggressive |
| 5 | Insane |

### Port Specification
| Option | Description |
|--------|-------------|
| Default | Most common 1000 ports in random order |
| `-p <range>` | Scans only defined ports |
| `-F` | Only 100 most common ports |
| `-r` | Don't randomize port numbers |
| `--top-ports N` | Scans most common N ports |

### Nmap Script Categories
`nmap --script <script name> <target url or ip>`

| Script | Purpose |
|--------|---------|
| auth | Test if authentication mechanism can be bypassed |
| broadcast | Find other hosts and add to scanning queue |
| brute | Brute force password guessing |
| discovery | Discover more about the network |
| dos | Test if target is vulnerable to DoS |
| exploit | Actively exploit a vulnerability |
| fuzzer | Test server response to unexpected/random packet fields |
| intrusive | More intense scans — higher risk of detection |
| malware | Test target for presence of malware |
| safe | General scan — less likely to alarm admins |
| vuln | Find vulnerabilities on target |

---

## NIDS vs HIDS

| Feature | NIDS | HIDS |
|---------|------|------|
| Scope | Network-wide | Individual host |
| Capability | Limited when scanning individual targets | Can prevent scans from happening |
| Consideration | Default choice for most admins | Often overlooked if number of hosts is large |

> ⚠️ Legitimate tools can be used for lateral movement — security systems ignore them,
> allowing hackers to move around in highly secured networks (powershell)

---

## Sysinternals
Suite of tools allowing admins to control Windows-based PCs from a remote terminal

**Attacker use:**
- Upload, execute and interact with executables on remote hosts
- Can be automated using scripts

**Why it's dangerous:**
- Does NOT give alerts to users on remote system during operation
- Classified as legitimate system admin tools → ignored by antivirus
- Can reveal info about running processes, kill or stop services

---

## Active Directory (AD)
Richest source of info for devices connected to a domain network — **key attack target**

- Stores names of users alongside their roles in the org
- Allows admins to change passwords and privileges

---

## Privilege Escalation
Exploiting a bug, design flaw or config oversight in OS/software to gain elevated access
to resources normally protected from app or user

**Goals of privilege escalation:**
- Mass deletion
- Data corruption
- Theft of data
- Disabling PCs
- Destroying hardware

---

## Horizontal Privilege Escalation
Attacker uses normal account to access accounts of other users at the **same privilege level**

### Two Main Ways
| Method | Description |
|--------|-------------|
| Software bugs | User can view/access other users' files due to coding error |
| Admin account | Attacker creates additional admin-level users |

**Common techniques:**
- Session and cookie theft
- Cross-site scripting
- Guessing weak passwords
- Logging keystrokes

**Result:**
- Well-established remote access entry points
- Access to multiple user accounts
- Knows how to avoid detection

---

## Vertical Privilege Escalation
User/process obtains higher access than admin or developer intended

- More difficult but more rewarding
- Attacker acquires system/super-user rights
- Higher chance of remaining undetected with super user rights

### Platform Differences
| Platform | Common Method |
|----------|--------------|
| Windows | Buffer overflows |
| Mac | Jailbreaking |
| Web-based | Exploitation of backend code |

> ⚠️ Attacker should avoid triggering alerts — normal to disable security systems
> before escalating, or use legitimate tools

### Vertical Escalation Methods

#### Valid Admin Account
- Gains unauthorized access to admin account
- Logs into sensitive systems or creates own credentials
- Exploits programming errors to bypass security mechanisms
- Some systems accept certain phrases as universal passwords

#### Access Token Manipulation
- Windows uses access tokens to determine process owners
- OS logs admin as normal user but executes processes with admin privileges
- Attacker copies access tokens from admin-started processes to new processes
  using built-in Windows API functions
- Result: processes run with full admin privileges undetected

#### Application Shimming
- Windows Application Compatibility Framework
- **Normal operation:**
  - Creates a shim to buffer between legacy program and OS
  - Shim cache checked during program execution
  - Shim DB uses API to redirect program code
  - Shims run in user mode for safety
- **Attacker use:**
  - Creates custom shims that bypass UAC
  - Injects DLL into running processes
  - Meddles with memory addresses
  - Runs malicious programs with elevated privileges
  - Can disable security software (e.g. Windows Defender)

#### DLL Attacks
**DLL (Dynamic-Link Library):** shared library allowing devs to share code/data
without re-linking apps. Apple equivalent: **Dylib**

| Attack Type | Description |
|-------------|-------------|
| DLL Injection | Runs malicious code using legitimate Windows processes/services to mask attacker's actions |
| Reflective DLL Injection | Loads malicious code without Windows API calls — bypasses monitoring, hard to detect |
| DLL Search Order Hijacking | Replaces legitimate DLL with malicious one — Windows loads fake DLL first |

**DLL Injection sequence:**
Attach malicious code → Access memory → Copy malicious DLL to memory → Execute with legitimate processes

**Real-world examples:**
| Malware | Injection Target |
|---------|----------------|
| Backdoor.Oldrea | explorer.exe |
| BlackEnergy | svchost.exe |
| Duqu | Multiple processes to avoid detection |

---

## Concluding the Mission

### Exfiltration
- Extracts huge chunks of sensitive data
- Includes: trade secrets, usernames, passwords, PII, top-secret docs
- Data put on sale for interested buyers
- Files on compromised systems can be erased or modified

### Sustainment
- Attacker remains silent after exfiltration
- Rootkit malware installed to maintain access
- Security tools ineffective at this point
- Multiple access points maintained — closing one doesn't stop attacker

### Assault
- Most feared stage — permanently damages data and software
- Disables or alters victim's hardware
- Example: **Stuxnet** attack on Iranian nuclear facility
  - First recorded digital weapon used to damage physical resources
  - Transmitted via USB thumb drive

### Obfuscation
- Attacker covers tracks to confuse/divert forensic investigation
- Attacks outdated servers in small orgs then moves laterally to other targets
- Uses public/free WiFi (less protected, harder to trace)
- **Dynamic code obfuscation:** prevents detection by signature-based AV and firewalls

---

## Stuxnet and Flame

### Stuxnet — 3 Attack Phases
1. Targets Windows PCs and network by replicating itself repeatedly
2. Seeks out **Siemens Step7 software** used to program industrial control systems
3. Compromises the **Programmable Logic Controllers (PLCs)**

### Stuxnet Steps
| Step | Action |
|------|--------|
| 1 | Infection |
| 2 | Search |
| 3 | Update |
| 4 | Compromise |
| 5 | Control |
| 6 | Deceive and Destroy |

### Flame
- Precursor to Stuxnet — sophisticated worm
- Data sent off in smaller chunks
- Can exchange data with any **Bluetooth-enabled device**
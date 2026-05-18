Chp 2-1
══════════════════════════════════════════════════════

## Steps for Compromising a System
1. Deploying payload
2. Compromise OS
3. Compromise web-based system

> Steps will vary according to attacker's mission

---

## Deploying Payloads

### Metasploit
- Collection of exploits and payloads used against identified vulnerabilities
- Vulnerabilities identified beforehand using tools like Nessus Scanner
- Framework console booted by running `msfconsole` in terminal
- Payload set up using command with IP address of target
- Payload generated using `msfvenom` command
  - Creates backdoor payloads such as Windows command shell or reverse TCP stager
  - Backdoors can be distributed via phishing emails

### Exploiting Vulnerabilities
- Errors in authentication code
- Bugs within account management system
- Unforeseen errors by developers

---

## Zero-Day Vulnerabilities
Uses advanced vuln discovery tools to identify vulns not yet known by software developers

### Discovery Methods

| Method | Description | Notes |
|--------|-------------|-------|
| Fuzzing | Automated testing using invalid/unexpected/random inputs | Often inefficient for large programs |
| Source Code Analysis | Manual/automated review of code | Simpler but lower success rate |
| Reverse Engineering | Generates assembly language source from machine-executable code | — |

**Fuzzing:**
- Refers to a system created by hacker to attempt to find vulns
- Tools: automated software testing frameworks

**Source Code Analysis:**
- Uses automated tools such as **Checkmarx**
  - Scans code, identifies, categorizes and suggests countermeasures for vulns

---

## Zero-Day Exploits

### Buffer Overflow
- Caused by incorrect logic that writes data to buffer memory without observing memory restrictions
- Writing data past the limit will crash the system
- Commonly used for **vertical privilege escalation**

### Structured Exception Handler (SEH) Overwrite
- Hackers attack SEH logic causing it to correct non-existent errors
- Leads system to shutdown
- Sometimes used in combination with buffer overflows

---

## Compromising the OS

### Insider Threats
- People working inside orgs with malicious intent
- Have advantage of knowing the inside of the org and where to attack
- Physically close to target machine when user is unattended

**Tools used for physical access attacks:**
| Tool | Purpose |
|------|---------|
| Kon-Boot | Bypasses Windows login |
| Hiren's BootCD | Multi-purpose boot toolkit |
| Ophcrack | Password cracker using rainbow tables |
| Linux Live CD | Boots directly into Linux to access files |

### Compromising with Live CD
- Boots target PC from DVD/USB containing Linux image
- Enables direct access to all files on Windows PC
- Unless hard disk is encrypted, all user files visible in plain text

### Compromising with Preinstalled Apps
- Aims to compromise Windows programs
- Modifies commonly used apps so when user runs them, malicious actions are performed instead

---

## Compromising Web-Based Systems
Contains highly valuable and sensitive data

### Attack Methods

#### SQL Injection
- Targets backend execution of user inputs on PHP/SQL websites
- Attacker supplies inputs that manipulate SQL statement execution
- Exposes and compromises the underlying database

#### Cross-Site Scripting (XSS)
- Exploits unsanitized input fields
- Used to steal cookies, sessions and display alert boxes
- **Stored XSS:** hacker stores malicious script in HTML/DB, executed when user loads page

#### Broken Authentication
- Captures or bypasses authentication methods
- Common on publicly shared PCs
- Websites store session cookies but don't delete them when user closes browser without logging out

#### DDoS Attacks
- Main aim: bring down a server
- Or create a diversion to commit another malicious act (e.g. stealing data)

---

## Chasing a User's Identity

### Identity is the New Perimeter
- Traditional network perimeter is no longer sufficient as security boundary
- Majority of credentials are just username and password
- MFA is not the default authentication method

### Growing Trends of Credential Theft
- Hackers infiltrate silently using valid credentials to authenticate to the network
- Target user's banking credentials using banking trojans

### BYOD Risk
- Personal app identity resides on the same device as corporate credentials
- Users may reuse the same password for different tasks

---

## Hash Function
A mathematical algorithm that takes any input data (message) and converts it into a
fixed-size output called a **hash value / digest / message digest**

### Key Properties
| Property | Description |
|----------|-------------|
| Easy to compute | Fast to generate hash from input |
| Hard to invert | Cannot reverse hash back to original input |
| Collision-resilience | Two different inputs should not produce the same hash |

### Uses
- Storing passwords
- Data integrity verification
- Efficiency
- Proof of work

---

## Strategies for Compromising a User's Identity
Attack plan considers current threat landscape across 3 stages:

### Stage 1 — Who Can Attack Us
- Red team performs self-assessment
- Understands what type of info the company has and who benefits from obtaining it
- Creates a basic adversary profile for Stage 2

### Stage 2 — What Are the Most Common Attacks
- Many hacker groups have a pattern
- Understanding attack categories allows the red team to emulate them during exercises

### Stage 3 — How the Attacks Are Executed
- Red team emulates hacker's mindset
- Attacker won't stop after first failed attempt
- Will retry using different techniques until successful

---

## Harvesting Credentials

### Using Unpatched Vulnerabilities
- Example: **CVE-2017-8563**
  - Elevation of privilege vuln due to Kerberos authentication failure
  - Attacker potentially gains local admin access through lateral movement

### Pass-the-Hash Attack
- Uses hashed password directly instead of cracking it
- Tools:
  - **Mimikatz** — dumps hashes and plaintext credentials from memory
  - **Sysinternals** — remotely accesses Windows and executes commands

### Brute Force
- Attacker tries many passwords/passphrases hoping to eventually guess correctly

### Social Engineering
- Uses Social Engineering Toolkit in Kali Linux
- Crafts and distributes malware via email
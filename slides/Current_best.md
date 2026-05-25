# CSIT302 CYBERSECURITY

Complete Study Notes

> *All lecture topics and Past Year Paper traps are combined into one document. Red boxes = exam traps. Yellow boxes = exam tips.*

---

# MODULE 1: CYBERSECURITY BASICS & SECURITY POSTURE

## 1.1 Key Definitions

| Term | Definition |
|------|------------|
| **Cybersecurity** | Keeping computers, networks, and data safe from attacks and damage. It covers computer security, network security, and software/hardware security. |
| **CIA Triad** | The three main goals of cybersecurity: Confidentiality, Integrity, and Availability. |

| CIA Property | Simple Meaning + Example |
|---|---|
| **Confidentiality** | Only the right people can see the information. Example: Encryption stops others from reading your files. |
| **Integrity** | The information is correct and has not been changed by someone else. Example: A checksum check shows if a file was changed. |
| **Availability** | The right people can always access the system or data when they need it. Example: Stopping a DDoS attack keeps a website running. |
| **Privacy** | Keeping personal information secret — for the benefit of the PERSON. Different from Confidentiality, which protects the ORGANISATION. |

> **Exam Tip:** Confidentiality = protects the organisation. Privacy = protects the individual. Do not mix these up!

---

## 1.2 Security Posture

Security posture = how strong an organisation's cybersecurity is. It has three parts:

- **Protection** — controls that stop attacks from happening
- **Detection** — tools that notice when an attack is happening
- **Response** — actions taken after an attack is found

**Important:** Having only a strong PROTECTION system is NOT enough. Detection and Response must also be in place. All three must work together.

> *Example: A firewall = Protection. An IDS = Detection. The Incident Response Plan = Response.*

---

## 1.3 The Threat Landscape

The threat landscape is growing because many organisations allow remote access and BYOD. There are 4 main entry points to consider for security:

- Between On-premises systems and the Cloud
- Between BYOD devices and the Cloud
- Between On-premises systems and BYOD devices
- Between the Cloud and Personal Devices

Security considerations for apps:

- **Apps developed in-house** — the organisation must make sure the app uses a secure framework throughout the entire software development lifecycle
- **Apps users are paying for as a service (SaaS)** — the organisation must carefully check the vendor's security and compliance policy to make sure it meets the company's own security requirements

> **Caution:** If an organisation extends to IaaS or PaaS, they must do a risk assessment to evaluate the new threats created by that connection and put the right countermeasures in place.

---

## 1.4 The Credential — Identity Is the New Perimeter

The old idea was that a firewall at the network border keeps attackers out. This is no longer enough. Today, a user's IDENTITY (login credentials) is the new security boundary. If an attacker steals credentials, they log in like a real user and move freely.

- Credential theft is the most common first step in a cyber attack
- Stealing credentials can give the attacker a path to escalate privileges all the way to domain administrator
- 63% of confirmed data breaches happen because of weak, default, or stolen passwords (Verizon 2016 DBIR)
- Most logins still only use username and password — MFA is not yet the standard everywhere

| Term | Definition |
|------|------------|
| **MFA (Multi-Factor Authentication)** | Using more than one method to verify identity at login. Even if your password is stolen, the attacker still needs the second factor to get in. |

MFA factor types:

- **Something you KNOW** — password, PIN
- **Something you HAVE** — phone (one-time SMS password), hardware token
- **Something you ARE** — biometrics: fingerprint, iris scan, face recognition, voice

*Example: The Australian government site my.gov.au uses: password PLUS a one-time password sent to your registered phone.*

| Term | Definition |
|------|------------|
| **Continuous Monitoring (Continuous Authentication)** | A newer technology that keeps checking your identity throughout your whole session — not just at the login screen. It watches your behaviour (e.g., typing speed) to make sure you are still the real user. |

### SIM Swap Attack — How MFA Can Be Broken

MFA is much better than just a password but is NOT bulletproof. The SIM Swap attack breaks SMS-based MFA:

1. Attacker calls the victim's mobile provider and tricks the agent using a small amount of personal information
2. Agent transfers the victim's phone number to the attacker's SIM card
3. All texts (including one-time passwords) now go to the attacker's phone
4. Attacker can now bypass SMS-based MFA and log in as the victim

> **⚠️ EXAM TRAP:** There is NO WAY to compromise 2FA/MFA — **FALSE**. MFA CAN be bypassed via SIM swap, social engineering, MITM, or malware.

---

## 1.5 Red Team and Blue Team

| Team | Job |
|------|-----|
| **Red Team** | Performs the ATTACK — penetration testing, tries to break through current security controls. Must know the current threat landscape. Members need a wide range of skills (sometimes including coding to create custom exploits). |
| **Blue Team** | DEFENDS — keeps assets secure. When Red Team breaches, Blue Team must: triage the incident, scope the breach, create a fix plan, execute the plan, save and validate evidence, and engage all relevant teams. |

**Red Team metrics:**
- **MTTC** (Mean Time to Compromise) — time from the start of the attack until the Red Team successfully gets in
- **MTPE** (Mean Time to Privilege Escalation) — time from the start of the attack until the Red Team has full admin-level access on the target

**Blue Team metrics:**
- **ETTD** (Estimated Time to Detection) — how long it takes to DETECT an attack. Not 100% precise.
- **ETTR** (Estimated Time to Recovery) — how long it takes to fully RECOVER after an attack

> **⚠️ EXAM TRAP:** ETTD is a Red Team metric — **FALSE**. ETTD and ETTR both belong to the **BLUE TEAM**. MTTC and MTPE belong to the Red Team.

---

## 1.6 Assume Breach vs Prevent Breach

The old approach was to try to stop all attacks at the border (Prevent Breach). This no longer works alone.

- The traditional 'prevent breach' approach does NOT push for ongoing continuous testing
- The new approach is **'Assume Breach'** — assume attackers are already inside and keep testing continuously
- Red/Blue team simulations must be a CONTINUOUS process, not a one-time exercise

> **⚠️ EXAM TRAP:** The traditional prevent-breach approach PROMOTES ongoing testing — **FALSE**. It does not. Only the assume-breach approach does.

> **⚠️ EXAM TRAP:** Targeted attacks are usually SHORT in time — **FALSE**. Targeted/APT attacks are long-term campaigns lasting months or years.

> **⚠️ EXAM TRAP:** The private sector can ignore government-sponsored cyber attacks — **FALSE**. Private sector organisations are also targets and must not ignore these threats.

---

## 1.7 Real-World Examples

| Event | What Happened |
|-------|---------------|
| **WannaCry (2017)** | Ransomware that hit 300,000+ computers in 150 countries. Used the EternalBlue Windows weakness. A fix was available 59 days before the attack. Patch management failure. |
| **British Airways (2018)** | First big GDPR fine of £183 million. Customer credit card data was stolen. |
| **MtGox (2014)** | Bitcoin exchange. Handled 70% of all Bitcoin trading. Lost 850,000 bitcoins to hackers. Went bankrupt. |

---

# MODULE 2: INCIDENT RESPONSE (IR)

## 2.1 What is Incident Response?

| Term | Definition |
|------|------------|
| **Incident Response (IR)** | A step-by-step plan for handling a cyberattack. It covers how to find the attack (Detection) and how to deal with it quickly (Response). |

> *Common problem: Many companies have an IR plan but never update it. They do not use lessons from past attacks to improve it.*

---

## 2.2 Foundational Areas of the IR Process

Before building an IR process, these **5 foundational areas** must be defined:

| Foundational Area | Simple Description |
|---|---|
| **1. Scope** | Who does this IR process apply to? Company-wide or just certain departments? |
| **2. Objective** | What is the purpose of this IR process? Everyone must know what it is trying to achieve. |
| **3. Roles and Responsibilities** | Who is allowed to do what during an incident? Example: Who has the right to take a computer for investigation? Define and communicate this to everyone. |
| **4. Definition / Terminology** | Each company may define a 'security incident' differently. Define exactly what counts as an incident and create a glossary. |
| **5. Priorities / Severity Level** | Rank incidents by: impact on the business, type of data affected, and how recoverable the situation is. |

Additionally: Define how to interact with third parties, partners, and customers during an incident. Record EVERY step of the IR process — this is required, not optional.

> **⚠️ EXAM TRAP:** 'Assessment' is a foundational area of the IR process — **FALSE**. The 5 foundational areas are: Scope, Objective, Roles, Definition/Terminology, and Priorities. 'Assessment' is NOT one of them. *(PYP Q20)*

---

## 2.3 Requirements for a Successful IR Process

- All IT staff must know how to handle a security incident
- All users must understand the basic security fundamentals
- The help desk system and the IR team must be connected
- Good sensors (IDS) must be in place — both network sensors and host sensors for fast and complete detection
- The IR process must follow all laws and industry regulations

---

## 2.4 NIST IR Life Cycle — 4 Phases

| Phase | What Happens |
|-------|-------------|
| **1. Preparation** | Set up security controls before any attack. Includes antivirus, firewalls, and network security. This phase is always updated using lessons from past attacks. |
| **2. Detection and Analysis** | Watch for attacks. Use tools and intelligence to find threats quickly. Reduce false alarms. An attack may still be happening while it is being detected. |
| **3. Containment and Eradication** | Short-term: Cut off the affected part of the network. Long-term: Keep the business running while fixing systems. Then remove all malware and fix the root cause. |
| **4. Post-Incident Activity** | Review what happened. Update the IR plan. Use what you learned to improve the Preparation phase next time. |

> **⚠️ EXAM TRAP:** It is unnecessary to record every step of the IR process — **FALSE**. Recording every step IS necessary. *(PYP Q25)*

---

## 2.5 Threat Life Cycle Management — 6 Phases

A more detailed look at detecting and containing a threat. 84% of all attacks leave traces in log files.

1. **Discovery** — find that a threat exists
2. **Qualification** — confirm it is a real threat, not a false alarm
3. **Investigation** — find out how big the attack is
4. **Neutralisation** — stop the attack
5. **Recovery** — bring systems back to normal
6. **Adaptation** — update defences so this cannot happen again

---

## 2.6 Cybersecurity Kill Chain — 5 Attacker Steps

| Step | Simple Description |
|------|--------------------|
| **1. External Reconnaissance** | Collect information about the target from outside. Uses social media, dumpster diving, social engineering. |
| **2. Compromising the System** | Use the collected info to get into the system. Methods: phishing, exploiting weaknesses, IoT attacks. |
| **3. Lateral Movement** | Move through the network to find important data or systems. |
| **4. Privilege Escalation** | Get higher-level access (like admin rights) to run harmful programs. |
| **5. Concluding the Mission** | Reach the final goal — stealing data, launching ransomware, or causing damage. |

> *Remember: The Kill Chain = what the ATTACKER does. The NIST IR Life Cycle = what the DEFENDER does.*

---

## 2.7 Concluding the Mission — What Attackers Do at the End

| Action | Simple Description |
|--------|--------------------|
| **Exfiltration** | The attacker steals sensitive data from the organisation. This includes trade secrets, usernames, passwords, personal data, and top-secret documents. Attackers steal huge amounts of data at this stage. They often put the stolen data up for sale. They may also erase or modify files on the compromised systems. Real examples: Ashley Madison (2015), Yahoo (2013, reported 2016), LinkedIn (2016). |
| **Sustainment** | The attacker stays quiet after stealing data. They install rootkits or other malware to keep access to the victim's systems for as long as they want. The victim's security tools are now ineffective. The attacker usually has multiple access points so that if one is closed, they still have others. |
| **Obfuscation** | The attacker covers their tracks. They use techniques to confuse, slow down, or mislead the forensic investigation. Methods include: attacking outdated servers in small businesses or schools first, then moving laterally; using free unprotected WiFi to hide their origin; using dynamic code obfuscation, which changes the malware code to avoid detection by signature-based antivirus and firewalls. |

---

## 2.8 IR in the Cloud

| Cloud Model | Who Has Control During an Incident |
|-------------|-------------------------------------|
| **IaaS (e.g. AWS EC2, Azure VM)** | Customer has FULL control of the VM and ALL OS logs. Cloud provider only controls the lowest layer (hardware, hypervisor). Customer must review cloud provider policy before asking for data from the provider's layer. |
| **PaaS (e.g. Heroku, AWS Beanstalk)** | Shared control. Customer manages apps and data. Cloud manages the platform (OS, middleware). |
| **SaaS (e.g. Google Docs, Office 365)** | Cloud provider holds MOST incident response information. Customer contacts the cloud provider directly or opens a support ticket. Customer reads the SLA to understand what help they can get. |

> **⚠️ EXAM TRAP:** For IaaS, the cloud provider holds most IR information — **FALSE**. That is true for SaaS, not IaaS. In IaaS, the CUSTOMER has full control and all OS logs. *(PYP Q2)*

> **⚠️ EXAM TRAP:** Company responsibility is highest in SaaS — **FALSE**. Company responsibility is HIGHEST in IaaS, LOWEST in SaaS. *(PYP Q2)*

> *Cloud Containment: During an incident, revisit the cloud provider's ability to isolate the affected VM from others.*

---

# MODULE 3: RECONNAISSANCE AND COMPROMISING SYSTEMS

## 3.1 What is Reconnaissance?

| Term | Definition |
|------|------------|
| **Reconnaissance** | The information-gathering step before an attack. The attacker looks for weaknesses in the target's network, users, or computers. One of the most important steps in an attack. |

| Type | Simple Description |
|------|--------------------|
| **External Reconnaissance** | Done from OUTSIDE the organisation's network. The attacker does NOT touch the target systems. They find information through people and public sources. Methods: Dumpster Diving, Social Media, Social Engineering. |
| **Internal Reconnaissance** | Done from INSIDE the organisation, on-site. Uses software tools. The attacker interacts with the actual target systems to find weaknesses. |

---

## 3.2 Dumpster Diving

Looking through thrown-away materials for useful information. When companies dispose of old computers or storage devices without properly erasing data, attackers can recover:

- The internal setup and structure of the organisation's network
- Passwords saved in browsers
- User privileges and account details
- Access credentials for special systems used in the network

**Proper data removal methods:**

| Method | Simple Description |
|--------|--------------------|
| **Degaussing** | Uses a strong magnetic field to erase data from magnetic hard drives and tapes. Does NOT work on SSDs. |
| **Software deletion** | Deleting files using software is NOT secure. Data can still be recovered. |
| **SSD removal** | No single standard method exists. Common approach: encrypt the disk with a long random key, forget the key, then format the disk. |

---

## 3.3 Social Media and Identity Theft

Attackers look at LinkedIn, Facebook, etc. to build a picture of employees — job roles, technologies used, who works where. This information is used to make later attacks more convincing.

---

## 3.4 Social Engineering

| Term | Definition |
|------|------------|
| **Social Engineering** | Tricking people psychologically to make them give away secret information or do something they should not. This attacks the human, not the computer. A company cannot fully protect itself from this. |

**The Six Levers of Social Engineering:**

| Lever | How Attacker Uses It |
|-------|----------------------|
| **Reciprocation** | Do something nice first, then ask for something back. The target feels they owe a favour. |
| **Scarcity** | Create urgency: 'Do this NOW or lose access.' Pressure makes people act without thinking. |
| **Consistency** | Get a small 'yes' first, then ask for bigger things. People want to stay consistent. |
| **Liking** | People say yes to people they like. The attacker becomes friendly first. |
| **Authority** | Pretend to be a boss or IT security officer. People follow authority. |
| **Validation (Social Proof)** | Tell the target everyone else already did it. People follow the crowd. |

> **⚠️ EXAM TRAP:** The six levers include 'sincerity' — **FALSE**. The sixth lever is VALIDATION (Social Proof), not sincerity. *(PYP Q6)*

---

## 3.5 Social Engineering Attack Types

| Attack Type | Simple Description |
|-------------|--------------------|
| **Phishing** | Fake email pretending to be a real company. Has a link to a fake website that asks for passwords. Normal phishing success rate = 3%. |
| **Spear Phishing** | Same as phishing but aimed at ONE specific person or company. Attacker does background research first. Success rate = 70%. |
| **Vishing (Phone Phishing)** | Attacker calls the target. Uses a fake phone system (IVR) that sounds like a real bank. Target is asked to give PIN or password. |
| **Baiting** | Attacker leaves a USB drive with malware in a public place. Hoping a curious person will plug it in. |
| **Pretexting** | Attacker invents a fake story to get information. Example: pretending to be a new employee who needs help. |
| **Quid Pro Quo** | Attacker offers help in exchange for information. Example: pretending to be IT support. |
| **Tailgating** | Physically following an authorised person into a locked area. |
| **Diversion Theft** | Tricking a delivery person into delivering a package to the wrong place. |
| **Water Holing (Watering Hole Attack)** | Attacker finds websites a specific GROUP regularly visits. Infects those websites with malware. When the group visits, their computers get infected. Targets a specific group — NOT the general public. |

> **⚠️ EXAM TRAP:** Water holing attack targets the GENERAL PUBLIC — **FALSE**. It targets a SPECIFIC GROUP (organisation, industry, region). *(PYP Q6)*

> *Water Holing name origin: Named after predators who wait near a watering hole for their prey. The attacker waits at a website the victim will visit. Real examples: **NotPetya** (Ukrainian government), US Department of Labor attack.*

---

## 3.6 Current Trends in Compromising Systems

- Extortion attacks — ransomware that locks files and demands money
- Data manipulation attacks — quietly changing data so people trust wrong information
- Backdoors — hidden access points left inside a system for later use
- IoT device attacks — attacking smart devices (cameras, routers) with weak security
- Mobile device attacks — targeting phones and tablets
- Hacking the cloud — exploiting misconfigured cloud services

---

## 3.7 Compromising Operating Systems — Linux Live CD

A Linux Live CD (or bootable USB) is a way to access all files on a Windows computer without logging into Windows.

1. Boot the target computer from a USB/DVD with a bootable Linux image, choose 'Try Ubuntu'
2. All Windows files appear — the attacker can simply copy them
3. This ONLY works if the hard disk is NOT encrypted

> *Key protection: Full disk encryption (e.g., BitLocker) stops this attack completely.*

---

## 3.8 Compromising Web-Based Systems

Almost all organisations have websites. Web systems contain valuable data. The OWASP Top 10 is the most important list of web application vulnerabilities.

| Web Attack | Simple Description |
|------------|--------------------|
| **SQL Injection** | Attacker types SQL code into a form field. If the website does not check the input, the SQL code runs and can dump the whole database or bypass login. |
| **Cross-Site Scripting (XSS)** | Attacker injects malicious JavaScript into a web page. The script runs in other users' browsers and can steal cookies or redirect to fake sites. |
| **Broken Authentication** | Websites store session cookies on computers. If a user closes the browser without logging out (common on shared computers), the session stays active. An attacker can reuse this session. Session IDs in URLs can also be stolen if shared on social media. |
| **DDoS Attacks** | Floods a website with massive traffic using a botnet, causing it to crash. Very LOUD and obvious — NOT stealthy. |

---

## 3.9 Stuxnet and Flame

### Stuxnet

A very advanced worm targeting Siemens industrial control systems (centrifuges for nuclear fuel in Iran). Spread through USB drives. Used a fake digital certificate to hide. Damaged machines while making them look normal. First known nation-state cyberweapon.

### Flame

Advanced spyware found in 2012. Targeted Middle Eastern countries. Could secretly record audio, take screenshots, log keyboard typing, and capture network traffic. Very large at 20MB.

---

# MODULE 4: LATERAL MOVEMENT AND PRIVILEGE ESCALATION

## 4.1 Lateral Movement

| Term | Definition |
|------|------------|
| **Lateral Movement** | After getting into a network, the attacker moves from one system to another to find valuable data — without being detected. |

Common techniques: pass-the-hash, pass-the-ticket, remote service exploitation, and using normal Windows tools (Living off the Land).

> **⚠️ EXAM TRAP:** Lateral movement can be performed BEFORE compromising the system — **FALSE**. Lateral movement happens AFTER an initial compromise. *(PYP Q16)*

> **⚠️ EXAM TRAP:** In lateral movement, attackers move horizontally IN THE SAME SYSTEM — **FALSE**. They move across DIFFERENT systems in the network. *(PYP Q16)*

> **⚠️ EXAM TRAP:** Lateral movement is a SHORT-TERM campaign — **FALSE**. It is a LONG-TERM campaign. *(PYP Q16)*

> **⚠️ EXAM TRAP:** It is acceptable for an attacker to raise alerts during lateral movement — **FALSE**. Attackers try very hard NOT to raise any alerts. *(PYP Q16)*

---

## 4.2 Hash Functions and Pass-the-Hash

| Term | Definition |
|------|------------|
| **Hash Function** | A one-way mathematical function. It takes any input and produces a fixed-length output (called a hash). You CANNOT reverse a hash to get the original input back. |

**Three key properties:**

| Property | Simple Meaning |
|----------|----------------|
| **Easy to compute** | Given an input, computing the hash is fast. |
| **Hard to invert** | Given a hash output, you cannot find the original input. One-way only. |
| **Collision-resilience** | It is very hard to find two different inputs that produce the same hash output. |

Common hash algorithms: MD5 = 128 bits, SHA-1 = 160 bits, SHA-2 = 224/256/384/512 bits, SHA-3 = 224/256/384/512 bits.

| Term | Definition |
|------|------------|
| **Pass-the-Hash Attack** | Instead of cracking a password, the attacker steals the PASSWORD HASH from memory and uses it directly to log in. The attacker never needs to know the actual plain-text password. |

---

## 4.3 SMB Relay Attack

| Term | Definition |
|------|------------|
| **SMB Relay Attack** | An attack where the attacker sits between a client (victim) and a server. The attacker captures the victim's authentication data and replays it to the server to log in as the victim — without knowing the actual password. |

**How it works:**

1. The victim's computer tries to connect to a server using the SMB protocol
2. The attacker (in the middle) intercepts the connection
3. The server sends a challenge (random number) to the client — attacker passes it to the victim
4. The victim's computer encrypts the challenge using its password hash and sends back the response
5. The attacker captures this response and replays it to the real server
6. The server checks the response — it matches — so the attacker is logged in as the victim

> *Key point: The attacker never knows the actual password. They just forward the authentication messages. This exploits the NTLM protocol.*

---

## 4.4 Windows Lateral Movement Tools

| Tool | Simple Description |
|------|--------------------|
| **PowerShell** | Built into modern Windows. Legitimate tool — antivirus ignores it. Attackers run PowerShell scripts as scheduled tasks. Scripts pass through the command line without triggering antivirus. Leaves almost no forensic traces. |
| **Sysinternals** | Suite of Windows admin tools for remote control and inspection. Runs SILENTLY — does NOT alert the user being watched. Antivirus ignores it. Can reveal running processes and kill services. |
| **WMI (Windows Management Instrumentation)** | Built-in Microsoft framework. Legitimate and not detectable. Used to start processes remotely, query system information, and hide persistent malware. Used in the Sony Pictures hack (2014). WMImplant is a hacking tool built on WMI — NOT made by Microsoft. |
| **Remote Registry** | The Windows Registry controls hardware and software settings. It CAN be edited remotely. Attackers use this to disable antivirus, set malware to auto-start, and change system configurations. |
| **Scheduled Tasks** | Requires SYSTEM user privileges. Attackers use scheduled tasks to steal data slowly over time without raising alarms. |

> **⚠️ EXAM TRAP:** Sysinternals GIVES ALERTS to users on a remote system — **FALSE**. Sysinternals runs SILENTLY with no user notification. *(PYP Q32)*

> **⚠️ EXAM TRAP:** The Windows Registry CANNOT be remotely modified — **FALSE**. It CAN be remotely edited. *(PYP Q36)*

> **⚠️ EXAM TRAP:** WMImplant was developed by MICROSOFT — **FALSE**. It was made by FortyNorthSecurity (open-source on GitHub). *(PYP Q36)*

---

## 4.5 Privilege Escalation

| Term | Definition |
|------|------------|
| **Privilege Escalation** | Getting higher-level access rights than the attacker started with. Usually needs multiple tools and skills used together. |

| Type | Simple Description |
|------|--------------------|
| **Vertical Privilege Escalation** | Moving from a low-level account to a high-level one (e.g., normal user → admin/root). With admin rights, the attacker can run any harmful program. Buffer overflow is a common method. Example: EternalBlue (WannaCry) is a buffer overflow in Windows SMBv1. |
| **Horizontal Privilege Escalation** | Moving to a DIFFERENT account with the SAME level of access. Used to reach another user's data without needing admin rights. Normally done using techniques that steal login credentials. |

**Vertical privilege escalation methods:**

- Using a stolen valid administrator account — attacker logs into a sensitive system using the admin's credentials or creates their own login
- Exploiting programming errors (bugs) in software — these errors may let the attacker bypass security mechanisms
- Using insecure default passwords — some systems accept the same default password for all users
- Buffer overflow exploit — sending more data than a buffer can hold, overwriting nearby memory to run harmful code

> **⚠️ EXAM TRAP:** In horizontal privilege escalation, the attacker uses a ROOT account to access other normal users' accounts — **FALSE**. Horizontal escalation uses a SAME-LEVEL account, not a root/admin account. *(PYP Q21)*

> **Exam Tip:** Buffer overflow = key technique for VERTICAL privilege escalation. EternalBlue is a buffer overflow exploit in Windows SMBv1 — used in WannaCry.

---

# MODULE 5: MALWARE AND ATTACK TECHNOLOGIES

| Term | Definition |
|------|------------|
| **Malware** | Short for 'Malicious Software'. Any program put into a system — usually in secret — to damage or steal data, or to disrupt how the system works. (NIST SP 800-83) |

## 5.1 Malware Classification

Malware can be classified in different ways:

| Classification Basis | Examples |
|----------------------|----------|
| **Needs a host or standalone** | Viruses need a host program to spread. Worms and bots are standalone — they spread on their own without a host. |
| **Replicates or not** | Viruses and Worms replicate themselves. Trojans and spam email do NOT replicate. |
| **Type of payload** | What the malware does when it reaches its target: corrupts system/data files, steals information, steals computing resources (e.g., for mining), etc. |

---

## 5.2 Virus Components

Every virus has 3 main components:

| Component | Simple Description |
|-----------|--------------------|
| **Infection Mechanism (Infection Vector)** | The way the virus spreads and replicates itself. How it gets from one file/system to another. |
| **Trigger (Logic Bomb)** | The event or condition that causes the virus to activate and deliver its payload. Example: activates on a specific date. |
| **Payload** | What the virus actually DOES beyond just spreading. This is the harmful action — deleting files, encrypting data, displaying messages, etc. |

---

## 5.3 Virus Classification by Concealment Strategy

| Virus Type | Simple Description |
|------------|--------------------|
| **Stealth Virus** | Designed to completely hide itself from antivirus detection. Not just the payload — the entire virus is hidden. |
| **Encrypted Virus** | Uses encryption to hide its contents so antivirus scanners cannot read what it contains. |
| **Polymorphic Virus** | Changes its own code every time it copies itself into another program. The signature changes each time — signature-based scanners struggle to detect it. |
| **Metamorphic Virus** | A higher level of polymorphic virus. It does not just change between copies — it can completely rewrite itself. Much harder to detect. |

---

## 5.4 Types of Malware

| Malware Type | Simple Description + Example |
|---|---|
| **Virus** | Attaches to real programs/files. Needs a HOST to spread. Activates when the host file is opened. Example: infects .exe files and spreads when shared. |
| **Worm** | Spreads on its own — NO host needed. Uses network weaknesses. Example: WannaCry spread automatically using the SMB port. |
| **Trojan (Trojan Horse)** | Looks like safe software but does harmful things in the background. Does NOT spread by itself. Example: a 'free game' that installs a keylogger. |
| **Backdoor** | Creates a hidden way into a system that skips normal login. Often installed by other malware. Example: Remote Access Trojan (RAT). |
| **Ransomware** | Locks (encrypts) files and demands money to unlock them. Example: WannaCry demanded Bitcoin. Hospitals and critical infrastructure are common targets. |
| **Rootkit** | Hides malware on a system by changing the operating system. Very hard to detect. |
| **Spyware** | Secretly watches what the user does and sends info to the attacker. Example: keylogger recording every keystroke. |
| **Adware** | Shows unwanted ads and can track browsing behaviour. |

---

## 5.5 Attack Tools — Quick Reference

| Tool | What It Does |
|------|-------------|
| **Metasploit** | A framework full of exploits and payloads for attacking known weaknesses. Launched via 'msfconsole'. NOT a network scanner. |
| **msfvenom** | Creates payloads (harmful programs) for backdoors — e.g., a reverse TCP shell. These backdoors are often sent via phishing emails. |
| **Nmap** | NETWORK SCANNER — maps out computers and devices on a network. Has scripting for vulnerability checking. NOT a password cracker. |
| **Nessus** | VULNERABILITY SCANNER — finds misconfigurations, missing patches, weak passwords. Best vulnerability scanner for security professionals. |
| **John the Ripper** | PASSWORD CRACKING tool — tries to guess passwords using brute force or dictionary attacks. |
| **THC Hydra** | PASSWORD CRACKING tool — same purpose as John the Ripper. |
| **Cain and Abel** | PASSWORD CRACKING tool — brute force and dictionary attacks. |
| **Wireshark** | PACKET SNIFFER — captures and shows network packets in human-readable format. Used for internal reconnaissance. |
| **Mimikatz** | Pulls password hashes and plain-text passwords from Windows memory. Used for pass-the-hash attacks. |

> **⚠️ EXAM TRAP:** John the Ripper, THC Hydra, and Nmap are ALL password cracking tools — **FALSE**. Nmap is a NETWORK SCANNER, not a password cracker. *(PYP Q4)*

---

## 5.6 Fuzzing

| Term | Definition |
|------|------------|
| **Fuzzing** | An automated software testing technique that sends INVALID, UNEXPECTED, or RANDOM inputs to a program to find hidden weaknesses. It does NOT use valid inputs — that would be normal testing. |

- Used by attackers to find zero-day weaknesses not yet known to developers
- Often too slow for very large programs
- The other common zero-day discovery method is source code analysis

> **⚠️ EXAM TRAP:** Fuzzing 'provides VALID inputs to a program' — **FALSE**. Fuzzing uses INVALID or RANDOM inputs. *(PYP Q3)*

---

## 5.7 Antivirus Scanner Generations

| Generation | What It Does |
|------------|-------------|
| **1st Generation** | Uses virus SIGNATURES only. Matches known malware patterns. Fast but only detects known threats. Cannot detect polymorphic viruses (their signature changes). |
| **2nd Generation** | Uses HEURISTIC rules to search for probable malware. Also uses integrity checks (e.g., checksums) to detect changes. Better against polymorphic viruses. |
| **3rd Generation** | Detects viruses by BEHAVIOUR. Example: if a program tries to interact with system files in an unusual way, it triggers an alert. Detects new threats based on what they DO. |
| **4th Generation** | Uses a COMBINATION of multiple antivirus techniques together. The most comprehensive approach. |
| **Virtualisation (Sandboxing)** | A newer approach. The suspect program is run inside a safe, isolated but realistic environment (sandbox) and its behaviour is observed. Note: up to 28% of all malware in 2014 was 'virtual machine aware' — designed to detect sandboxes and hide its true behaviour. |

> *WannaCry Kill Switch connection: WannaCry checked whether it could connect to a specific internet domain. If it could connect, it STOPPED running because it assumed it was inside a sandbox/antivirus environment. Registering that domain triggered this kill switch.*

---

## 5.8 How to Protect Against Malware

- Keep software and OS updated — patch management (WannaCry could have been stopped this way)
- Use antivirus/anti-malware software
- Filter emails to block phishing and harmful attachments
- Use application whitelisting — only let approved programs run
- Train staff — teach them to spot suspicious emails and links
- Use network segmentation — stops malware from spreading to other parts of the network
- Make regular backups — recover files without paying ransom

---

## 5.9 WannaCry — Full Case Study

**Date:** 12 May 2017. Hit: 300,000+ computers in 150+ countries.

| Aspect | Detail |
|--------|--------|
| **Type** | Ransomware + Worm (spread itself automatically) |
| **Weakness Used** | EternalBlue — a buffer overflow in Windows SMBv1. Made by the NSA, later leaked by the Shadow Brokers hacker group. |
| **Was There a Fix?** | Yes. Microsoft released patch MS17-010 on 14 March 2017 — 59 days BEFORE the attack. Companies that applied the patch were safe. |
| **How It Spread** | Automatically scanned networks for vulnerable computers on port 445. No user action needed. |
| **Who Was Hit?** | NHS hospitals in the UK (operations cancelled), Telefonica Spain, FedEx, Russian Interior Ministry. |
| **How It Was Stopped** | Security researcher Marcus Hutchins found an unregistered domain inside the code and registered it — this acted as a kill switch and stopped the spread. |
| **Lesson** | Apply security patches immediately. Unpatched systems are easy targets. |

---

# MODULE 6: LAW AND REGULATION

## 6.1 GDPR — General Data Protection Regulation

| Topic | Simple Answer |
|-------|---------------|
| **Made by** | The European Union (EU) |
| **Start date** | 25 May 2018 |
| **Purpose** | Create clear, strict rules for protecting personal data of people in the EU. All organisations must follow the same rules. |
| **Who must follow it?** | Any organisation that processes personal data of EU residents — even if the organisation is based OUTSIDE the EU. (Extraterritorial scope) |
| **What is personal data?** | Any information about a person who can be identified. Examples: name, ID number, location, email, genetic data, health data. |
| **Fines** | Up to €20 million OR 4% of the company's total global yearly income — whichever is higher. |
| **Exception** | Does NOT apply when a person processes their own data for purely personal or household use. |

### The 7 Key Principles of GDPR (Article 5)

| Principle | Simple Meaning |
|-----------|----------------|
| **1. Lawfulness, Fairness, Transparency** | You must have a legal reason to use data. The person must know how their data is used. Nothing hidden. |
| **2. Purpose Limitation** | Only collect data for a specific reason. Do not use it for other purposes later. |
| **3. Data Minimisation** | Only collect data you actually need. |
| **4. Accuracy** | Keep data correct and up to date. |
| **5. Storage Limitation** | Do not keep data longer than needed. |
| **6. Integrity and Confidentiality** | Use proper security to protect data. (Links to CIA Triad) — Technical measures: 2FA, encryption. Organisational measures: staff training, security policy. |
| **7. Accountability** | The organisation must be responsible and PROVE it follows the rules. This includes training staff and regularly testing data handling processes. |

> *GDPR Accountability (Q23): The principle that requires training staff and regularly evaluating data handling processes.*

> *Subject Access Request (SAR) (Q28): What an individual must submit to find out what personal data a company holds about them under GDPR.*

---

## 6.2 GDPR — Controller and Processor

| Role | Simple Description |
|------|--------------------|
| **Controller** | The party who DECIDES the purposes and means of processing personal data. Responsible for GDPR compliance. |
| **Processor** | The party who PROCESSES personal data on behalf of the controller. Example: a cloud hosting company that stores customer data for a business. |

The territorial scope of GDPR is based on two criteria: (1) the establishment of a controller or processor IN the EU, or (2) being active on the EU market by offering services/goods or monitoring behaviour of EU residents.

---

## 6.3 Rights of Data Subjects Under GDPR

Every person whose data is processed (data subject) has these rights:

- Right to be informed — know how your data is being used
- Right of access — request a copy of your personal data (Subject Access Request / SAR)
- Right to rectification — ask for incorrect data to be corrected
- Right to erasure (Right to be forgotten) — ask for your data to be deleted
- Right to restrict processing — limit how your data is used
- Right to data portability — receive your data in a usable format
- Right to object — object to your data being used for certain purposes
- Rights related to automated decision making and profiling — humans must review automated decisions that significantly affect you

---

## 6.4 GDPR Cross-Border Data Transfers

GDPR restricts sending personal data outside the EU to make sure the same level of protection is maintained.

- Data can only be transferred to non-EU countries where the European Commission has decided the country provides an ADEQUATE level of protection (called an adequacy decision under Article 45)
- If a country's protection is found to be inadequate, the Commission can remove its adequacy status
- Australia currently does NOT have an adequacy decision — so transferring EU personal data to Australia requires additional safeguards (e.g., Standard Data Protection Clauses, Binding Corporate Rules)

> *Real Example: Meta (Facebook) was fined a record €1.2 billion in May 2023 by Ireland's Data Protection Commission. Reason: Meta kept transferring EU user data to the USA without adequate protection. The US does not provide an equivalent level of data protection to the EU.*

---

## 6.5 Australian Privacy Act 1988

Contains 13 Australian Privacy Principles (APPs). Key ones to know:

| APP | Simple Description |
|-----|--------------------|
| **APP1** | Open and transparent management. The organisation must have a clear, up-to-date privacy policy. |
| **APP2 — KEY** | Anonymity and Pseudonymity. Individuals must have the OPTION to not identify themselves, or use a pseudonym, when dealing with an organisation (where lawful and practical). |
| **APP3** | Collection of solicited personal information — must have a clear privacy policy for collecting data. |
| **APP5** | Notification — if an entity collects personal information, it must notify the person. |
| **APP12** | Access — individuals have the right to access their own personal information held by an organisation. |
| **APP13** | Correction — outlines steps to correct personal information if it is wrong. |

| Term | Definition |
|------|------------|
| **Anonymity** | A person chooses NOT to identify themselves at all when interacting with an organisation. |
| **Pseudonymity** | A person uses a FAKE name or identifier instead of their real name. Gives some privacy while still allowing interaction. |

---

## 6.6 Cyber Security Act 2024

Issued 29 November 2024. Designed to bring Australia in line with international best practices. Implements 4 key initiatives:

| Initiative | Simple Description |
|------------|--------------------|
| **1. Minimum security standards for smart devices** | IoT and smart devices (cameras, TVs, routers) must meet minimum cybersecurity standards. |
| **2. Mandatory ransomware reporting** | Certain businesses MUST report to the government if they pay a ransom or receive a cyber extortion demand. |
| **3. Limited Use obligation** | The National Cyber Security Coordinator can only use information shared by companies during a cyber incident for specific limited purposes. Encourages companies to share information with the government. |
| **4. Cyber Incident Review Board** | Reviews significant cyber incidents and shares lessons learned with the whole country. |

---

# MODULE 7: DIGITAL FORENSICS

## 7.1 Definitions

| Term | Definition |
|------|------------|
| **Forensics Science** | Using scientific methods to collect, keep safe, and study evidence for legal cases. |
| **Digital Forensics** | Using computer science and investigation methods to study DIGITAL EVIDENCE for a legal purpose. Also covers research and incident response. |

Key standards:
- NIST SP 800-86 — Guide for using forensics in Incident Response
- ISO/IEC 27037 — Guide for finding, collecting, and keeping digital evidence safe

---

## 7.2 Why Digital Forensics Is Used

Digital forensics tools are not only for criminal investigations. They are also useful for:

- **Operational Troubleshooting** — finding the root cause of a technical problem
- **Log Monitoring** — watching logs for suspicious activity
- **Data Recovery** — getting back deleted or corrupted files
- **Data Acquisition** — making forensic copies of storage devices
- **Due Diligence / Regulatory Compliance** — proving that security standards are followed

---

## 7.3 Investigations Triad

| Function | What It Does |
|----------|-------------|
| **Vulnerability/Threat Assessment and Risk Management** | Test and check if computers and servers are secure. Do penetration tests to find weaknesses in OS and applications. |
| **Network Intrusion Detection and Incident Response** | Detect attacks on the network. Respond to attacks. Collect evidence that could be used in court. |
| **Digital Investigations** | Manage investigations. Study systems that may contain evidence related to a crime or security incident. |

---

## 7.4 Forensic Workstation Setup

Investigations are done on a specially configured forensic workstation. Key requirements:

- Windows XP or later operating system
- **Write-blocker device** — lets you READ the evidence drive WITHOUT writing any data to it, so evidence is not changed
- Digital forensics acquisition tool — to make exact copies of storage
- Digital forensics analysis tool — to examine the copied data
- A target drive — to store the copy of the evidence

Common forensics software: ProDiscover, EnCase, FTK (AccessData Forensic Toolkit), X-Ways Forensics.

> *Write-blocker is critical. Without it, simply connecting a drive to a computer can change timestamps and metadata — making evidence invalid in court.*

---

## 7.5 Digital Forensics Process

| Step | Simple Description |
|------|--------------------|
| **1. Gathering the Evidence** | Collect the physical devices (computers, USB drives, phones) that may contain evidence. |
| **2. Acquiring an Image of Evidence Media** | Make an exact bit-for-bit copy (bit-stream copy) of the storage device using a tool like ProDiscover. All analysis is done on the copy — not the original. |
| **3. Analysing the Digital Evidence** | Examine the forensic copy for files, deleted files, metadata, and activity logs. |
| **4. Completing the Case** | Write up findings clearly for use in court or by management. |
| **5. Critiquing the Case** | Review what went well and what to improve for future investigations. |

> *Key rule: Evidence must be collected carefully so it is not changed. Maintain chain of custody at all times.*

---

## 7.6 Public-Sector vs Private-Sector Investigations

| Type | Simple Description |
|------|--------------------|
| **Public-Sector Investigations** | Carried out by government agencies responsible for criminal investigations and prosecution. The examiner must understand: standard legal processes, guidelines on search and seizure, how to build a criminal case. Key questions asked: What tool was used? Was it trespass? Was it theft or vandalism? Was it cyberstalking or harassment? A criminal case follows 3 stages: The Complaint → The Investigation → The Prosecution. |
| **Private-Sector Investigations** | Carried out inside companies to investigate rule violations or attacks on company assets. The goal is to minimise risk to the company. Three common situations: abuse/misuse of computing assets, email abuse, internet abuse. Businesses want to reduce litigation (legal costs). Ways to do this: publish clear policies employees can follow, and display warning banners that inform users the organisation reserves the right to inspect computer systems and network traffic. |

**Investigation planning steps:**

1. Acquire the evidence
2. Complete an evidence form and establish the chain of custody
3. Transport evidence to a computer forensics lab
4. Secure evidence in an approved secure container
5. Prepare the forensics workstation
6. Retrieve evidence from the secure container
7. Make a forensic copy
8. Return the original evidence to the secure container
9. Process the copied evidence with forensics tools

| Term | Definition |
|------|------------|
| **Chain of Custody Form (Evidence Custody Form)** | A document that records everything that has or has not been done with the original evidence and any forensic copies. Proves that evidence has not been tampered with. |

> *BYOD and digital investigations: If an employee connects a personal device to the business network, many companies treat it under the same rules as company property. BYOD is a major challenge for digital investigations and regulatory compliance.*

---

# MODULE 8: PRIVACY AND DIFFERENTIAL PRIVACY

## 8.1 Privacy vs Confidentiality

| Term | Simple Meaning |
|------|----------------|
| **Privacy** | Keeping personal information secret — to protect the INDIVIDUAL person. |
| **Confidentiality** | Keeping business information secret — to protect the ORGANISATION. |

---

## 8.2 Differential Privacy

| Term | Definition |
|------|------------|
| **Differential Privacy** | A mathematical method that lets organisations share data statistics without revealing information about any single person. It adds small amounts of random 'noise' to results so individual records cannot be identified. |

| Aspect | Simple Explanation |
|--------|--------------------|
| **Purpose** | Publish useful statistics from data WITHOUT revealing any one person's information. |
| **Main idea** | For every query on the database, return the answer WITH a small amount of random noise. The noise hides the effect of any single individual's data. |
| **What happens without noise?** | Without noise, an attacker could ask several related questions and compare answers to figure out one specific person's data. |
| **Challenges** | Accuracy is lower for SMALL datasets. Privacy loss can build up over time if many queries are made. Active research problems. |
| **Who uses it?** | Apple (iOS), Google (RAPPOR), Microsoft, US Census Bureau, Uber, Meta. These companies use it to collect usage statistics without exposing individual user data. |

> *Differential privacy was first proposed in 2006. Key guarantee: an attacker cannot tell if any one person's data was included in or removed from the dataset.*

---

# MODULE 9: NETWORK SEGMENTATION

| Term | Definition |
|------|------------|
| **Network Segmentation** | Splitting one computer network into smaller separate parts. If one part is attacked, the attacker cannot easily move to the other parts. |

## 9.1 Why Use Network Segmentation?

- Stops lateral movement — the attacker stays stuck in one segment
- Makes the attack surface smaller
- Helps with compliance (e.g., PCI DSS requires payment systems to be isolated)
- Improves network performance by reducing traffic

---

## 9.2 Types of Segmentation

| Type | Simple Description |
|------|--------------------|
| **Physical Segmentation** | Uses separate physical hardware for different zones. Most secure but most expensive. |
| **VLAN (Virtual LAN)** | Creates separate logical zones on the SAME physical hardware. More flexible and cheaper. Common in medium and large organisations. |
| **DMZ (Demilitarised Zone)** | A zone between the internet and the internal network. Public-facing servers (web, email) are placed here. Traffic goes through the DMZ before reaching the internal network. |

> **⚠️ EXAM TRAP:** VLANs are separated PHYSICALLY, not logically — **FALSE**. VLANs are LOGICAL separations on shared hardware. *(PYP Q10)*

> **⚠️ EXAM TRAP:** No data can flow between segmented networks even if there is a router — **FALSE**. Data CAN flow if a router connects the segments. *(PYP Q10)*

---

## 9.3 VLAN Design Options

| Design Option | Simple Description |
|---------------|--------------------|
| **By Department (Small/Medium Orgs)** | Group resources by department. Simple but causes cross-VLAN complexity if departments need shared resources. Large organisations avoid this. |
| **By Business Objective** | Group resources that share the same business goal. Example: all sales systems in one VLAN. |
| **By Level of Sensitivity** | Group systems by risk level (high, medium, low sensitivity) after a risk assessment. |
| **By Location** | For large organisations, organise VLANs by physical location. |
| **By Security Zone** | Create special zones for specific purposes. Example: one zone for all servers that external partners can access. |
| **Mixed VLAN** | In practice, most organisations use a COMBINATION of these. No single perfect solution. |

> **⚠️ EXAM TRAP:** Cross-VLAN is suitable for LARGE networks — **FALSE**. Cross-VLAN is for SMALL and MEDIUM organisations. Large networks avoid it because of complexity. *(PYP Q18)*

---

## 9.4 Virtual Network Security

When using virtual machines (VMs), traffic from one VM can reach other hosts. To prevent this, these features are enabled on virtual switches:

- **MAC address spoofing prevention** — stops a VM from sending traffic using a fake MAC address
- **DHCP Guard** — stops VMs from acting as a DHCP server
- **Router Guard** — stops VMs from sending fake router messages
- **Port ACL (Access Control List)** — sets specific access rules per port based on MAC or IP address

---

## 9.5 Defence in Depth

| Term | Definition |
|------|------------|
| **Defence in Depth** | A security strategy that uses MANY layers of security. If one layer fails, the next layer still protects. No single point of failure. |

Example layers from outside to inside: Perimeter firewall → DMZ → Internal firewall → VLAN segmentation → Host-based firewall → Endpoint detection → User authentication → Encryption at rest.

> *The Defence in Depth approach DELAYS attacks — it does not guarantee they will never get in. (PYP Q15)*

---

## 9.6 Network Access Control (NAC)

| Term | Definition |
|------|------------|
| **NAC (Network Access Control)** | A security approach that checks a device's health AND authenticates the user BEFORE letting the device connect to the network. Combines endpoint security checks, user authentication, and network enforcement. |

- NAC DOES perform end-user authentication — this is its main purpose
- NAC checks: latest patches, antivirus running, firewall on, compliance with security policies
- Cisco NAC is a well-known example

> **⚠️ EXAM TRAP:** NAC systems do NOT perform end-user authentication — **FALSE**. NAC DOES authenticate users and check device health. *(PYP Q18)*

---

## 9.7 Network Segmentation Best Practices

- Use SSH to manage switches and routers (not Telnet — Telnet is not encrypted)
- Restrict who can access the management interface
- Disable any switch ports that are not being used
- Enable port security to stop MAC flooding attacks
- Enable DHCP snooping to stop fake DHCP servers
- Keep switch and router firmware updated

---

## 9.8 Site-to-Site VPN

| Term | Definition |
|------|------------|
| **Site-to-Site VPN** | A technology that creates a secure, private, encrypted communication channel between the main company network and a remote office or branch network. *(PYP Q27 answer)* |

When planning a site-to-site VPN, apply the 'need to know' principle — only allow access to the exact segments that are really necessary. If a branch office has no need to access the HR VLAN, block it.

---

# MODULE 10: THREAT INTELLIGENCE

## 10.1 Definitions

| Term | Definition |
|------|------------|
| **Intelligence** | Knowledge about what is happening or what might happen — used to make decisions and take action. (US CIA) |
| **Threat Intelligence (CTI)** | Threat information that has been collected, analysed, and made useful so organisations can make better security decisions. (NIST SP 800-150) |

---

## 10.2 How Threat Intelligence Is Used

Threat intelligence can be used in 4 main ways:

| Use | Simple Description |
|-----|--------------------|
| **Profiling Motivations** | Understanding WHY attackers attack. Knowing the type of attacker helps you focus your defences on threats that are actually relevant to your organisation. |
| **Analysing Attacker Tactics** | Understanding the attacker's methods, tools, and strategies (TTPs). |
| **Analysing Techniques** | Identifying indicators of specific malware or attack campaigns. |
| **Assessing Operations** | Assessing the organisation's own ability to detect and handle future cyber threats. |

---

## 10.3 Attacker Profiling — Motivation Types

| Motivation Type | Simple Description |
|-----------------|--------------------|
| **Cybercrime** | The main motivation is FINANCIAL GAIN. Attackers want money — through ransomware, stealing credit card data, selling stolen data, etc. |
| **Hacktivism** | The motivation is political or ideological expression. The group may express a political preference or support a particular cause. Example: Anonymous. This is the 'profiling motivation' answer for PYP Q31. |
| **Cyber Espionage / State-Sponsored** | Carried out as part of a larger government-sponsored campaign. The goal is to steal information that can be used against the hacked party. The private sector CANNOT ignore these attacks — they are also targeted. |

> *Key question to ask: Which type of attacker is most likely to target your organisation? A financial institution should focus on threat intelligence from adversaries actively attacking the financial industry.*

---

## 10.4 Intelligence Collection Types

| Type | What It Means |
|------|---------------|
| **OSINT** | Open Source Intelligence — from public sources: news, social media, government websites. |
| **HUMINT** | Human Intelligence — from human sources. |
| **SIGINT** | Signals Intelligence — from intercepted electronic signals and communications. |
| **GEOINT** | Geospatial Intelligence — from satellite images and geographic data. |
| **IMINT** | Imagery Intelligence — from photographs and image analysis. |

---

## 10.5 Levels of Threat Intelligence

| Level | Who Uses It and Why |
|-------|---------------------|
| **Tactical** | Focuses on HOW attackers operate — TTPs (Tactics, Techniques, Procedures). Main output: IOCs. IOCs are machine-readable. TTP descriptions are human-readable. Useful for NOC/SOC defenders. |
| **Operational** | Information about specific campaigns and threat actors. Helps with incident response planning. |
| **Strategic** | High-level overview of the threat landscape. For senior management. Helps with long-term security planning. |

> **⚠️ EXAM TRAP:** CTI providers supply TTPs in MACHINE-READABLE format ONLY — **FALSE**. TTPs are human-readable. IOCs are machine-readable. *(PYP Q1)*

> **⚠️ EXAM TRAP:** It is desirable for an organisation to defend against ALL potential threats — **FALSE**. It is NOT practical or desirable to try to defend against every possible threat. Organisations must prioritise. *(PYP Q1)*

---

## 10.6 IOC — Indicators of Compromise

| Term | Definition |
|------|------------|
| **IOC (Indicator of Compromise)** | Evidence that a system has been attacked or is currently under attack. Used to detect known threats and update security systems. |

- **File IOCs** — known malicious file hashes (MD5, SHA256), suspicious filenames
- **Network IOCs** — known bad IP addresses, domain names, or URLs
- **Behavioural IOCs** — unusual processes, unexpected registry changes, strange outbound connections
- **Email IOCs** — phishing sender addresses, suspicious subject lines
- Large number of requests for the same file from the same host — can indicate data staging before theft

---

## 10.7 Major IOCs in Event Logs

| IOC / Event Log Entry | Why It Matters |
|-----------------------|----------------|
| **Audit log was cleared** | Major red flag. Attackers clear logs to hide tracks. |
| **Logon success/failure at unusual times** | Multiple failed logons = brute force. Logon at odd hours = suspicious. |
| **Registry value modified** | Could mean malware set itself to auto-start. |
| **Unauthorised access to a file or object** | Used to find who made an unauthorised change. |
| **New process created** | Malware often runs as cmd.exe. An unexpected new process is a sign of infection. |
| **Scheduled task enabled or updated** | Attackers use scheduled tasks for persistence. |
| **Mismatched port-application traffic** | Application using an unusual port could mean C2 traffic hiding as normal traffic. Example: infected computers send C2 messages as DNS requests over PORT 80 (DNS normally uses port 53). |

> *Port 80 and DNS: DNS normally uses port 53. Attackers disguise C2 traffic as DNS requests but send them over port 80 to blend in with normal web traffic. This is TRUE — not an incorrect statement. (PYP Q5)*

---

## 10.8 Alert Triage

| Term | Definition |
|------|------------|
| **Alert Triage** | The process of deciding which security alert is the most urgent and must be handled first. If triage is done badly, the whole response operation can fail. |

- Which systems were attacked?
- Where did the attack start?
- Which user account was used?
- Did the attacker move to other systems? Which ones?

---

## 10.9 Open Source Threat Intelligence Tools

| Tool | What It Does |
|------|-------------|
| **fraudguard.io** | Quick IP address validation — check if an IP is known to be malicious. |
| **vms.drweb.com** | Malware inspection — upload a suspicious file to check if it is malware. |
| **otx.alienvault.com** | Threat intelligence exchange — find and share IOCs (hashes, IPs, domains) with the security community. |

---

## 10.10 Incident Investigation — Real On-Premises Case Study

How a real attack unfolded (from the slides):

1. Everything started with a **PHISHING EMAIL**
2. The email had an image with a hidden hyperlink to a malicious website
3. Visiting the website automatically downloaded a package of tools: mimikatz, procdump, PsExec
4. mimikatz stole password hashes (pass-the-hash attack)
5. PsExec was used to escalate privileges
6. procdump dumped credentials from memory
7. The attacker cleared the event logs to hide evidence
8. The infected computer was NOT part of the domain, so only local credentials were stolen

---

# MODULE 11: ACTIVE SENSORS — IDS AND IPS

## 11.1 IDS — Intrusion Detection System

| Term | Definition |
|------|------------|
| **IDS (Intrusion Detection System)** | A device or software that watches a network or system for attacks or rule violations and sends an ALERT. It only detects and alerts — it does NOT block anything. |

| IDS Type | Simple Description |
|----------|--------------------|
| **NIDS (Network-based IDS)** | Watches traffic for the whole network segment. Placed at important points in the network. Compares traffic to a list of known attacks. NIDS CANNOT fully shield against internal recon when hackers scan individual targets one by one — it has blind spots. |
| **HIDS (Host-based IDS)** | Installed on a single computer. Watches local activity: system calls, file changes, application logs. Covers only that one machine. |

> **⚠️ EXAM TRAP:** NIDS shields the organisation from internal recon even when hackers scan individual targets — **FALSE**. NIDS has blind spots for individual/slow scanning. *(PYP Q32)*

---

## 11.2 Detection Methods

| Method | Simple Description |
|--------|--------------------|
| **Signature-based** | Compares activity to a database of known attack patterns. Fast and accurate for KNOWN attacks. CANNOT detect new/unknown (zero-day) attacks. |
| **Anomaly-based (Behaviour-based)** | Learns what 'normal' looks like (baseline model, built using machine learning). Alerts when activity is different from normal. CAN detect new/unknown attacks. BUT produces more false positives (false alarms). |

**Two major anomaly-based intrusion detection systems:**

- **UEBA** (User and Entity Behaviour Analytics) — profiles normal behaviour of users and entities, alerts on deviations
- **NTA** (Network Traffic Analysis) — analyses network traffic patterns. Especially useful for detecting malicious INSIDERS and targeted external attacks that have already compromised a system

> **Exam Tip:** Signature-based = good for known threats. Anomaly-based = can catch new threats but more false alarms.

---

## 11.3 IPS — Intrusion Prevention System

| Term | Definition |
|------|------------|
| **IPS (Intrusion Prevention System)** | Works the same as IDS but also BLOCKS the attack (e.g., drops the harmful traffic). Both HIPS (host-based) and NIPS (network-based) versions exist. |

| System | What It Does |
|--------|-------------|
| **IDS** | MONITORS and ALERTS only. Does not block. Lower risk of blocking legitimate traffic. |
| **IPS** | MONITORS, ALERTS, and BLOCKS. Risk: a false positive can block real traffic and stop services from working. |

---

## 11.4 Old vs New Defender Mindset

| Mindset | Approach |
|---------|---------|
| **Old (Traditional) Mindset** | Watch the network border only. Trust users inside the network. Only monitor HIGH PROFILE users. |
| **New Mindset (Assume Breach / Zero Trust)** | Monitor ALL users — including regular ones. Assume attackers are already inside. Current attackers specifically target REGULAR users first (they have weaker security), then move quietly towards bigger targets. |

> **⚠️ EXAM TRAP:** Traditional defender mindset focuses on monitoring ALL users — **FALSE**. It focuses on HIGH PROFILE users only. This is TRUE in the slides and NOT an incorrect statement. *(PYP Q5)*

---

## 11.5 Behaviour Analytics

Behaviour analytics = watching how users normally behave and alerting when something unusual happens. It is used as one layer of defence in the defence-in-depth approach.

- Used to detect pass-the-ticket attacks — looks for attack patterns and suspicious behaviour from regular users
- Example: If a regular user tries to run NetSess.exe tool against the local domain, Microsoft ATA raises an alert because this is unusual for a regular user

---

## 11.6 Behaviour Analytics in a Hybrid Cloud

In a hybrid cloud environment (on-premises + IaaS), the Blue Team must:

- Expand their view of the threat landscape to include cloud threats
- Perform an assessment to validate continuous connectivity with the cloud
- Check the impact of the hybrid setup on the overall security posture
- Focus efforts on improving detection — IaaS adoption is growing and is ultimately having a positive impact on security

> *Most companies in a hybrid cloud environment use the IaaS model. The security aspect of IaaS is still the main concern for organisations adopting it.*

---

# MODULE 12: RECOVERY PROCESS

## 12.1 Disaster Recovery Plan (DRP)

| Term | Definition |
|------|------------|
| **Business Continuity Plan (BCP)** | A plan that makes sure the most important business activities keep running during and after a disaster. |
| **Disaster Recovery Plan (DRP)** | A plan that focuses specifically on bringing IT systems and data back after a disaster. It is part of the BCP. |

| Metric | Simple Meaning |
|--------|----------------|
| **RTO (Recovery Time Objective)** | Maximum time allowed to bring a system back online. Example: 'We must be back online within 4 hours.' |
| **RPO (Recovery Point Objective)** | Maximum amount of data loss allowed, measured in time. Example: 'We can lose at most 1 hour of data.' |

**Key facts about the DR plan:**

- SENIOR MANAGEMENT determines the scope of the DR plan
- A thorough DR plan must consider the WORST-CASE SCENARIO
- POLICIES are a key priority in making a DR plan — they give authority and direction
- The DR team determines the MINIMUM time each department can work without critical systems (RTO per department)
- The DR team does NOT approve the plan alone — senior management is also involved

> **⚠️ EXAM TRAP:** Policies are NOT key areas in a DR plan — **FALSE**. Policies ARE key and must be prioritised. *(PYP Q37)*

> **⚠️ EXAM TRAP:** The DR team has SOLE responsibility to approve the DR plan — **FALSE**. Senior management is also involved. *(PYP Q37)*

---

## 12.2 IT Contingency Planning — 5 Steps

| Step | Simple Description |
|------|--------------------|
| **Step 1: Develop a contingency planning policy** | Write a formal policy statement. Defines scope, resources, training needs, and testing schedules. |
| **Step 2: Conduct a Business Impact Analysis (BIA)** | Identify critical IT resources. Determine how long the organisation can survive without each one. Develop recovery priorities. BIA has 3 sub-steps: identify critical resources, identify disruption impacts, develop recovery priorities. |
| **Step 3: Identify preventive controls** | Put controls in place that REDUCE the chance of a disruption (e.g., redundant power, regular backups). |
| **Step 4: Develop recovery strategies** | Plan exactly how IT infrastructure will be restored. Must consider cost, security, compatibility, and RTO. |
| **Step 5: Plan testing, training, and exercises** | Test the plan regularly. Train staff on their roles. Run exercises to find weaknesses. Update the plan. |

---

## 12.3 Backup Types

| Type | Simple Description |
|------|--------------------|
| **Full Backup** | Complete copy of ALL data. Slowest to perform, uses most storage. Fastest recovery — only needs one backup. |
| **Incremental Backup** | Only backs up data changed since the LAST BACKUP (full or incremental). Fastest, uses least storage. Slowest recovery — needs full backup PLUS all incrementals. |
| **Differential Backup** | Backs up all data changed since the LAST FULL BACKUP. Slower than incremental, uses more storage. Faster recovery than incremental — needs full backup PLUS the latest differential only. |

> *3-2-1 Backup Rule: Keep 3 copies of data, on 2 different types of media, with 1 copy off-site or in the cloud.*

---

## 12.4 Recovery Best Practices

- Store backup copies at an OFF-SITE location (cloud is a ready option)
- Keep a record of ALL changes made to IT systems — makes updating the contingency plan easier
- Use proactive monitoring to detect disasters early and start recovery faster
- Implement fault-tolerant systems — systems that keep working if one component fails (e.g., RAID for disks)
- Regularly TEST the process of restoring a system from a backup — do not wait for a real disaster

> *RAID (Redundant Array of Independent Disks) = fault-tolerant disk technology. If one disk fails, data is still available from other disks. (PYP Q34)*

| Term | Definition |
|------|------------|
| **Contingency Plan** | A plan of action to help an organisation respond effectively to a significant future event that may or may not happen. *(PYP Q35)* |

---

# MODULE 13: SECURITY POLICY AND STANDARDISATION

## 13.1 What is a Security Policy?

NIST defines a security policy as:

- A set of rules for how to provide security services
- A statement that describes what information needs to be protected
- A set of rules that controls all security-related behaviour in a system
- A document that sets the goals and limits for the security program

| Term | Definition |
|------|------------|
| **Security Policy** | A formal document with rules for keeping an organisation's information safe. It should protect the CIA Triad. |

A security policy should include: industry standards, procedures, guidelines and best practices, and well-defined scopes.

---

## 13.2 Policy vs Standard vs Procedure vs Guideline

| Document Type | Simple Description |
|---------------|--------------------|
| **Policy** | High-level rules from management. Everyone MUST follow. Says WHAT must be done. Example: 'All sensitive data must be encrypted.' |
| **Standard** | Technical details that MUST be followed to meet the policy. More detailed than a policy. Says HOW requirements are met. |
| **Procedure** | Step-by-step instructions for a specific task. Everyone MUST follow. Says the EXACT STEPS to take. |
| **Guideline** | Recommended best practices — NOT required. People can choose to follow them. Example: 'It is recommended to lock your screen when you walk away.' |
| **Best Practices** | Well-known, widely used methods from industry. Not required but widely adopted. |

> *Memory help — from most strict to least strict: **Policy > Standard > Procedure > Guideline > Best Practice***

> **⚠️ EXAM TRAP:** Procedure is MORE TECHNICAL than policy — **FALSE**. STANDARD is more technical than policy. Policy = high-level WHAT. Standard = technical HOW. Procedure = step-by-step STEPS. *(PYP Q19)*

> **⚠️ EXAM TRAP:** Policy can sometimes NOT be enforced — **FALSE**. Policy MUST always be enforced. *(PYP Q19)*

---

## 13.3 Security Awareness Program

Teaches all employees how to behave securely. A key part of a security policy.

- Users remember security rules more easily when REAL SCENARIOS and examples are used in training
- The program must comply with legal requirements (e.g., GDPR Accountability principle requires staff training)
- Security awareness training is as important as technical controls — both are needed together

> **⚠️ EXAM TRAP:** Security awareness training CANNOT be considered the main protection as technical controls are more important — **FALSE**. Both are important and work together. *(PYP Q29)*

---

## 13.4 CCE — Common Configuration Enumeration

| Term | Definition |
|------|------------|
| **CCE (Common Configuration Enumeration)** | A standard list of system configuration issues with unique ID numbers. Used to harden systems by identifying and fixing known insecure configurations. |

- Hardening = making a system more secure by removing unnecessary features, fixing misconfigurations, applying security settings
- Used with vulnerability scanners to check if systems are configured securely

---

## 13.5 ISO 27001

ISO 27001 is the international standard for an ISMS (Information Security Management System). The main goal is to protect the CIA Triad. Organisations can get certified to show they follow this standard.

---

## 13.6 GPO — Group Policy Object

| Term | Definition |
|------|------------|
| **GPO (Group Policy Object)** | A collection of settings that defines how computers and users in a group behave. Pushed to users and computers through Active Directory via OUs. |

- Example uses: force strong passwords, disable USB ports, control which software can be installed, configure Windows Firewall
- Group policies can be segmented using OUs — different OUs get different GPOs
- GPO changes are NOT permanent — they can be updated or reversed at any time

> **⚠️ EXAM TRAP:** A change in Group Policy in AD is PERMANENT — **FALSE**. GPO changes can be modified or removed at any time. *(PYP Q30)*

---

## 13.7 Active Directory (AD)

| Term | Definition |
|------|------------|
| **Active Directory (AD)** | A Microsoft service for Windows networks. Stores and organises all users, computers, and devices. Handles login (authentication) and access rights (authorisation). |

| Part | Simple Description |
|------|--------------------|
| **Object** | A single item in AD — a user, computer, printer, or shared folder. |
| **Domain** | A group of objects. The main container in AD. |
| **OU (Organisational Unit)** | A smaller container inside a Domain. Used to group related objects. Different GPOs can be applied to each OU. |
| **Domain Tree** | Multiple domains in a parent-child structure. Example: company.com → dubai.company.com → london.company.com. |
| **DNS in AD** | Follows the same tree structure as the domain. DNS in AD is hierarchical. |

**Trust relationships between domains:**

| Trust Type | Simple Description |
|------------|--------------------|
| **Default: Transitive Two-Way Trust** | The DEFAULT relationship between parent and child domains. Both trust each other AND the trust extends through the whole tree. |
| **One-Way Trust** | Domain A trusts Domain B, but Domain B does NOT trust Domain A. Must be set up manually. |
| **Non-Transitive Two-Way Trust** | Both domains trust each other but the trust does NOT extend to other domains in the tree. |

> **⚠️ EXAM TRAP:** The default trust between parent and child domain is a ONE-WAY trust — **FALSE**. The default is a TWO-WAY TRANSITIVE trust. *(PYP Q30)*

---

## 13.8 NIST SP 800-53 and Flexibility

- NIST SP 800-53 is a set of baseline security controls for US federal systems
- NIST SP 800-53 DOES allow organisations to have flexibility in applying baseline controls — organisations can tailor them to their own risk environment
- Organisations are NOT forced to follow every control rigidly

> **⚠️ EXAM TRAP:** NIST SP 800-53 organisations are NOT allowed to have flexibility — **FALSE**. NIST SP 800-53 deliberately allows flexibility. *(PYP Q22)*

---

## 13.9 Whitelisting vs Blacklisting

| Method | Simple Description |
|--------|--------------------|
| **Whitelisting (Allowlisting)** | Only programs/IPs/users on the APPROVED list are allowed. Everything else is blocked. More secure but harder to manage. |
| **Blacklisting (Blocklisting)** | Only programs/IPs/users on the BLOCKED list are stopped. Everything else is allowed. Easier to manage but weaker. |

---

# MODULE 14: VULNERABILITY MANAGEMENT

| Term | Definition |
|------|------------|
| **Vulnerability** | The state of being exposed to an attacker who can maliciously gain full access to a network or system. (CVE definition) |
| **Exposure** | A mistake in software code or configuration that provides an attacker with INDIRECT access to a network or system. (CVE definition) |
| **CVE (Common Vulnerabilities and Exposures)** | A publicly available catalogue of known security vulnerabilities and exposures. Each entry has a unique CVE ID. Maintained by MITRE and supported by the US Department of Homeland Security / US-CERT. Lets security administrators quickly find technical information about a specific threat across multiple sources. |

## 14.1 Five Phases of Vulnerability Management Strategy

| Phase | Simple Description |
|-------|--------------------|
| **Phase 1: Asset Inventory** | Create a complete list of all computing devices and systems the organisation has. This helps track which devices need security software and patches. A small team is responsible for keeping the inventory up to date. Best practices: establish one person/group as the single point of authority for the inventory; use consistent abbreviations; validate the inventory at least once a year. |
| **Phase 2: Information Management** | Gather and share information about intrusions and attackers with the right people. Tools: CERT Coordination Center, Security Focus, Symantec Security Response. Mailing lists can be set up so incident responders get alerts first, then other users are informed after the incident is confirmed. |
| **Phase 3: Risk Assessment** | Perform an in-depth analysis of vulnerabilities and prioritise which ones to fix first. The 6 sub-stages are: (1) Scope identification, (2) Collecting data, (3) Analysis of policies and procedures, (4) Vulnerability analysis, (5) Threat analysis, (6) Analysis of acceptable risks. Best practices: document ways to review new vulnerabilities as they appear; publish risk ratings; keep asset inventory updated; have a strict change management process. |
| **Phase 4: Reporting and Remediation Tracking** | Report vulnerabilities to asset owners. Track whether vulnerabilities have been fixed. Separate reports for technical staff and non-technical management (different audiences need different levels of detail). Fix vulnerabilities in order of SEVERITY — highest risk first. Agree with management on remediation timeframes and what happens if vulnerabilities are not fixed. |
| **Phase 5: Response Planning** | Plan how to respond to vulnerabilities. This feeds back into the IR process and improves the overall security posture. |

---

## 14.2 Vulnerability Management Tools

| Tool Category | Description + Examples |
|---------------|------------------------|
| **Asset Inventory Tools** | Record all computing assets to make tracking and updating easier. Examples: Peregrine tools, LANDesk Management Suite, StillSecure. |
| **Information Management Tools** | Share information about threats and attackers with the right people. Examples: CERT Coordination Center, Security Focus, Symantec Security Response. |
| **Vulnerability Analysis Tools** | Scan networks to find and assess vulnerabilities. The two most commonly used: Nessus (deep vulnerability assessment — finds OS versions, missing patches, relevant exploits, sorts by threat level) and Nmap (quickly maps a network and finds asset vulnerabilities using its scripting function). |
| **Reporting and Remediation Tracking Tools** | Generate reports for different audiences. Examples: Foundstone Enterprise Manager, Latis Reporting Tool. Both provide customisable reporting for technical and non-technical stakeholders. |

---

## 14.3 Remediation Phase

| Term | Definition |
|------|------------|
| **Remediation** | The phase that completes or follows up on previous vulnerability analyses that were cut short. It is the process of actually FIXING the identified vulnerabilities. *(PYP Q9 answer)* |

- Remediation must be performed in order of severity — fix the most dangerous vulnerabilities first
- The IR team must agree with management on remediation timeframes and required resources
- Consequences of NOT remediating must be communicated clearly

> **Exam Tip:** Remediation = the phase for completing premature (unfinished) vulnerability analyses. This was Q9 in the PYP.

---

# QUICK REFERENCE: KEY TERMS

| Term | Simple Meaning |
|------|----------------|
| **Anonymity** | Not being identified at all when interacting with a service (APP2). |
| **Pseudonymity** | Using a fake name instead of your real name (APP2). |
| **Buffer Overflow** | Sending more data than a buffer can hold — overwrites nearby memory. Used for privilege escalation. Example: EternalBlue. |
| **Chain of Custody** | A record proving evidence has not been changed or tampered with. |
| **CCE** | Common Configuration Enumeration — standard list of system configuration issues used for hardening. |
| **Contingency Plan** | A plan of action for a significant future event that may or may not happen. |
| **Defence in Depth** | Multiple layers of security so no single failure compromises the whole system. |
| **DMZ** | Demilitarised Zone — network zone between the internet and the internal network. |
| **EternalBlue** | NSA-made exploit targeting a Windows SMBv1 buffer overflow. Used in WannaCry. |
| **ETTD / ETTR** | Estimated Time to Detection / Recovery — Blue Team metrics. |
| **False Positive** | An IDS alert triggered when there is NO real attack — legitimate activity flagged as malicious. |
| **Fuzzing** | Testing technique using invalid/random inputs to find software weaknesses. |
| **Hash Function** | One-way mathematical function — easy to compute, hard to invert, collision-resilient. |
| **IOC** | Indicator of Compromise — evidence that a system has been attacked. |
| **Kill Chain** | 5-step attacker method: Recon → Compromise → Lateral Movement → Privilege Escalation → Conclude Mission. |
| **MFA** | Multi-Factor Authentication — uses two or more factors to verify identity. |
| **MTTC / MTPE** | Mean Time to Compromise / Privilege Escalation — Red Team metrics. |
| **NIST** | National Institute of Standards and Technology (USA) — publishes widely used cybersecurity frameworks. |
| **Patch Management** | Regularly applying software updates to fix known security weaknesses. |
| **Personal Data (GDPR)** | Any information relating to a person who can be identified. |
| **RAID** | Redundant Array of Independent Disks — fault-tolerant disk technology. |
| **Ransomware** | Malware that encrypts files and demands money to unlock them. |
| **RTO / RPO** | RTO = maximum downtime allowed. RPO = maximum data loss allowed. |
| **SAR** | Subject Access Request — how a person asks a company what data it holds about them under GDPR. |
| **Shadow IT** | Systems built by individual departments without central IT's knowledge or approval. |
| **SMB Relay Attack** | Attacker captures and replays authentication data to log in as a victim without knowing their password. |
| **Social Engineering** | Tricking people psychologically to bypass security. Attacks humans, not technology. |
| **Spear Phishing** | Targeted phishing aimed at a specific person/org. 70% success rate. |
| **TTP** | Tactics, Techniques, and Procedures — describes HOW attackers operate. |
| **VLAN** | Virtual Local Area Network — logical (software-based) network split on shared physical hardware. |
| **CVE** | Common Vulnerabilities and Exposures — a public catalogue of known security weaknesses with unique ID numbers. |
| **Data Exfiltration** | Stealing sensitive data from an organisation and taking it outside. Attackers often sell this data or use it for blackmail. |
| **Dynamic Code Obfuscation** | Malware changes its own code to avoid detection by signature-based antivirus. Used at the Concluding the Mission stage. |
| **Hypervisor** | Software that creates and manages virtual machines (VMs). Examples: VirtualBox, VMware. |
| **Metamorphic Virus** | A higher-level polymorphic virus that can completely rewrite itself each time. Very hard to detect. |
| **NTA (Network Traffic Analysis)** | An anomaly-based detection system that analyses network traffic to detect malicious insiders and compromised systems. |
| **Obfuscation** | Attackers covering their tracks after an attack to confuse or slow down forensic investigators. |
| **Polymorphic Virus** | A virus that changes its own code each time it copies itself — makes signature-based detection harder. |
| **Sustainment** | The phase where an attacker stays hidden inside a victim's network even after stealing data, to keep access for future use. |
| **UEBA (User and Entity Behaviour Analytics)** | An anomaly-based detection system that profiles normal user behaviour and alerts on deviations. |
| **Write-Blocker** | A device that lets you read evidence storage without writing any data to it — preserves evidence. |
| **Zero Trust** | Security model: never automatically trust anyone, always verify — even users already inside. |

---

# PYP ANSWER KEY — ALL 40 QUESTIONS

> *Use this to quickly check your answers. The correct answer and a short reason are shown for each question.*

| Question | Answer + Simple Reason |
|----------|------------------------|
| **Q1 — a (1 only)** | CTI is used in IR = TRUE. Statement 2 wrong (defending ALL threats is impractical). Statement 3 wrong (IOCs = machine-readable; TTPs = human-readable). Statement 4 wrong (TTPs are human-readable not machine-only). Statement 5 wrong (MS Threat Intel DOES use botnet data). |
| **Q2 — a (3 and 5)** | IaaS customers must review cloud provider policy = TRUE. For containment, revisit cloud provider isolation capabilities = TRUE. Statement 1 wrong (SaaS, not IaaS, has most IR info with cloud). Statement 2 wrong (highest responsibility = IaaS). Statement 4 wrong (IaaS customers DO have full OS log access). |
| **Q3 — c (1, 2 and 4 are incorrect)** | Statement 4: fuzzing uses INVALID inputs, not valid = INCORRECT. Metasploit provides exploits/payloads = TRUE. msfvenom generates backdoor payloads = TRUE. |
| **Q4 — e (2 only)** | Hackers DO sell stolen data = TRUE. Statement 1 wrong (Nmap is NOT a password cracker). Statement 3 wrong (phishing IS external recon). Statement 4 wrong (inefficient neutralisation = false negatives, not false positives). Statement 5 wrong (discovery uses both software and human analysis). |
| **Q5 — a (None of the options are incorrect)** | ALL 5 statements are TRUE: behaviour analytics = defence layer; traditional mindset = high-profile users; large requests for same file = IOC; attackers target regular users; infected hosts use port 80 for C2 disguised as DNS. |
| **Q6 — b (2, 4 and 5)** | Baiting = leaving infected USB = TRUE. Guessing passwords from social media = TRUE. Social engineering beyond security tools = TRUE. Statement 1 wrong (lever is 'liking', not 'sincerity'). Statement 3 wrong (watering hole targets specific groups, NOT general public). |
| **Q7 — User Account Control (UAC)** | Windows feature for giving programs permission to run with admin-level privileges. |
| **Q8 — d (3, 4 and 5)** | Internal recon determines security mechanisms = TRUE. Sniffing tools capture packets in readable format = TRUE. Wireshark = internal recon tool = TRUE. Statement 1 wrong (internal recon = ONSITE, not off-site). Statement 2 wrong (not simply called 'an active attack'). |
| **Q9 — Remediation** | The phase for completing unfinished vulnerability analyses. |
| **Q10 — b (3 and 4 are incorrect)** | VLANs are LOGICAL not physical (Statement 3 = wrong). Data CAN flow between segments via a router (Statement 4 = wrong). |
| **Q11 — Kerberos TGT (KRBTGT)** | Microsoft's Kerberos account targeted in pass-the-ticket attacks. |
| **Q12 — d (2 and 3 are incorrect)** | Shadow IT REDUCES IT visibility (Statement 3 = wrong). Statement 2 also incorrect per answer key. |
| **Q13 — c (1 and 3)** | BA £183m GDPR fine in 2018 = TRUE. 'Confidentiality' = 'secrecy' in cryptography = TRUE. Statement 4 wrong (privacy = individual; confidentiality = organisation — reversed in the exam question). |
| **Q14 — a (All of the options are incorrect)** | Targeted attacks are NOT short. Private sector cannot ignore govt attacks. ETTD = Blue Team not Red. Prevent-breach does NOT promote ongoing testing. 2FA CAN be compromised. |
| **Q15 — a (3)** | Defence in depth DELAYS attacks = TRUE and correct. |
| **Q16 — b (All of the options are incorrect)** | Data exfiltration IS an option for lateral movement. Attackers try NOT to raise alerts. Lateral movement happens AFTER compromise. Movement crosses different systems. Lateral movement is LONG-TERM not short-term. |
| **Q17 — d (4 — Analysis of recovery plan)** | Risk assessment stages: scope ID, collecting data, analysis of policies/procedures, vulnerability analysis, threat analysis, analysis of acceptable risks. 'Analysis of recovery plan' is NOT a stage. |
| **Q18 — a (1 and 3)** | Small orgs aggregate by department = TRUE. SSH recommended for managing switches = TRUE. Cross-VLAN NOT for large networks. NAC DOES do authentication. VM security should NOT be relaxed. |
| **Q19 — b (2 and 5)** | Policy should have well-defined scope = TRUE. Policy can include industry standards = TRUE. Statement 1 wrong (policy updated when needed, not only on a schedule). Statement 3 wrong (procedure is more technical, not policy). Statement 4 wrong (policy MUST always be enforced). |
| **Q20 — b (4 — Assessment)** | IR foundational areas: Scope, Objective, Roles, Definition/Terminology. 'Assessment' is NOT one of them. |
| **Q21 — a (1 only)** | Horizontal privilege escalation via credential compromise = TRUE. Statement 2 wrong (horizontal = same-level, not root). Statement 3 wrong (vertical techniques vary). Statement 4 wrong (admin should NOT be given to normal users). Statement 5 wrong (token copying IS possible in Windows). |
| **Q22 — b (4 only)** | NIST SP 800-53 DOES allow flexibility. Statement 4 says organisations are NOT allowed to have flexibility = INCORRECT. |
| **Q23 — Accountability** | GDPR principle requiring staff training and evaluating data handling processes. |
| **Q24 — EternalBlue** | NSA-developed exploit, basis of WannaCry ransomware. |
| **Q25 — c (5 only)** | Recording every step of IR IS necessary. Statement 5 says it is unnecessary = INCORRECT. |
| **Q26 — c (1, 3, 4 and 5)** | WannaCry = extortion. Data manipulation = integrity failure. Backdoors bypass firewalls. MITM on smartphone web apps = TRUE. Statement 2 wrong (selling data is NOT simpler than blackmail — it is more complex). |
| **Q27 — Virtual Private Network (VPN)** | Secure private channel between corporate and remote networks. |
| **Q28 — Subject Access Request (SAR)** | GDPR right to know what personal data a company holds about you. |
| **Q29 — e (None of the options)** | All 5 statements contain errors. BYOD failures = insecure implementation. BYOD-to-premises connectivity must be considered. Google Docs = SaaS not PaaS. Compromised BYOD CAN compromise SaaS data. Security awareness IS important. |
| **Q30 — e (2, 4 and 5)** | DNS in AD is hierarchical = TRUE. GPO defines system behaviour = TRUE. OUs segment group policies = TRUE. Statement 1 wrong (default = TWO-WAY trust). Statement 3 wrong (GPO changes are NOT permanent). |
| **Q31 — Hacktivism** | Hacker group expressing political preference or supporting a cause. |
| **Q32 — a (1 and 3 are incorrect)** | NIDS does NOT fully shield against individual-target internal recon. Sysinternals does NOT alert remote users. Statements 2, 4, 5 are TRUE. |
| **Q33 — b (1 and 2)** | Reverse engineering = assembly from machine code = TRUE. Buffer overflow = not observing memory restrictions = TRUE. Statements 3, 4, 5 are incorrect. |
| **Q34 — Redundant Array of Independent Disks (RAID)** | Disk redundancy technology for servers. |
| **Q35 — Contingency Plan** | Course of action for a significant future event that may or may not happen. |
| **Q36 — b (2, 3 and 5)** | WMI used in Sony Pictures hack = TRUE. Scheduled tasks used to steal data = TRUE. PowerShell deployed as scheduled tasks = TRUE. Statement 1 wrong (Registry CAN be remotely modified). Statement 4 wrong (WMImplant NOT made by Microsoft). |
| **Q37 — b (2 only)** | Thorough DR plan considers worst-case scenario = the only fully correct statement. All others contain errors. |
| **Q38 — a (3 and 5)** | NIDS placed at strategic network points = TRUE. Anomaly-based IDS establishes a baseline = TRUE. Statement 1 wrong (Petya IOC = ports 137/139/445, not 443/445). Statement 2 wrong (HIDS monitors the HOST, not just subnet). Statement 4 wrong (describes signature-based detection). |
| **Q39 — c (5 only)** | Botnets DO include IoT devices. Statement 5 says they do not = INCORRECT. |
| **Q40 — e (5 only)** | Statement 5: most credentials = username + password = TRUE. Other statements are wrong: hackers DO rent bots; DDoS is NOT stealthy; traditional perimeter is NOT sufficient. |
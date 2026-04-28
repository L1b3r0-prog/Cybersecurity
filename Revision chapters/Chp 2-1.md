## Steps for compromising a system
1. Deploying payload
2. Compromise OS
3. Compromise web-based system

Steps will vary according to attacker's mission

## Deploying payloads
Metasploit
- Hive of exploits and payloads used against different vulnerabilities that hacker has already identified using tools like Nessus Scanner
- Framework console can be booted up by running msfconsole in terminal.
  - Paylod is setup using command with IPa of target
- Payload is generated using msfvenom command
  - Creates backdoor payload such as window command shell or reverse TCP stagger
  - Backdoors can be distributed via phsihing emails


Exploiting vulns
- Can be errors in the authentication code
- Bugs within account management system
- Unforseen errors by devs

## Zero day
It uses advanced vuln discovery tools and techniques to identify vulns not yet know by sw devs

Done via fuzzing and source code analysis

Fuzzing
- Automated testing technique for sw involving providing invalid, unexpected or random data as inputs to pc program
- Refers to system created by hacker to attempt to find vuln
- Often inefficient when dealing with large programs

Source code analysis
- Simpler and quicker
- Lower success rate as not easy to pinpoint errors from merely looking at code
- Uses automated tools such as Checkmarx
  - Scans code and quickly identifies, categorize and suggest countermeasures for vulns in code

Reverse engineering
- Generates assembly language source code from machine-executable code

## Zero day Exploits
Buffer overflow
- Caused by use of incorrect logic in system codes which writes data to buffer memory but not to observe memory restrictions of buffer
- Writing data past limit will crash the system

Structured exception handler overwrites
- Structures Exception Handling (SEH)
- Hackers attacks SEH logic causing it to correct non-existent errors and lead system to shutdown
- Sometimes used with buffer overflows

## Compromising OS
Hackers are insider threats
- People working inside orgs that have malicious intent
- Have advantage of being exposed to inside of org and know where to attack
- Are physically close to target and target machine when user is not attended
  - Third party tolls such as Kon-Boot, Hiren's BootCD or Ophcrack
  - Linux live cd
  - Preinstalled applications

Compromising with Live CD
- Enables hacker to access all files contained in win pc directly
- Boots target pc from DVD/thumb drive containing image of linux
- Unless hard disk is encrypted, all user files will be visible in plain text to be copied

Compromising with preinstalled apps
- Aim is to compromise windows programs
- By modifying commonly used apps so that when user runs it, malicious actions is performed instead

## Compromising web-based systems
Contains highly valuable and sensitive data and ways to compromise are
- SQL injection
- Cross-site scripting
- Broken authentication
- DDoS attacks

SQL injection
- Targets execution of input provided by users on backend for websites coded in PHP and SQL
- Hackers supply inputs that manipulates execution of SQL statement, causing compromise to occur at backend and exposing underlying DB

XSS
- Exploits input fiels of website if not sanitized.
- Used to steal cookies and sessions as well as display alert boxes
- Stored XSS is a variant where hacker stores a malicious XSS script in the HTML of page/DB and is executed when user loads affected page

Broken auth
- Allows attackers to capture or bypass authentication methods used by web app
- Common attack in publicly shared pc
- Websites establish sessions and stores cookies but don't delete when user closes browser without logging out

DDoS attacks
- Main aim is to bring down a server or to create diversion to commit another malicious act such as stealing data

## Chasing user's identity
Identity is the new perimeter
- Trad network perimeter is not sufficient for security boundary of orgs
- Majority of new creds is only username and pw
- MFA is not default method for authentication

Growing trends of credential theft
- Hackers infiltrate without making noise using valid creds to authenticate network
- Targets user's bank cred using banking trojans

BYOD
- User identity for personal app resides in the same device that has corporate creds in use to access corporate-related data
- Might use same pw for different tasks

## Hash Function
A hash function is a mathematical algorithm that takes any input data (called a message) and converts it into a fixed-size output called a hash value, digest, or message digest.

Key properties
- Easy to compute
- Hard to invert
- Collision-resillience

Used for
- Storing passwords
- Integrity
- Efficiency
- Proof of work

## Strats for compromising user's identity
Attack plan should consider current threat landscape which includes three stages
1. Who can attack us
2. What are the most common attacks launched by adversaries
3. How the attacks are executed

Stage 1
- Red team performs self-assessment and understand what type of info company has and who benefits from obtaining it
- Might not be able to map all adversaries but red team can create basic adversary profile for next stage

Stage 2
- Many hacker groups have a pettern
- Understanding the category of the attack and how they are created, during the attack exercise, it can be emulated

Stage 3
- Red team is trying to be accurate with reality
- Red team emulates hacker's mindset
  - Attacker won't stop if fail to infiltrate on the first attempt
  - Would attack again using different techniques until successful

## Harvesting Credentials
Using identified unpatched vulns
- Such as CVE-2017-8563
- Allows elevation of privilege vulns due to kerberos' authentication failure
- Attackers potentially gains access to local admin acc through lateral movement

Using pass-the-hash attack
- Uses hashed pw directly instead of cracking it

Tools used  
  - Mimikatz is a tool that dumps hashes and clears text credentials straight from memory
  - Sysinternals is a suite to remotely access windows and execute commands

Brute force
- Attacker tries many passwords or passphrases with the hope of eventually guessing correctly

Social engineering
- Uses social engineering toolkit in kali linux to craft and distribute malware via email
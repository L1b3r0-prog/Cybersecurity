## Malware Classification
Malware is a program that is inserted into a system, usually covertly with the intent of compromising confidentiality, integrity or availability of victim's data, applications or OS which annoys or disrupts the victim

- Malware carries out cyberattacks including
  - Nation-state cyberwar
  - Cybercrime
  - Fraud
  - Scam


## Characteristics of different malwares
Types of malware includes
- Virus
- Worms
- Trojans
- Spyware
- Botnet Malware
- Ransomware

### Different categories
Needing a host program or standalone
- Viruses vs Worms & Bots

Able to replicate
- Viruses & Worms vs Trojans & Spam emails

Variety of actions/payloads used when target is reached
- Payload actions performed once target system is reached can include corruption of system or data files
- Corruption of system or data files vs Theft of service vs Theft of info

### Virus
Piece of sw that infects other programs or any type of executable content by modifying them

Requires host program or file to execute

Main components:
- Infection mechanism: How virus spreads/propogates enabling it to replicate. Known as infection vector
- Trigger: Event or condition that determines when payload is activated/deactivated, known as logic bomb
- Payload: What virus does besides spreading. Payload may involve damage or benign but noticeable activity

### Phases
- Dormant: Idle, waiting for trigger
- Propagation: Virus places copy of itself into other programs or into certain system areas on the disk
- Triggering: Virus activated to perform the function for which it was intended
- Execution: Function is performed

### Classification of Virus
Two classifications that are based on
- Type of target virus tries to infect
- Method used to conceal itself from detection

By target:
- Boot sector infector: Infects master boot record or boot record and spreads once system is booted from the infected disk
- File infector: Infects files that OS or shell considers to be executable
- Macro virus: Infects files with macro or scripting code that is interpreted by an application
- Multipartite virus: Infects files in multiple ways, infecting multiple type of files

By concealment strategy:
- Stealth: Desgined to hide itself from detection by anti-virus sw. Entire virus and not just payload is hidden
- Encrypted: Uses encryption to obscure its content
- Polymorphic virus: Changes from each time they are inserted into other program
- Metamorphic virus: Higher order of polymorphic. Not only changes forms between transistions, but can also be completely re-written

### Worms
Program that self-propogates/replicates across systems by arranging to have itself immediately executed, creating additional new instances of itself

Usually exploits sw vulns in client or server programs to gain access to each new system

Standalone and doesn't need host program

### Replication
Electronic mail or instant messenger facility: Worm emails a copy of itself to other systems, or sends itself as an attachment via instant message service

File sharing: Worm either creates a copy of itself or infects other suitable files as virus on removable media such as USB drive

Remote execution capability: Worm executes copy of itself on another system, either by using explicit remote execution facility or by exploiting a program flaw in a network service to subvert its operations

Remote file access or transfer capability: Worm uses remote file access or transfer service to another system to copy itself from one system to another

Remote login capability: Worm logs onto remote system as a user and then uses commands to copy itself from one system to the other

Remote login capability: Worm logs onto remote system as a user and then uses commands to copy itself from one system to another

### Rapid propagation
Worms can potentially spread quickly as they parallelize the process of propagating

Virus is the same but slower spread as they require user action to trigger each propagation

## Trojan Horse
Sw that appears to perform desirable function but is actually designed to perform undisclosed malicious functions. Doesn't self-replicate

### Concealment method
- Trojan renames itself to the name of valid system file
- Can also be encrypted and polymorphic and could install themselves in different ways to escape detection

## Backdoor
Secret entry point to program that allows someone to gain access without going through the usual security access procedures
- Programmers use backdoors to debug and test programs
- Can be used to gain unauthorised access

Usually implemented as network service listening on non-standard port that attacker can connect to and issue commands through to be run on the compromised system

Difficult to implement OS system controls for backdoors in application

## Ransomware
Attacks availability of data, usually by encrypting files and demands payment for the decryption key

## Extras
Potentially unwanted programs (PUP)
- Piece of code that is part of a useful program that can collect user data without consent
  - sits in legal grey area but is considered as malware from cybersecurity standpoint

Logic Bomb
- Program that performs malicious action when specific external event occurs
  - presence or absence of certain files or devices of the system
  - particular day of the week or date
  - particular version or config of some sw
  - particular user running the app
- Once triggered, may alter or delete data or files causing machine or other damage

## Countermeasures for malware
How malware works
- Acts as both data and instructions
  - Inserts code (set of instructions) into another program
  - Executes itself where the instructiosn is treated as an executable
- Protections: treat all programs as data by default which only allows execution after trusted certifying authority verifies them

Against malicious code assuming the identity of a user
- Limit the objects accessible to a given process run by the user
  - Reducing the rights
  - Sandboxing

Sandboxing can be used
- Virtual environment to contain malicious behaviour

Restrict domain sharing
- Prevent users in different protection domains from sharing programs or data

## Detection
Behaviour monitoring
- Works for all viruses
- Detection is before (complete) infection
  - Sensitivity of the monitor is set to high and may generate many false alarms

Signature scanning
- Matches known virus signatures against a library
- Simple and effective against known threats
  - Can't find new viruses before patterns are known
  - Ineffective against polymorphic viruses
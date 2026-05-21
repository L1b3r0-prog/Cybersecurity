Chp 1-3
══════════════════════════════════════════════════════

## External Reconnaissance

---

### Dumpster Diving
Organizations dispose of obsolete devices via bidding, recyclers or dumping in storage.

**Info attackers can obtain from improperly disposed devices:**
- Internal setup of the organization
- Openly-stored passwords on browsers
- Privileges and details of different users
- Access to bespoke systems used in the network

**Disposal methods:**
| Method | Notes |
|--------|-------|
| Crusher | Google's method — renders hard drives physically unreadable |
| Degaussing | Reduces/eliminates magnetic field/data on hard drives — does NOT work on SSDs |
| Encryption | Suggested method for SSDs — no standard method exists |

---

## Social Media
Currently the best place to mine data concerning specific targets
- Data related to companies user is working at
- Details about family members, residence and contact info

### Identity Theft
- Easy to create fake accounts bearing another person's identity
- Uses victim's picture and up-to-date details
- Account impersonates high-level org officials to request:
  - Network info and stats from IT department
  - Security info of the network
- Hackers can guess passwords or answers to secret questions through social media posts

---

### Social Engineering
> ⚠️ Company can't completely protect itself — beyond the protection of security tools (exploiting human nature)
> Humans are sympathetic, trusting of friends, show-offs and obedient to higher authorities making them open to attacks through manipulation of information

#### 6 Levers of Social Engineering

| Lever | Description | Example |
|-------|-------------|---------|
| Reciprocation | Victim feels obligated to return a favour | Attacker does something nice, victim reciprocates |
| Scarcity | Threatens short supply of something target needs | Fake mega sale, limited trip package |
| Consistency | Humans honour promises and stick to usual flow | Attacker clones known IT vendor, delivers malware-infected electronics |
| Liking | More likely to comply with people they like | Attacker appears attractive or friendly |
| Authority | Most obedient to those ranked above them | Victim gives login credentials or sensitive data over unsecured channels |
| Validation | Comply if others are doing the same | Social proof manipulation |

---

### Social Engineering Attacks

#### Pretexting
- Construction of an elaborate, well-researched lie to appear legitimate
- Impersonates imaginary boss or trusted individuals (police officers, debt collectors, etc.)

#### Diversion Theft
- Persuades delivery/transport companies that deliveries are requested elsewhere

#### Phishing
- **Vishing:** done via phone calls using illegitimate interactive voice response systems
  - Sounds like banks or service providers
  - System rejects input to ensure multiple PINs are disclosed
- **Spear Phishing:** specifically targeted at particular end users
  - Performs background checks on targets
  - Success rate: Normal phishing **3%** vs Spear phishing **70%**

### Water holing
- Strat where attacker guesses or observes websites group often (org, industry or region) uses and infects one or more with malware
- Attacker may only attack users coming from specific IPa
- Looks for specific information

#### Baiting
- Exploits greed/curiosity of targets
- Attacker leaves malware-infected external storage where it can be easily found
- May install rootkit viruses that activate when infected media is connected
- High success rate due to human nature

#### Quid Pro Quo
- Commonly carried out by low-level attackers
- Attacker calls random numbers claiming to be tech support
- Offers help → gains access to victim's PC or launches malware

#### Tailgating
- Least common but significant success rate
- Attacker walks behind employee with legitimate access
- Enters by borrowing RFID card or using fake card under guise of accessibility problems

---

## Internal Reconnaissance
Tools used to determine security mechanisms in place

### Sniffing and Scanning Tools

| Tool | Description |
|------|-------------|
| Prismdump | Linux only — sniffs with Prism2 chipset card, captures packets to pcap format |
| Tcpdump | Most powerful packet-filtering capabilities, selectively captures packets |
| Wireshark | Most popular sniffing tool — user-friendly interface, powerful packet interpretation |
| Nmap | Maps out hosts in network to discover valuable targets — slower scans bypass monitoring |
| Nessus | Best vuln scanner for white hats — detects misconfigs, missing patches, weak/default passwords |

---

## Compromising Systems — Current Trends of Attack

### Extortion
- Holding PC files for ransom
- Threatening to release damaging info about victim
- Examples: ransomware, threatening to hack sites

### Data Manipulation
- Compromises systems by manipulating data instead of deleting/releasing it
- Difficult to detect
- Single value change can have far-reaching consequences
- Targets: healthcare, financial and government data
- Can be used to spread misinformation to the masses

### Backdoors
- Hidden access points planted in firmware
- Can allow hackers to decrypt traffic flowing through firewalls

### IoT Device Attacks
- Exploits smart devices with weak security
- Manufacturers don't prioritize security
- Most users leave devices with default security config

### Mobile Device Attacks
- Mobile malware sends messages to generate revenue for hackers
- Steals personal info from victim's devices
- Browsers and web-supported apps vulnerable to:
  - Scripting attacks
  - Man-in-the-Middle (MitM) attacks

### Hacking Every Device
- Overlooked devices targeted (e.g. printers) to:
  - Extract password authentication mechanisms
  - Access sensitive data sent to be printed
  - Use as entry points into secured networks

### Hacking the Cloud
- Cloud stores everything: storage space, CPU cores, network interfaces
- Security left to cloud vendor
- Individual company's security control is limited on shared platforms
- Cloud is not the direct target — hacker compromises a user/system within the org
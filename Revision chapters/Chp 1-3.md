Chp 1-3
--------------------------------------------------------------------------------------------------------------
External Reconnaissance
What is Dumpster Diving
Organizations dispose of obsolete devices in a number of ways, such as through bidding, sending to recyclers, or dumping them in storage. There are serious implications for these methods of disposal.
By taking old external storage devices or obsolete computers which are not thoroughly handled, attackers may get the information like 
-	The internal setup of an organization 
-	Openly-stored passwords on browsers 
-	The privileges and details of different users 
-	Access to some bespoke systems used in the network
Google puts old hard drives into a crusher to render them unreadable
Degaussing is another way to reduce or eliminate unwanted magnetic field or data stored on hard drives but doesn’t work on SSD
No standard way for SSD, suggested method is encryption

Social Media
## Identity theft
-	Easy to create fake account bearing identity of another person
-	Picture and up to date details of victim
-	Acc is used on org high level officials where hacker can request
  -	Network info and stats from IT dpt
  -	Sec info of network
Hackers can guess pw or answers to secret qs through posts
 
## Social engineering
Company can’t completely protect itself from this type of threat as its beyond the protection of sec tools
6 levers of social engineering are: Reciprocation, Scarcity, Consistency, Liking, Authority and Validation
Reciprocation
-	Victim does something for social media user who in turn feels need to reciprocate favour
-	Human nature to feel obligated to return favour
Scarcity
-	Threatening short supply of something that target is in need of such as trip package, mega sale or new release of products
Consistency
-	Humans tend to honour promises to get used to usual flow of events
-	Eg. Attacker clone known vendor of IT team and deliver malware infected electronics
Liking
-	More likely to comply with request of people they like or appear attractive
Authority
-	Commonly used lever with high success rate
-	More obedient to authority of those ranked above them even if malicious
-	Eg. Giving login credentials or send sensitive data over unsecured channels
Validation
-	Readily comply and do something if other people are doing the same

## Social engineering attacks
Pretexting
-	Construction of elaborate lie that is well-researched to appear legit to the target
-	Attackers that uses pretexting have honed art of impersonating an imaginary boss/ trusted individuals in society such as police officers, debt collectors, etc
Diversion theft
-	Attackers persuade delivery and transport companies that deliveries and services are requested elsewhere
Phishing
-	Vishing is done using phone calls instead of emails where attacker will use illegitimate interactive voice response system that sounds like banks, service providers. Target is prompted by system to give verification info. Normal for system to reject input given by target to ensure several PINs are disclosed
-	Spear phishing is specifically targeted to obtain info from particular end users in org by performing number of background checks on targets
-	Statistically, normal phishing is 3% while spear phishing is 70%
Baiting
-	Exploiting greed/curiosity of certain targets
-	Attacker leaves malware-infected external storage device where it can be easily found
-	Files would be left for victims to be tempted to open
-	Attackers might install rootkit viruses that infects pc’s when booted while infected secondary storage media is then connected to them
-	High success rate due to human nature to be greedy/curious
Quid pro quo
-	Commonly carried out by low-level attackers
-	Attackers keeps calling random numbers claiming to be from tech sup and offer help, which gives attackers access to victim’s pc or ability to launch malware
Tailgating
-	Least common but significant success rate
-	Attacker walks behind employee that has legit access and enters behind them by borrowing RFID card or gaining entry by using fake card under guise of accessibility problems

## Internal reconnaissance
Tools used to determine security mechanisms in place that wards off hacking attempts
Sniffing and Scanning Tools
Prismdump
-	Only for linux which allows hackers to sniff with Prism2 chipset based card
-	Only captures packets and stores to pcap format
Tcpdump
-	Most powerful packet-filtering capabilities and can selectively capture packets
Wireshark
-	Most popular sniffing tools with user-friendly interface and powerful packet interpretation
Nmap
-	Attackers will try to map out hosts in network to discover ones containing valuable info
-	Slower scanning tools are used to get past network monitoring systems
Nessus
-	Best network scanners and vuln scanner for white hats
-	Scans network and shows connected devices that have misconfig and missing patches
-	Tool shows devices that are using default pw, weak pw or no pw and recovers pw from devices by launching external tool to help with dict attacks against targets in network

## Compromising systems – current trends of attack
Extortion, Data manipulation, Backdoors, IoT device, Mobile device, Hacking every device, Hacking cloud
Extortion
-	Holding pc files of ransom
-	Threatening to release damaging info about victim to public
-	Ransomware and threatening to hack sites are examples
Data manipulation
-	Compromise systems through manipulation of data instead of deleting or releasing it. Difficult to detect
-	Hacker changes single value but consequences can be far-reaching
-	Can happen on health care, financial and gov data
-   Can be used to provide misinfo to the masses
Backdoors
-	Hidden access points planted in firmware
-	Can allow hackers to decrypt traffic flowing through the firewalls
IoT device
-	Exploiting smart devices with weak security
-	Manufacturers don’t prioritize security of the devices and most users leave it with default security config
Mobile
-	Mobile malware sends msgs on victim’s phones to gen revenues for hackers and steal personal info from victim’s devices
-	Browsers and web-supported apps are vuln to scripting attacks and exploitable through mitm attacks
Hacking every device
-	Overlooked devices are attacked such as printers to extract password authentication mechanisms, sensitive data users send to be printed and used as entry points into secured networks
Cloud
-	Cloud vuln: stores everything; storage space, cpu cores and network interfaces
-	Security is left to cloud vendor such as the security environment
-	Security control of the individual company is limited with the use of the shared platform with other people
-	Cloud is not the direct target as the hacker compromises a user or system within the org

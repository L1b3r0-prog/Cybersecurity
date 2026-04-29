## Lateral movement
Attackers moving from device to device after initial intrusion in hopes of accessing high-valued data
- Also looks for ways to gain additional control of victim's netowrk
- Tries to not trigger alarms or raise any alerts

Attacks are carried out within org network, systems and premises
- Can take a long time, up to several months before hackers reach desired target device
- Involves scanning network for other resources, collecting and exploiting credentials or the collection of more info for exfiltration

## Sniffing tools
Free and open source utility for network discovery and security auditing

Wireshark, Tcpdump, Nmap and nessus are used

Nmap

Uses raw IP packets in novel ways to determine:
- Hosts available on network
- Services (application name and version) hosts are offering
- OS (and versions) they are running
- Type of packet filters/firewalls are used
- Dozens of other characteristics

Basic function of Nmap
- Basic command: nmap <option> <target IPa>

<option>
- TCP SYN scan (-sS)
- UDP scan (-sU)
- Scanning outputs will be open, closed, filtered, unfiltered or a combination

Timing options (-T)
- Paranoid (0)
- Sneaky (1)
- Polite (2)
- Normal (3)
- Aggressive (4)
- Insane (5)

Port specification
- Default is most common 1000 ports in random order
- Scans only defined ports (-p port range)
- Only 100 most common (-F)
- Don't randomize port numbers (-r)
- Scans most common N ports (--top-ports N)

Commands for script function would look like

nmap --script <script name> <target url or ip>


WannaCry
--------------------------------------------------------------------------------------------------------------
WannaCry is ransomware that encrypts files, disks, and locks computers, demanding Bitcoin to decrypt them.
It spreads via the Server Message Block (SMB) protocol over ports 445 and 139 — the same ports Windows machines use to share files over a network. This meant it could self-propagate across networks without user interaction (worm-like behaviour).
How it works 
1. Attacker uses a yet-to-be-confirmed initial attack vector 
2. WannaCry encrypts files in the victim’s machine using AES-128 cipher, deletes shadow copies. 
3. It then displays a ransom note requesting $300 or $600 in bitcoin 
4. Tor.exe is used by wannadecryptor.exe, initiating connections to tor nodes in order to connect back to the attacker (therefore making this extremely difficult, if not impossible, to track) 
5. IP address of the infected machine is checked; then IP addresses of the same subnet are scanned for additional vulnerable machines and connected to via port 445 TCP 
6. When a machine is successfully connected, data containing the exploit payload is transferred

Exploits WannaCry uses
> ETERNALBLUE (CVE-2017-0144)
•	An NSA-developed exploit leaked by Shadow Brokers on 14 April 2017
•	Exploits a flaw in SMBv1 on Windows, allowing attackers to execute arbitrary code remotely
•	Microsoft had already patched this on 14 March 2017 — weeks before the attack — but many systems were unpatched
DOUBLEPULSAR
•	Not an exploit itself — it's a backdoor implant, also leaked by Shadow Brokers
•	Delivered via EternalBlue; once installed, it allows a malicious DLL to be injected into memory on the compromised system
•	No patch exists for DoublePulsar itself; patching the delivery exploit (EternalBlue) is the mitigation

Indicator of compromise (IOCs) for WannaCry 
•	Hashes: ed01ebfbc9eb5bbea545af4d… 
•	URLs: http://146.0.32.144:9001 , http://188.166.23.127:443 ØIPs: 91.121.65.179, 89.40.71.149, … 
•	File names: wcry.exe, WanAcry.exe, wanacry.exe … 
•	Targeted extensions: .der, .pfx, .key, .crt, .csr, .p12, .pem

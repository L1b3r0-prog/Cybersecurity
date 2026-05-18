WannaCry
══════════════════════════════════════════════════════

## Overview
WannaCry is ransomware that encrypts files, disks and locks computers,
demanding Bitcoin payment for decryption.

Spreads via **SMB (Server Message Block) protocol** over ports **445 and 139**
— same ports Windows uses to share files — enabling self-propagation
across networks without user interaction (worm-like behaviour).

──────────────────────────────────────────────────────

## How It Works (Step-by-Step)

1. Attacker uses a yet-to-be-confirmed initial attack vector
2. WannaCry encrypts victim's files using **AES-128 cipher** and deletes shadow copies
3. Displays ransom note demanding **$300 or $600 in Bitcoin**
4. **tor.exe** used by **wannadecryptor.exe** to connect to Tor nodes
   → connects back to attacker (extremely difficult to track)
5. Infected machine's IP is checked → same subnet IPs scanned for
   additional vulnerable machines → connects via **port 445 TCP**
6. Exploit payload data transferred to successfully connected machines

──────────────────────────────────────────────────────

## Exploits Used

### ETERNALBLUE (CVE-2017-0144)
- NSA-developed exploit leaked by **Shadow Brokers** on 14 April 2017
- Exploits flaw in **SMBv1** on Windows → allows remote arbitrary code execution
- Microsoft patched on **14 March 2017** (weeks before attack) — many systems unpatched

### DOUBLEPULSAR
- Not an exploit — it's a **backdoor implant**, also leaked by Shadow Brokers
- Delivered via EternalBlue
- Once installed, injects malicious DLL into memory on compromised system
- No patch for DoublePulsar itself → patching EternalBlue is the mitigation

──────────────────────────────────────────────────────

## Indicators of Compromise (IOCs)

| IOC Type | Examples |
|----------|---------|
| Hashes | ed01ebfbc9eb5bbea545af4d… |
| URLs | http://146.0.32.144:9001, http://188.166.23.127:443 |
| IPs | 91.121.65.179, 89.40.71.149 |
| File Names | wcry.exe, WanAcry.exe, wanacry.exe |
| Targeted Extensions | .der, .pfx, .key, .crt, .csr, .p12, .pem |
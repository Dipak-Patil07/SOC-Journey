# 04: Cyber Defence Frameworks

## Pyramid of Pain
Shows how much it hurts an adversary when defenders deny them each type of indicator. Higher = harder for them to change.

```
        /\        TTPs                 (Tough!)
       /--\       Tools                (Challenging)
      /----\      Network/Host artifacts   (Annoying)
     /------\     Domain names         (Simple)
    /--------\    IP addresses         (Easy)
   /----------\   Hash values          (Trivial)
```

**Lesson:** blocking a file hash is trivial for an attacker to bypass (recompile the file). Detecting behaviour (TTPs) forces them to change how they operate.

## Cyber Kill Chain (Lockheed Martin)
1. Reconnaissance
2. Weaponisation
3. Delivery
4. Exploitation
5. Installation
6. Command & Control
7. Actions on Objectives

Useful for spotting *where* in an attack you caught something and which earlier or later stages to check.

## MITRE ATT&CK
A knowledge base of real-world adversary **tactics** (the "why") and **techniques** (the "how").
Enterprise tactics: Reconnaissance, Resource Development, Initial Access, Execution, Persistence, Privilege Escalation, Defense Evasion, Credential Access, Discovery, Lateral Movement, Collection, Command and Control, Exfiltration, Impact.

## Applying them to a phishing case
| Framework | Mapping |
|-----------|---------|
| Kill Chain | Phishing email = **Delivery** |
| ATT&CK | Initial Access: **T1566** Phishing (`.001` attachment, `.002` link) |
| ATT&CK | Credential Access, if a fake login page harvests credentials |
| Pyramid of Pain | Sender address and domain are low/mid pyramid; the kit's behaviour and reuse is higher |

# Week 1 — CTI Fundamentals: WannaCry Ransomware Attack

## Introduction

WannaCry (also known as WannaCrypt, WCry) was a global ransomware cyberattack
that occurred in May 2017. It exploited a Windows SMB vulnerability
(EternalBlue) to self-propagate across networks without any user interaction,
infecting an estimated 200,000+ computers in over 150 countries within days.
The attack has been officially attributed by the US, UK, and other
governments to North Korea, specifically to the Lazarus Group
(MITRE ATT&CK: **S0366** — associated with group **G0032**).

## Glossary

| Term | Definition | Relevance to WannaCry |
|---|---|---|
| **Ransomware** | Malware that encrypts a victim's files and demands payment for decryption | Core mechanism of the attack; demanded $300–$600 in Bitcoin |
| **Exploit** | Code that takes advantage of a software vulnerability | EternalBlue exploited CVE-2017-0144 (SMBv1 vulnerability) |
| **EternalBlue** | An NSA-developed exploit leaked by the Shadow Brokers group in April 2017 | Primary infection/propagation vector for WannaCry |
| **Worm** | Self-replicating malware that spreads across networks without user action | WannaCry behaved as a worm, unlike typical ransomware requiring a click |
| **Kill switch** | A hardcoded condition that, if met, stops malware execution | WannaCry checked an unregistered domain before encrypting; researcher Marcus Hutchins registered it, halting the spread |
| **IOC (Indicator of Compromise)** | An artifact (hash, domain, IP) indicating a system was compromised | Used to detect WannaCry samples and infrastructure |
| **C2 (Command & Control)** | Infrastructure used to control infected systems | WannaCry used Tor-based C2 for payment tracking |
| **Patch management** | Process of applying security updates to systems | Microsoft had released a patch (MS17-010) two months before the attack; unpatched systems were the main victims |
| **Attribution** | Process of identifying who is responsible for a cyberattack | WannaCry was attributed to Lazarus Group / North Korea by multiple governments |

## Threat Classification

| Threat Category | Description | Evidence / Source |
|---|---|---|
| Ransomware / extortion | Files encrypted, ransom demanded in Bitcoin | Europol, 2017 |
| Exploitation of unpatched vulnerability | Spread via SMBv1 (CVE-2017-0144), patched in MS17-010 (March 2017) | Microsoft Security Bulletin MS17-010 |
| Self-propagating worm | Automatic spread across local networks and internet-facing SMB ports | Symantec, Kaspersky technical reports |
| State-sponsored attack | Attributed to Lazarus Group (North Korea) | US DOJ indictment (2018), UK NCSC statement |
| Critical infrastructure impact | UK National Health Service (NHS) forced to cancel operations | NHS England incident report, 2017 |

## Sources
- MITRE ATT&CK — Software S0366 (WannaCry), Group G0032 (Lazarus Group)
- Microsoft Security Bulletin MS17-010
- Europol / UK NCSC public statements on WannaCry
- US Department of Justice indictment (2018) attributing WannaCry to North Korea

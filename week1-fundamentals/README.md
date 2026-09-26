# Week 1 — CTI Fundamentals: Lazarus Group

## Introduction

Lazarus Group (also tracked as APT38, Hidden Cobra, Guardians of Peace) is a
state-sponsored threat actor believed to be linked to North Korea. Active
since at least 2009, the group has evolved from destructive/espionage
operations into large-scale, financially motivated cybercrime — primarily
targeting cryptocurrency exchanges and financial institutions. It is one of
the most well-documented APT groups in MITRE ATT&CK (ID: **G0032**).

## Glossary

| Term | Definition | Relevance to Lazarus Group |
|---|---|---|
| **APT (Advanced Persistent Threat)** | A stealthy, long-term, state-sponsored or highly resourced threat actor | Lazarus is classified as a nation-state APT (North Korea) |
| **TTP (Tactics, Techniques, Procedures)** | Behavioral patterns describing how an attacker operates | MITRE ATT&CK documents dozens of TTPs specific to Lazarus |
| **IOC (Indicator of Compromise)** | Artifact (hash, IP, domain) signaling a system was compromised | Used to detect Lazarus malware in network/endpoint data |
| **C2 (Command & Control)** | Infrastructure used by attackers to control compromised systems | Lazarus uses fake job-offer sites and trojanized apps as C2 channels |
| **Supply Chain Attack** | Compromising a trusted vendor/software to reach its customers | Core Lazarus method (e.g., 3CX, AppleJeus campaigns) |
| **Watering Hole Attack** | Compromising a website frequented by the target to infect visitors | Used by Lazarus in targeted espionage campaigns |
| **Spear-Phishing** | Highly targeted phishing aimed at a specific person/org | Lazarus's primary initial-access vector (fake recruiter messages) |
| **Cryptocurrency Laundering** | Obscuring the origin of stolen crypto funds via mixers/chains | Lazarus is responsible for the largest known crypto heists |
| **Wiper Malware** | Malware designed to destroy data rather than steal it | Used in the 2014 Sony Pictures attack |
| **Living off the Land (LotL)** | Using legitimate system tools to avoid detection | Common Lazarus post-exploitation technique |

## Threat Classification

| Threat Category | Example Lazarus Operation | Year | Source |
|---|---|---|---|
| Financially motivated (cryptocurrency theft) | Ronin Bridge / Axie Infinity hack (~$620M) | 2022 | Chainalysis, FBI advisory |
| Financially motivated (exchange hacks) | Bybit exchange theft | 2025 | Elliptic, industry reports |
| Cyber espionage | Operation Dream Job (fake job offers to defense/aerospace employees) | 2020–2023 | ESET, ClearSky |
| Supply chain attack | 3CX software compromise | 2023 | Mandiant, CrowdStrike |
| Supply chain attack | AppleJeus (trojanized crypto trading apps) | 2018–ongoing | Kaspersky |
| Destructive attack | Sony Pictures Entertainment hack | 2014 | FBI, US-CERT |

## Sources
- MITRE ATT&CK — Group G0032: Lazarus Group
- ENISA Threat Landscape Report (state-sponsored actors section)
- Mandiant, CrowdStrike, Kaspersky public threat reports on Lazarus Group****

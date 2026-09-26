# Week 2 — Data Collection Process: WannaCry Ransomware

## Objective
Collect open-source intelligence (OSINT) related to the WannaCry ransomware
campaign using VirusTotal and Shodan, and map the data sources used.

## VirusTotal — Malware Sample Analysis

**Search performed:** the term `WannaCry` returns hundreds of tagged samples
directly by name (unlike APT-group searches, which require pivoting through
specific hashes).

**Sample analyzed (SHA256):**
ed01ebfbc9eb5bbea545af4d01bf5f1071661840480439c6e5babe8e080e41aa
**Findings:**

| Field | Value |
|---|---|
| Detection ratio | 66 / 71 security vendors flagged the file as malicious |
| File name | diskpart.exe |
| File size | 3.35 MB |
| Relevant tags | `exploit`, `malware`, `cve-2017-0147`, `executes-dropped-file`, `via-tor` |
| Contacted domains | 39 domains observed, including infrastructure-related entries |

The tag `cve-2017-0147` confirms the sample's link to the same family of SMB
vulnerabilities exploited by EternalBlue (CVE-2017-0144), which WannaCry used
as its primary infection and propagation vector. The `via-tor` tag also
indicates use of Tor for command-and-control communication.

## Shodan — Exposed Infrastructure

**Search query used:**
port:445
**Result:** 811,611 internet-facing hosts currently expose port 445 (SMB)
worldwide. Top countries: United States (161,268), Pakistan (76,755),
Germany (56,598), Singapore (46,950), United Kingdom (40,957).

**Notable finding:** one returned host (IP redacted in this report for
ethical reasons) displayed the following banner:
SMB Status:
Authentication: disabled
SMB Version: 1
OS: Unix
Software: Samba 3.0.37
This is significant because **SMBv1 with authentication disabled** is
precisely the type of misconfiguration that made systems vulnerable to the
EternalBlue exploit used by WannaCry in 2017. The fact that hundreds of
thousands of SMB-exposed hosts are still discoverable in 2026 illustrates why
such worms can achieve rapid, widespread propagation once a vulnerable
service is found.

**Ethical note:** no connection attempts were made to any identified host;
observation was limited to banner information already indexed by Shodan.

## Data Source Mapping

| Source | Data Type | Purpose in Analysis |
|---|---|---|
| VirusTotal | File hash, detection ratio, tags, contacted domains | Sample identification and confirmation of exploit linkage (CVE-2017-0147) |
| Shodan | Exposed SMB services (port 445) | Understanding the attack surface / propagation vector at scale |
| MITRE ATT&CK | Techniques, associated software/group | Contextualizing findings within known TTPs (used in Week 1 and 3) |

## Sources
- VirusTotal file report for the analyzed SHA256 hash
- Shodan search results for `port:445` (accessed September 2026)
- MITRE ATT&CK — Software S0366 (WannaCry)

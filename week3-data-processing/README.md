# Week 3 — Data Processing and Exploitation: WannaCry Ransomware

## Objective
Deploy MISP, import Indicators of Compromise (IOCs) related to WannaCry, and
apply filtering/normalization techniques to the collected data.

## MISP Deployment

For this exercise, the MISP demo instance was used
(https://www.misp-project.org/demo/) rather than a full local deployment,
to focus on the data processing workflow rather than infrastructure setup.

**Steps performed:**
1. Logged into the MISP demo instance
2. Created a new event: **"WannaCry Ransomware — IOC Analysis"**
3. Set event distribution and threat level fields (Threat Level: High,
   Analysis: Completed)

![MISP new event creation](images/misp-event-creation.png)

## IOC Import

The following indicators, collected during Week 2 OSINT research, were added
as attributes to the MISP event:

| Attribute Type | Value | Category |
|---|---|---|
| sha256 | `ed01ebfbc9eb5bbea545af4d01bf5f1071661840480439c6e5babe8e080e41aa` | Payload delivery |
| domain | `iuqerfsodp9ifjaposdfjhgosurijfaewrwergwea.com` (kill-switch domain) | Network activity |
| vulnerability | CVE-2017-0144 (EternalBlue) | External analysis |
| vulnerability | CVE-2017-0147 (related SMB vulnerability, confirmed via VirusTotal tag) | External analysis |

![MISP attributes added to event](images/misp-attributes.png)

Additionally, the **MISP Galaxy** feature was used to link the event to the
existing "Ransomware" and "WannaCry" galaxy clusters, which provide
pre-built context (aliases, related threat actors, references) without
manually re-entering publicly known metadata.

![MISP galaxy cluster linked to event](images/misp-galaxy.png)

## Filtering and Normalization

To keep the dataset clean and analysis-ready, the following steps were
applied:

1. **Type filtering** — only attributes of type `sha256`, `domain`, and
   `vulnerability` were kept; irrelevant or duplicate indicator types
   (e.g., MD5 of the same file, redundant IP entries) were excluded to avoid
   noise.
2. **Deduplication** — checked that the same hash was not already present in
   the event as both `sha256` and `md5` for the same file (kept `sha256`
   only, as it is the more collision-resistant identifier).
3. **Normalization** — domain values were lowercased and trimmed of
   whitespace before entry, matching MISP's expected attribute format.
4. **Tagging** — attributes were tagged with `tlp:white` (safe for public
   sharing) since all data originates from open-source, publicly available
   reports.

## Summary

This process demonstrates a simplified CTI data pipeline: raw OSINT findings
from Week 2 (VirusTotal hash, Shodan exposure data) were structured into a
formal MISP event, enriched with existing galaxy context, and normalized
into a consistent, shareable format — the kind of workflow used by real
threat intelligence teams to convert unstructured findings into actionable
indicators.

## Sources
- MISP Project — demo instance and documentation (misp-project.org)
- MISP Galaxy — Ransomware cluster (github.com/MISP/misp-galaxy)
- VirusTotal and Shodan findings from Week 2 of this project****

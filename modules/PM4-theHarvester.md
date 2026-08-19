# W2-PM4 — OSINT Reconnaissance with theHarvester

## Overview

This module covered passive footprinting of the internship-scoped `networkwalks.com` domain using **theHarvester** on Kali Linux.

Two queries were performed:

- A Baidu-only query
- A multi-source query using `-b all`

## Activities

The Baidu-only query completed successfully but returned no IP addresses, email addresses, people or hosts.

The multi-source query continued across available sources despite several API-dependent sources being unavailable and returned:

- 3 ASNs
- 2 interesting URLs
- 4 IP addresses
- 32 hosts

No email addresses, people or LinkedIn users were returned.

Linux piping and `tee` were also used to preserve terminal output while keeping the results visible during execution.

## Evidence Handling

Public evidence was sanitised before publication.

Discovered IP addresses and hostnames were redacted, while summary counts and general tool output were retained.

## Skills Used

- Passive OSINT reconnaissance
- theHarvester
- Multi-source enumeration
- Linux command-line usage
- Pipes and `tee`
- Evidence collection
- Evidence sanitisation

## Dedicated Repository

Full technical documentation, commands, screenshots and sanitised evidence are available in the dedicated repository:

[W2-PM4 — OSINT Reconnaissance with theHarvester](https://github.com/Ritchalison/networkwalks-B082-week2-PM4-theHarvester)

## Author

**Prince Manu Gyebi**  
Cybersecurity Intern — Batch B082  
NETWORKWALKS

LinkedIn: [Prince Manu Gyebi](https://www.linkedin.com/in/princemanugyebi)

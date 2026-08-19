# NETWORKWALKS Cybersecurity Internship — Week 2

**Footprinting, OSINT Reconnaissance, Network Discovery & Technical Reporting**  
**Batch B082**

Week 2 focused on reconnaissance and discovery: gathering publicly available information, examining relationships between OSINT entities, identifying live systems on a local network, and documenting observations without overstating what the evidence proves.

## Week 2 Structure

Electives:

- W2-PM1 — Footprinting with Multiple Kali Tools
- W2-PM2 — GHDB-based Footprinting
- W2-PM3 — Maltego-based Footprinting
- W2-PM4 — Footprinting with theHarvester

Essentials:

- W2-PM5 — Network Scanning with Zenmap
- W2-PM-FINAL — Week 2 Technical Report

---

Week 2 required the completion of at least one elective module together with both essential projects. I selected **W2-PM4 — theHarvester** as my elective and completed **W2-PM5 — Zenmap/Nmap** and **W2-PM-FINAL — Technical Report** as the essential components.

After completing the requirements, I continued with additional electives to extend my exposure to different footprinting and reconnaissance techniques.

## Week 2 Progress

| Module | Focus | Status | Classification |
|---|---|---|---|
| W2-PM4 | theHarvester Footprinting | ✅ Completed | Selected elective |
| W2-PM5 | Zenmap/Nmap Network Discovery | ✅ Completed | Essential |
| W2-PM-FINAL | Technical Reporting | ✅ Completed | Essential |
| W2-PM3 | Maltego Footprinting | ✅ Completed | Additional elective |
| W2-PM1 | Multiple Kali Footprinting Tools | ⏳ Not yet completed | Additional elective |
| W2-PM2 | GHDB-based Footprinting | ⏳ Not yet completed | Additional elective |

## Reconnaissance Perspective

The completed modules approach reconnaissance from different angles:

| Component | Perspective | Primary Question |
|---|---|---|
| theHarvester | Enumeration | What information can external OSINT sources return about a target? |
| Maltego | Link analysis | How are known and discovered entities related, and where can the investigation pivot? |
| Zenmap/Nmap | Network discovery | What systems are present and responsive on a network? |
| Technical report | Analysis | What do the observations mean, and how should they be communicated? |

Together, they form a broader workflow:

```text
Collect
   ↓
Relate
   ↓
Discover
   ↓
Interpret
   ↓
Document
```

## Selected & Essential Modules

### W2-PM4 — theHarvester Footprinting

**Technique:** Passive OSINT enumeration  
**Platform:** Kali Linux 2026.2  
**Target:** `networkwalks.com` — internship-scoped target  
**Repository:** [networkwalks-B082-week2-PM4-theHarvester](https://github.com/Ritchalison/networkwalks-B082-week2-PM4-theHarvester)

W2-PM4 used **theHarvester** to compare single-source and multi-source reconnaissance against the assigned domain.

#### Baidu Query

```bash
theHarvester -d networkwalks.com -l 1000 -b baidu
```

The command completed successfully but returned no IP addresses, email addresses, people or hosts.

This demonstrated an important distinction:

```text
No Results ≠ Failed Command
```

A reconnaissance query may execute correctly while the selected source has little or no relevant indexed data.

#### Multi-Source Query

```bash
theHarvester -d networkwalks.com -l 50 -b all
```

Some sources required API credentials that were not configured locally, while accessible sources continued running.

The completed query returned:

| Result Type | Count |
|---|---:|
| ASNs | 3 |
| Interesting URLs | 2 |
| IP addresses | 4 |
| Hosts | 32 |
| Email addresses | 0 |
| People | 0 |
| LinkedIn users | 0 |

The contrast between the two runs showed how strongly OSINT results depend on the sources available to a tool.

#### Evidence Collection

Terminal output was preserved using Linux piping and `tee`, allowing results to remain visible while also being written to evidence files.

```text
Command Output
      |
      v
     tee
    /   \
   v     v
Terminal File
```

Public evidence was sanitised before publication. Discovered IP addresses and hostnames were redacted while methodology, result counts and general tool behaviour were retained.

theHarvester was most useful here as an **enumeration tool**, showing how different external sources expose different levels of information about the same target.

---

### W2-PM5 — Zenmap / Nmap Network Discovery

**Technique:** Active local host discovery  
**Platform:** Windows 11  
**Tools:** Zenmap / Nmap 7.991  
**Scope:** My own local network  
**Repository:** [networkwalks-B082-week2-PM5-Zenmap](https://github.com/Ritchalison/networkwalks-B082-week2-PM5-Zenmap)

W2-PM5 shifted from public OSINT to discovery on my own LAN.

#### Network Identification

The active network configuration was:

```text
IPv4 address:     192.168.2.27
Subnet mask:      255.255.255.0
Default gateway:  192.168.2.1
LAN subnet:       192.168.2.0/24
```

The `/24` subnet was used as the Zenmap target.

#### Host Discovery

Using the **Ping scan** profile generated:

```bash
nmap -sn 192.168.2.0/24
```

The scan checked 256 addresses and identified two live hosts:

```text
192.168.2.1   → local gateway
192.168.2.27  → Windows host
```

The gateway MAC address was returned through the scan, while the Windows host MAC address was verified locally with:

```text
ipconfig /all
```

MAC addresses were redacted from the public evidence.

#### Network Topology

Zenmap's topology view displayed the Windows host and local gateway around its `localhost` reference node.

The `localhost` node is part of Zenmap's visual representation and does not represent a third discovered live host.

#### Troubleshooting

The initial topology PDF export failed when the destination pointed to:

```text
C:\Program Files (x86)\Nmap
```

with:

```text
error while writing to output stream
```

Changing the destination to the Desktop resolved the issue.

The behaviour was consistent with Windows write restrictions on protected installation directories.

Zenmap/Nmap demonstrated a different form of reconnaissance: rather than asking what public sources expose, it identifies which systems actually respond within a defined network range.

---

### W2-PM-FINAL — Technical Report

The submitted Week 2 report covers **W2-PM4 — theHarvester** and **W2-PM5 — Zenmap/Nmap**.

It documents:

- methodology and tools
- reconnaissance findings
- network-discovery findings
- risk observations
- recommendations
- troubleshooting
- evidence handling
- scope and limitations

A central reporting principle was avoiding unsupported security claims.

```text
Discovered Information
        ≠
Security-Relevant Exposure
        ≠
Validated Vulnerability
```

No exploitation or vulnerability validation was performed.

#### Report

- [View Report PDF](report/Prince_Manu_Gyebi_NETWORKWALKS_Week2_Final_Report.pdf)
- [View Report DOCX](report/Prince_Manu_Gyebi_NETWORKWALKS_Week2_Final_Report.docx)

## Additional Electives Completed

### W2-PM3 — Maltego Footprinting

**Technique:** Relationship-based OSINT / link analysis  
**Platform:** Kali Linux 2026.2  
**Tool:** Maltego Graph (Desktop) 4.12.1 Community Edition  
**Target:** `networkwalks.com` — internship-scoped target  
**Repository:** [networkwalks-B082-week2-PM3-Maltego](https://github.com/Ritchalison/networkwalks-B082-week2-PM3-Maltego)

Maltego introduced a relationship-based approach to reconnaissance.

Unlike theHarvester, which primarily enumerates information returned by external sources, Maltego organises information as **entities and relationships** within a graph.

#### Domain-to-Email Transform

The investigation began with a Domain entity:

```text
networkwalks.com
```

An email-related transform returned:

```text
info@networkwalks.com
```

Maltego preserved the relationship visually:

```text
networkwalks.com
       |
       v
info@networkwalks.com
```

The useful distinction was not merely the returned email entity, but the way Maltego retained the relationship between the two pieces of information.

#### Investigative Pivoting

A transform takes an existing entity, performs a lookup and returns related entities.

```text
Known Entity
     |
     v
 Transform
     |
     v
Related Entity
     |
     v
Next Pivot
```

After completing the required Domain-to-Email task, I explored additional entities and transforms to observe how the graph could expand through successive pivots.

The broader graph was exploratory; not every displayed entity was returned directly from the initial domain transform.

Maltego demonstrated how reconnaissance can move beyond collecting isolated results and instead develop into a relationship-based investigation.

## Comparing the Approaches

theHarvester and Maltego both support passive reconnaissance, but with different emphasis: theHarvester is primarily enumeration-oriented, while Maltego is relationship- and pivot-oriented. Zenmap/Nmap shifts to active network discovery, identifying responsive systems within an authorised network range.

## Operational Lessons

| Module | Observation | Lesson |
|---|---|---|
| theHarvester | Some sources required unavailable API credentials | Multi-source tools can continue with partial source availability |
| theHarvester | Baidu returned no findings | Zero results do not necessarily indicate failed execution |
| Zenmap | PDF export failed in the Nmap installation directory | Environment and file permissions can affect otherwise functional tools |
| Maltego | Installation and setup on Kali were smooth | Setup completed without requiring additional troubleshooting |

## Evidence & Disclosure

Public cybersecurity documentation requires enough evidence to demonstrate the work without unnecessarily exposing identifiers.

Where appropriate, public evidence removed:

- discovered IP addresses from theHarvester
- discovered hostnames from theHarvester
- MAC addresses from the local network exercise
- unnecessary personal identifiers in exploratory material

Documentation retained:

- commands
- methodology
- result counts
- assigned target domain
- tool behaviour
- general screenshots
- troubleshooting evidence
- analytical observations

The aim was to preserve technical value while applying reasonable disclosure judgement.

## What I Learned

### Tool output still requires interpretation

Running a command or transform produces data. Turning that data into a defensible security conclusion requires context.

```text
Tool Output
    ↓
Observation
    ↓
Interpretation
    ↓
Security Judgement
```

Skipping those intermediate steps risks overstating what the evidence proves.

### Evidence collection is part of the workflow

Saving outputs and screenshots while the work was being performed produced a more reliable record than reconstructing evidence afterwards.

The use of `tee` during theHarvester exercise was a simple example of building evidence collection into the technical process.

## Reporting

A separate **Extended Week 2 Report** will consolidate the additional electives and comparative lessons once the extended Week 2 work is complete.

## Repository Structure

```text
.
├── report/
│   ├── Prince_Manu_Gyebi_NETWORKWALKS_Week2_Final_Report.pdf
│   └── Prince_Manu_Gyebi_NETWORKWALKS_Week2_Final_Report.docx
│
└── README.md
```

## Resources & Instructor Guidance

The Week 2 activities were completed using the project guidance, walkthroughs and practice material provided through the **NETWORKWALKS Cybersecurity Internship Programme**.

**Instructor:** **Waqas Karim (CCIE)**

Maltego walkthrough:

- [Maltego Installation + Setup || Practice Lab 1](https://youtu.be/v0eqeYJ5PKc)

## Ethical Use & Scope

All activities documented here were completed for educational purposes as part of the **NETWORKWALKS Cybersecurity Internship Programme, Batch B082**.

Testing was limited to:

- `networkwalks.com` where assigned as the internship-scoped reconnaissance target
- my own local network for Zenmap/Nmap discovery

No exploitation, credential attacks, unauthorised access or destructive testing was performed.

Reconnaissance observations are documented as findings, not automatically as vulnerabilities.

## Week 2 Takeaway

Week 2 moved beyond learning individual tools.

theHarvester demonstrated **enumeration across OSINT sources**.  
Maltego introduced **relationship-based investigation and pivoting**.  
Zenmap/Nmap demonstrated **active host discovery and network visibility**.  
The reporting exercise required those observations to be **qualified, interpreted and communicated responsibly**.

Together, they reinforced a practical progression:

```text
Discover
   ↓
Relate
   ↓
Interpret
   ↓
Document
```

## Author

**Prince Manu Gyebi**  
Cybersecurity Intern — Batch B082  
NETWORKWALKS

LinkedIn: [Prince Manu Gyebi](https://www.linkedin.com/in/princemanugyebi)

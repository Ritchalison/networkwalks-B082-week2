# W2-PM5 — Network Scanning with Zenmap

## Overview

This module covered local network discovery and topology mapping using **Zenmap/Nmap** on my own LAN.

The task involved identifying the active network configuration, determining the LAN subnet, discovering live hosts, verifying IP and MAC address information, and visualising the resulting topology.

## Activities

The active Wi-Fi configuration was identified as:

- Local IPv4 address: `192.168.2.27`
- Subnet mask: `255.255.255.0`
- Default gateway: `192.168.2.1`
- LAN subnet: `192.168.2.0/24`

A Zenmap Ping Scan was performed using:

```bash
nmap -sn 192.168.2.0/24
```

The scan checked **256 IP addresses** and identified **2 live hosts**:

- `192.168.2.1` — local gateway
- `192.168.2.27` — Windows host

The gateway MAC address was returned by Zenmap, while the Windows host MAC address was verified using `ipconfig /all`.

Zenmap's Topology view displayed the Windows host and local gateway around the `localhost` reference node. The `localhost` node is part of Zenmap's topology representation and does not represent a third discovered live host.

The topology was exported to PDF after changing the save location from the protected Nmap installation directory to the Desktop.

## Evidence Handling

MAC addresses were redacted from the public screenshots before publication.

The exported topology PDF and supporting screenshots are maintained in the dedicated PM5 repository.

## Skills Used

- Zenmap and Nmap
- IPv4 addressing and subnetting
- Host discovery
- IP and MAC address verification
- Network topology mapping

## Dedicated Repository

Full technical documentation, commands, screenshots and topology evidence are available in the dedicated repository:

[W2-PM5 — Network Scanning with Zenmap](https://github.com/Ritchalison/networkwalks-B082-week2-PM5-Zenmap)

## Author

**Prince Manu Gyebi**  
Cybersecurity Intern — Batch B082  
NETWORKWALKS

LinkedIn: [Prince Manu Gyebi](https://www.linkedin.com/in/princemanugyebi)

---
title: "CCNA ITN Project"
order: 1
category: Networking
---

<h1 align="center">  Enterprise LAN Deployment with VLAN Segmentation and Router-on-a-Stick </h1>

---

### Project Overview

This project simulates a small enterprise network consisting of multiple departments connected through a centralized routing infrastructure. The network was designed to provide secure communication between departments while maintaining logical separation using VLAN technology.
The implementation demonstrates core networking concepts commonly used in enterprise environments, including network segmentation, dynamic IP address allocation, remote device management, and switch security.

---

### Network Topology

![Network Topology](/assets/images/projects/ITN-Topology.png)

---

### Project Highlights
- Created departmental VLANs
- Configured trunk links
- Implemented Router-on-a-Stick
- Verified end-to-end connectivity

---

### Skills Demonstrated
- Basic Router Configuration
- Switch Configuration
- DHCP Configuration
- Inter-VLAN Routing
- Network Troubleshooting

---

### VLAN Design

| VLAN  | Department  |
|----------|-------------|
| VLAN 10 | IT |
| VLAN 20 | Finance |
| VLAN 30 | HR |
| VLAN 40 | Guest |
| VLAN 99 | Management |

The use of VLANs reduces unnecessary broadcast traffic and improves network organization.

---

### Inter-VLAN Routing

The router was configured using the Router-on-a-Stick architecture.
Subinterfaces were created for each VLAN and connected through a trunk link.

### Example

interface g0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

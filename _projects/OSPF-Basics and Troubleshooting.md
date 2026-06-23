---
title: "OSPF"
order: 3
category: Networking
---

Project description goes here...

<h2 align="center"> OSPF BASICS AND TROUBLESHOOTING </h2>


## Network Topology
<img src="assets/images/projects/OSPF1.png"> </img>
assets/images/projects/OSPF1.png

### IP Addressing Plan

| Device     | Interface | IP              |
| ---------- | --------- | --------------- |
| R2(Area10) | G0/0      | 192.168.10.1/24 |
| R3(Area20) | G0/0      | 192.168.20.1/24   |

#### Backbone Area 0

R1 ↔ R2
| Interface | IP           |
| --------- | ------------ |
| R1 G0/0   | 10.0.12.1/30 |
| R2 G0/1   | 10.0.12.2/30 |

R1 ↔ R3
| Interface | IP           |
| --------- | ------------ |
| R1 G0/1   | 10.0.13.1/30 |
| R3 G0/1   | 10.0.13.2/30 |

### Configure Single-Area OSPF
#### Area O
<i> R1:</i>
router ospf 1
network 10.0.12.0 0.0.0.3 area 0
network 10.0.13.0 0.0.0.3 area 0
<i> R2:</i>
router ospf 1
network 10.0.12.0 0.0.0.3 area 0
<i> R3:</i>
router ospf 1
network 10.0.13.0 0.0.0.3 area 0

### Convert to Multi-Area OSPF
#### Area 1O
<i> R2:</i>
router ospf 1
network 192.168.10.0 0.0.0.255 area 10
#### Area 20
<i> R3 :</i>
router ospf 1
network 192.168.20.0 0.0.0.255 area 20

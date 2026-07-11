---
title: "OSPF Basics and Troubleshooting"
layout: single
classes: wide
toc: true
toc_label: "Project Contents"
---

<h1 align="center"> OSPF Basics and Troubleshooting </h1>

> Implementation of Single-Area and Multi-Area OSPF routing in Cisco Packet Tracer, including verification and troubleshooting procedures.

---

## 📡 Network Topology

<div align="center">
  <img src="{{ '/assets/images/projects/OSPF1.png' | relative_url }}" alt="OSPF Topology" width="900">
</div>

---

## 🎯 Project Objectives

- Configure Single-Area OSPF
- Convert the network to Multi-Area OSPF
- Verify OSPF neighbor relationships
- Analyze routing tables
- Troubleshoot adjacency issues

---

## 🗺️ IP Addressing Plan

### Area 10 LAN

| Device | Interface | IP Address |
|----------|----------|----------|
| R2 | G0/0 | 192.168.10.1/24 |

### Area 20 LAN

| Device | Interface | IP Address |
|----------|----------|----------|
| R3 | G0/0 | 192.168.20.1/24 |

### Backbone Area 0

| Link | Interface | IP Address |
|--------|----------|----------|
| R1 ↔ R2 | R1 G0/0 | 10.0.12.1/30 |
|         | R2 G0/1 | 10.0.12.2/30 |
| R1 ↔ R3 | R1 G0/1 | 10.0.13.1/30 |
|         | R3 G0/1 | 10.0.13.2/30 |

---

## ⚙️ Step 1: Configure Single-Area OSPF

### R1 Configuration

```cisco
router ospf 1
 network 10.0.12.0 0.0.0.3 area 0
 network 10.0.13.0 0.0.0.3 area 0
```
### R2 Configuration

```cisco
router ospf 1
 network 10.0.12.0 0.0.0.3 area 0
```
### R3 Configuration

```cisco
router ospf 1
 network 10.0.13.0 0.0.0.3 area 0
```
### Verification Command
<div align="center">
  <img src="{{ '/assets/images/projects/OSPF2.png' | relative_url }}" alt="OSPF verify" width="900">
</div>

## ⚙️ Step 2: Convert to Multi-Area OSPF

### AREA 10 (R2)
```cisco
router ospf 1
 network 192.168.10.0 0.0.0.255 area 10
```
### AREA 20 (R3)
```cisco
router ospf 1
 network 192.168.10.0 0.0.0.255 area 10
```

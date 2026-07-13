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
### Verification Command for R2 and R1
Run _show ip ospf neighbor_ on the routers and if successful, you will observe some output as observed in the image
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
### Verification Command for R2 and R3
To verify, just run _show ip route ospf_
<div align="center">
  <img src="{{ '/assets/images/projects/OSPF3.png' | relative_url }}" alt="OSPF verify" width="900">
</div>

## ⚙️ Step 3: Configure Passive Interfaces
You guys are unmatched geniuses, you know what passive interfaces in OSPF do. For those who might have read this some decades back it basically does this:
- Enhances resource optimization by reducing hello packets in the network
- Security- Prevents rogue routers from forming OSPF adjacencies and injecting malicious routes into your network.
To prevent unnecessary OSPF hellos towards PCs, we can configure passive interfaces for the routers R2 and R3 as observed in the images
<div align="center">
  <img src="{{ '/assets/images/projects/OSPF4.png' | relative_url }}" alt="OSPF verify" width="900">
</div>

### Verification Command for R2 and R3
Run _show ip protocols_ to verify any passive interfaces configured, and of course we can see one🙂
<div align="center">
  <img src="{{ '/assets/images/projects/OSPF5.png' | relative_url }}" alt="OSPF verify" width="900">
</div>

## ⚙️ Step3: Configure Default Route Propagation
Configure a static default route on R1 by running the following series of commands in that order:
```cisco
ip route 0.0.0.0 0.0.0.0 203.0.113.1
router ospf 1
 default-information originate
```
To verify run _show ip route_ on either R2 or R3 and you should see "O*E2 0.0.0.0/0"
<div align="center">
  <img src="{{ '/assets/images/projects/OSPF6.png' | relative_url }}" alt="OSPF verify" width="900">
</div>


## ⚙️ SUMMARY

### Single-Area OSPF vs Multi-Area OSPF
| Feature | Single-area OSPF | Multi-area OSPF |
|------------------------|------------------------|------------------------|
| **Design complexity** | Low | High |
| **LSDB size** | Large | Small (per area) |
| **SPF calculations** | Global | Localized |
| **Route summarization** | Not supported | Supported at ABRs |
| **Ideal network size** | Small (<100 routers) | Large (100s to 1000s) |

### OSPF Verification Commands
OSPF Verification Commands
- show ip ospf neighbor
- show ip ospf interface
- show ip route
- show ip ospf database
- show ip protocols
- show running-config

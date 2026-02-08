# Static-and-Dynamic-Routing-Lab
# Multi-Router Static and Dynamic Routing Lab (RIPv2)

## Overview
This project simulates a routed enterprise network using three routers.
The objective was to establish connectivity between multiple LANs using both:

1. Static Routing
2. Dynamic Routing with RIPv2

The lab demonstrates routing table propagation, hop-by-hop learning, and
troubleshooting missing route advertisements.

---

## Objectives
- Build a multi-router topology with three separate LANs
- Configure IPv4 addressing across LAN and WAN links
- Implement static routes for end-to-end communication
- Replace static routing with RIPv2 dynamic routing
- Verify routing behavior using Cisco IOS commands

---

## IP Addressing Plan

### LAN Subnets
| LAN | Network | Gateway |
|-----|---------|---------|
| A   | 192.168.1.0/24 | 192.168.1.1 |
| B   | 192.168.2.0/24 | 192.168.2.1 |
| C   | 192.168.3.0/24 | 192.168.3.1 |

### WAN Links (/30)
| Link | Subnet |
|------|--------|
| R1–R2 | 10.0.12.0/30 |
| R2–R3 | 10.0.23.0/30 |

---

## Routing Implementation

### Phase 1: Static Routing
Static routes were configured manually on each router to reach remote LANs.

### Phase 2: Dynamic Routing (RIPv2)
Static routes were removed and replaced with RIPv2:

```bash
router rip
version 2
no auto-summary
network 192.168.X.0
network 10.0.X.0

```

## Verification Commands Used
```bash
show ip route
show ip protocols
show ip interface brief
ping <destination>
tracert <destination>
```
### Expected routing table entries:
- C = Connected routes
- R = RIP-learned routes

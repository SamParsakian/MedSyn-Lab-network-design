# VLAN Design — Sam Medsyn Lab Company

## VLAN Table

| VLAN ID | Name | Purpose | Subnet (HQ) | Subnet (Branch) |
|---------|------|---------|-------------|-----------------|
| 10 | Admin | Admin / management workstations | 172.16.10.0/24 | 172.17.10.0/24 |
| 20 | LAN | Wired department end devices | 172.16.20.0/22 | 172.17.20.0/22 |
| 50 | WLAN | Wireless clients and APs | 172.16.48.0/22 | — |
| 99 | BLACKHOLE | Native VLAN (unused, security) | — | — |
| 100 | DMZ | DMZ servers (HQ only) | 10.10.10.0/26 | — |

---

## MgmtAdmin Department — Dual VLAN Design

The MgmtAdmin department uses two VLANs in one physical area:

| Device | Role | VLAN | Subnet |
|--------|------|------|--------|
| SMLC-HQ-Mgmt-PC1 | Normal department user | VLAN 20 | 172.16.20.0/22 |
| SMLC-HQ-Mgmt-PC2 | Normal department user | VLAN 20 | 172.16.20.0/22 |
| SMLC-HQ-Mgmt-PRN1 | Department printer | VLAN 20 | 172.16.20.0/22 |
| SMLC-HQ-Admin-PC1 | Admin workstation | VLAN 10 | 172.16.10.0/24 |
| SMLC-HQ-Admin-PC2 | Admin workstation | VLAN 10 | 172.16.10.0/24 |
| SMLC-HQ-MgmtAdmin-AP1 | Lightweight AP | VLAN 50 | 172.16.48.0/22 |
| SMLC-HQ-MgmtAdmin-LAP1 | Wireless laptop | VLAN 50 | 172.16.48.0/22 |
| SMLC-HQ-MgmtAdmin-TAB1 | Wireless tablet | VLAN 50 | 172.16.48.0/22 |
| SMLC-HQ-MgmtAdmin-MOB1 | Wireless smartphone | VLAN 50 | 172.16.48.0/22 |

**Why two VLANs in one department:** VLAN 20 carries normal user traffic. VLAN 10 carries trusted admin traffic used for managing switches, firewalls, WLC, and servers. Separating them prevents normal users from reaching management interfaces.

---

## SMLC-HQ-MgmtAdmin-SW1 Port Assignment

```
Fa0/3  → SMLC-HQ-Mgmt-PC1      → VLAN20
Fa0/4  → SMLC-HQ-Mgmt-PC2      → VLAN20
Fa0/5  → SMLC-HQ-Mgmt-PRN1     → VLAN20
Fa0/6  → SMLC-HQ-Admin-PC1     → VLAN10
Fa0/7  → SMLC-HQ-Admin-PC2     → VLAN10
Fa0/22 → SMLC-HQ-MgmtAdmin-AP1 → VLAN50
Uplinks (Fa0/1, Fa0/2) → trunk, allowed VLANs 10,20,50
```

---

## HSRP Gateways

| VLAN | HQ Active | HQ Standby | HQ VIP | Branch Active | Branch VIP |
|------|-----------|------------|--------|---------------|------------|
| 10 | CoreSW1 | CoreSW2 | 172.16.10.1 | BR-CoreSW1 | 172.17.10.1 |
| 20 | CoreSW1 | CoreSW2 | 172.16.20.1 | BR-CoreSW1 | 172.17.20.1 |
| 50 | CoreSW1 | CoreSW2 | 172.16.50.1 | — | — |

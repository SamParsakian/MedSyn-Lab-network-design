# SMLC-HQ-TechOps-SW1 — CONFIRMED ✓
Date confirmed: 2026-06-04

## show interfaces trunk

```
Fa0/1  on  802.1q  trunking  native 99  allowed: 10,20,50  → SMLC-HQ-CoreSW1
Fa0/2  on  802.1q  trunking  native 99  allowed: 10,20,50  → SMLC-HQ-CoreSW2
STP forwarding: Fa0/1=10,20 / Fa0/2=10,20 (both active)
```

## Key Config

- L2 switch (no ip routing)
- VLANs: 10 (Management), 20 (LAN), 50 (WLAN), 99 (BLACKHOLE)
- Fa0/1: trunk → SMLC-HQ-CoreSW1, Fa0/2: trunk → SMLC-HQ-CoreSW2 (native 99, allowed 10/20/50)
- Fa0/3-22, Fa0/24: access VLAN 20 (TechOps department end devices)
- Fa0/23: access VLAN50 → SMLC-HQ-TechOps-LAP wired uplink
- Vlan10 SVI: 172.16.10.13/24, default-gw 172.16.10.1

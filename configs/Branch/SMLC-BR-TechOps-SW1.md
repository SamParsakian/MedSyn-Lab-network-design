# SMLC-BR-TechOps-SW1 — CONFIRMED ✓
Date confirmed: 2026-06-04

## show interfaces trunk

```
Fa0/1  on  802.1q  trunking  native 99  allowed: 10,20,50  → SMLC-BR-CoreSW1
Fa0/2  on  802.1q  trunking  native 99  allowed: 10,20,50  → SMLC-BR-CoreSW2
STP forwarding: Fa0/1=10,20 / Fa0/2=none (Fa0/2 STP alternate/blocking — normal)
```

## Key Config

- L2 switch (no ip routing)
- VLANs: 10 (Branch-Management), 20 (Branch-LAN), 50 (Branch-WLAN), 99 (BLACKHOLE)
- Fa0/1: trunk → SMLC-BR-CoreSW1, Fa0/2: trunk → SMLC-BR-CoreSW2 (native 99, allowed 10/20/50)
- Fa0/3-24: access VLAN 20
- Vlan10 SVI: 172.17.10.20/24, default-gw 172.17.10.1

# SMLC-HQ-ITInfra-SW1 — CONFIRMED ✓
Date confirmed: 2026-06-04

## show interfaces trunk

```
Fa0/2  on  802.1q  trunking  native 99  allowed: 10,20,50  → SMLC-HQ-CoreSW2 (single uplink)
STP forwarding: Fa0/2=10,20 ✓
```

Note: ITInfra-SW1 has one physical uplink in this topology. SMLC-HQ-CoreSW HSRP handles gateway redundancy at L3.

## Key Config

- L2 switch (no ip routing)
- VLANs: 10 (Management), 20 (LAN), 50 (WLAN), 99 (BLACKHOLE)
- Fa0/1-2: trunk config (native 99, allowed 10/20/50); only Fa0/2 physically connected
- Fa0/3-20, Fa0/24: access VLAN 20 (ITInfra department end devices)
- Fa0/21-22: access VLAN 10 (management devices)
- Fa0/23: access VLAN50 → SMLC-HQ-ITInfra-LAP wired uplink
- Vlan10 SVI: 172.16.10.14/24, default-gw 172.16.10.1

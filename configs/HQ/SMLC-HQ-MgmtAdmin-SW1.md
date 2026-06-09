# SMLC-HQ-MgmtAdmin-SW1 — CONFIRMED ✓
Date confirmed: 2026-06-09

## show interfaces trunk

```
Fa0/1  on  802.1q  trunking  native 99  allowed: 10,20,50  → SMLC-HQ-CoreSW1
Fa0/2  on  802.1q  trunking  native 99  allowed: 10,20,50  → SMLC-HQ-CoreSW2
```

## show interfaces status

```
Fa0/1   connected  trunk   → SMLC-HQ-CoreSW1
Fa0/2   connected  trunk   → SMLC-HQ-CoreSW2
Fa0/3   connected  VLAN20  → SMLC-HQ-Mgmt-PC1
Fa0/4   connected  VLAN20  → SMLC-HQ-Mgmt-PC2
Fa0/5   connected  VLAN20  → SMLC-HQ-Mgmt-PRN1
Fa0/6   connected  VLAN10  → SMLC-HQ-Admin-PC1
Fa0/7   connected  VLAN10  → SMLC-HQ-Admin-PC2
Fa0/22  connected  VLAN50  → SMLC-HQ-MgmtAdmin-AP1 (LAP-PT wired uplink)
Fa0/8-21, Fa0/23-24: notconnect
Gi0/1-2: notconnect (not used)
```

## Key Config

- L2 switch (no ip routing)
- VLANs: 10 (Admin), 20 (Mgmt — LAN), 50 (WLAN), 99 (BLACKHOLE)
- Fa0/1: trunk → SMLC-HQ-CoreSW1, Fa0/2: trunk → SMLC-HQ-CoreSW2 (native 99, allowed 10/20/50)
- Fa0/3-5: access VLAN20 (Mgmt-PC1, Mgmt-PC2, Mgmt-PRN1)
- Fa0/6-7: access VLAN10 (Admin-PC1, Admin-PC2)
- Fa0/22: access VLAN50 → SMLC-HQ-MgmtAdmin-AP1 wired uplink + spanning-tree portfast
- Vlan10 SVI: 172.16.10.10/24, default-gw 172.16.10.1

See also: `../../docs/vlan-design.md`

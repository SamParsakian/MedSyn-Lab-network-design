# SMLC-HQ-CoreSW2 — CONFIRMED ✓
Date confirmed: 2026-06-04

## show ip interface brief

```
Port-channel1         unassigned  up/up
GigabitEthernet1/0/1  10.10.0.5   up/up   → SMLC-HQ-FW1 INSIDE2
GigabitEthernet1/0/2  unassigned  up/up   → SMLC-HQ-MgmtAdmin-SW1 trunk
GigabitEthernet1/0/3  unassigned  up/up   → SMLC-HQ-BizOps-SW1 trunk
GigabitEthernet1/0/4  unassigned  up/up   → SMLC-HQ-Finance-SW1 trunk
GigabitEthernet1/0/5  unassigned  up/up   → SMLC-HQ-TechOps-SW1 trunk
GigabitEthernet1/0/7  10.10.0.13  up/up   → SMLC-HQ-FW2 INSIDE2
GigabitEthernet1/0/8  unassigned  down    → SMLC-HQ-ITInfra-SW1
GigabitEthernet1/0/21 unassigned  up/up   → LACP to SMLC-HQ-CoreSW1
GigabitEthernet1/0/22 unassigned  up/up   → LACP to SMLC-HQ-CoreSW1
GigabitEthernet1/0/23 unassigned  up/up   → LACP to SMLC-HQ-CoreSW1
Vlan10               172.16.10.2  up/up
Vlan20               172.16.20.2  up/up
Vlan50               172.16.50.2  up/up
```

## Key Config

- HSRP STANDBY (priority 100) for VLANs 10/20/50
  - HSRP VIPs: 172.16.10.1, 172.16.20.1, 172.16.50.1
- DHCP relay (ip helper-address 10.10.10.10 + 10.10.10.11) on all VLANs
- LACP mode on, Gi1/0/21-23 → Port-channel1
- OSPF 15, RID 2.2.2.2
  - Networks: 10.10.0.4/30, 10.10.0.12/30, 172.16.10.0/24, 172.16.20.0/22, 172.16.50.0/22

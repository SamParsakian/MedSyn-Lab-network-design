# SMLC-BR-CoreSW2 — CONFIRMED ✓
Date confirmed: 2026-06-04

## show ip interface brief

```
Port-channel1         unassigned  up/up   → EtherChannel to SMLC-BR-CoreSW1 (Po1)
GigabitEthernet1/0/1  10.10.1.5   up/up  → SMLC-BR-FW1 INSIDE2
GigabitEthernet1/0/2  unassigned  up/up  → SMLC-BR-TechOps-SW1 trunk
GigabitEthernet1/0/3  unassigned  up/up  → SMLC-BR-FieldOps-SW1 trunk
GigabitEthernet1/0/4  unassigned  up/up  → SMLC-BR-BizOps-SW1 trunk
GigabitEthernet1/0/5  unassigned  up/up  → SMLC-BR-Support-SW1 trunk
GigabitEthernet1/0/21 unassigned  up/up  → LACP to SMLC-BR-CoreSW1
GigabitEthernet1/0/22 unassigned  up/up  → LACP to SMLC-BR-CoreSW1
GigabitEthernet1/0/23 unassigned  up/up  → LACP to SMLC-BR-CoreSW1
Vlan10               172.17.10.2  up/up
Vlan20               172.17.20.2  up/up
Vlan50               172.17.50.2  up/up
```

- Port-channel1: up/up ✓

## Key Config

- HSRP STANDBY (priority 100) for VLANs 10/20/50
  - HSRP VIPs: 172.17.10.1, 172.17.20.1, 172.17.50.1
- DHCP relay (ip helper-address 10.10.10.10 + 10.10.10.11) on all VLANs
- LACP mode on, Gi1/0/21-23 → Port-channel1
- OSPF 15, RID 7.7.7.2
  - Networks: 10.10.1.4/30, 172.17.10.0/24, 172.17.20.0/22, 172.17.50.0/22
  - passive-interface default; active on Gi1/0/1

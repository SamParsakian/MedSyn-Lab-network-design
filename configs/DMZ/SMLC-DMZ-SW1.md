# SMLC-DMZ-SW1 — CONFIRMED ✓
Date confirmed: 2026-06-04

## show ip interface brief

```
FastEthernet0/1-7   unassigned  up/up   → FW1 DMZ link + 6 DMZ servers
FastEthernet0/8-24  unassigned  down    → not connected
Vlan100             10.10.10.2  up/up   → DMZ management SVI
```

## Key Config

- L2-only switch (no ip routing)
- VLAN 100 (DMZ) — all Fa0/1-24 access ports
- SVI Vlan100: 10.10.10.2/26 (management)
- Default gateway: 10.10.10.1 (SMLC-HQ-FW1 Gi1/3)
- spanning-tree portfast default on all access ports

## Neighbour Map

| Interface | Neighbour      | IP             |
|-----------|----------------|----------------|
| Fa0/1     | SMLC-HQ-FW1 Gi1/3 | 10.10.10.1 |
| Fa0/2     | SMLC-DHCP1     | 10.10.10.10/26 |
| Fa0/3     | SMLC-DHCP2     | 10.10.10.11/26 |
| Fa0/4     | SMLC-DNS1      | 10.10.10.12/26 |
| Fa0/5     | SMLC-WEB1      | 10.10.10.13/26 |
| Fa0/6     | SMLC-MAIL1     | 10.10.10.14/26 |
| Fa0/7     | SMLC-FTP1      | 10.10.10.15/26 |

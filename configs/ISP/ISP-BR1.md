# ISP-BR1 — CONFIRMED ✓
Date confirmed: 2026-06-04

## show ip interface brief

```
Interface              IP-Address      Status     Protocol
GigabitEthernet0/0     198.51.100.1    up         up
Serial0/3/0            192.0.2.6       up         up
Loopback0              5.5.5.1         up         up
```

## Interface ↔ Neighbour Map

| PT Interface | IP              | Neighbour                 | Neighbour IP  |
|--------------|-----------------|---------------------------|---------------|
| Serial0/3/0  | 192.0.2.6/30    | INTERNET Serial0/3/1      | 192.0.2.5     |
| Gi0/0        | 198.51.100.1/30 | SMLC-BR-FW1 Gi1/3 OUTSIDE | 198.51.100.2  |
| Loopback0    | 5.5.5.1/32      | OSPF router-id             | —             |

## OSPF

- Process 15, router-id 5.5.5.1
- Networks: 5.5.5.1/32, 192.0.2.4/30, 198.51.100.0/30

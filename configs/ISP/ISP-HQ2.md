# ISP-HQ2 — CONFIRMED ✓
Date confirmed: 2026-06-04

## show ip interface brief

```
Interface              IP-Address      Status     Protocol
GigabitEthernet0/0     203.0.113.9     up         up
GigabitEthernet0/1     203.0.113.13    up         up
Serial0/3/0            192.0.2.10      up         up
Loopback0              3.3.3.2         up         up
```

## Interface ↔ Neighbour Map

| PT Interface | IP              | Neighbour                    | Neighbour IP   |
|--------------|-----------------|------------------------------|----------------|
| Serial0/3/0  | 192.0.2.10/30   | INTERNET Serial0/2/0         | 192.0.2.9      |
| Gi0/0        | 203.0.113.9/30  | SMLC-HQ-FW2 Gi1/4 OUTSIDE2  | 203.0.113.10   |
| Gi0/1        | 203.0.113.13/30 | SMLC-HQ-FW1 Gi1/5 OUTSIDE2  | 203.0.113.14   |
| Loopback0    | 3.3.3.2/32      | OSPF router-id               | —              |

## OSPF

- Process 15, router-id 3.3.3.2
- Networks: 3.3.3.2/32, 192.0.2.8/30, 203.0.113.8/30, 203.0.113.12/30

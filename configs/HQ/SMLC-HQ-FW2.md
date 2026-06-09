# SMLC-HQ-FW2 — CONFIRMED ✓
Date confirmed: 2026-06-04

## Interfaces

| Interface | Nameif   | Security | IP                    |
|-----------|----------|----------|-----------------------|
| Gi1/1     | INSIDE1  | 100      | 10.10.0.10/30         |
| Gi1/2     | INSIDE2  | 100      | 10.10.0.14/30         |
| Gi1/3     | OUTSIDE  | 0        | 203.0.113.6/30        |
| Gi1/4     | OUTSIDE2 | 0        | 203.0.113.10/30       |

## Neighbour Map

| Interface | IP              | Neighbour              | Neighbour IP   |
|-----------|-----------------|------------------------|----------------|
| Gi1/3     | 203.0.113.6/30  | ISP-HQ1 Gi0/1          | 203.0.113.5    |
| Gi1/4     | 203.0.113.10/30 | ISP-HQ2 Gi0/0          | 203.0.113.9    |
| Gi1/1     | 10.10.0.10/30   | SMLC-HQ-CoreSW1 Gi1/0/7 | 10.10.0.9    |
| Gi1/2     | 10.10.0.14/30   | SMLC-HQ-CoreSW2 Gi1/0/7 | 10.10.0.13   |

## Routing

- Default route: `route OUTSIDE 0.0.0.0 0.0.0.0 203.0.113.5 1`
- OSPF 15, RID 1.1.1.2, networks: 10.10.0.8/30, 10.10.0.12/30, 203.0.113.4/30, 203.0.113.8/30

## VPN

- Peer: 198.51.100.2 (SMLC-BR-FW1)
- Transform: esp-aes esp-sha-hmac
- IKEv1 group 2 (PT limitation)
- Crypto map CMAP on OUTSIDE interface

## Notes

- No DMZ interface on FW2 — DMZ is terminated on FW1 only

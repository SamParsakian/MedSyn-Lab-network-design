# SMLC-BR-FW1 — CONFIRMED ✓
Date confirmed: 2026-06-04

## Interfaces

| Interface | Nameif  | Security | IP                   |
|-----------|---------|----------|----------------------|
| Gi1/1     | INSIDE1 | 100      | 10.10.1.2/30         |
| Gi1/2     | INSIDE2 | 100      | 10.10.1.6/30         |
| Gi1/3     | OUTSIDE | 0        | 198.51.100.2/30      |

## Neighbour Map

| Interface | IP               | Neighbour              | Neighbour IP  |
|-----------|------------------|------------------------|---------------|
| Gi1/3     | 198.51.100.2/30  | ISP-BR1 Gi0/0          | 198.51.100.1  |
| Gi1/1     | 10.10.1.2/30     | SMLC-BR-CoreSW1 Gi1/0/1 | 10.10.1.1   |
| Gi1/2     | 10.10.1.6/30     | SMLC-BR-CoreSW2 Gi1/0/1 | 10.10.1.5   |

## Routing

- Default route: `route OUTSIDE 0.0.0.0 0.0.0.0 198.51.100.1 1`
- OSPF 15, RID 6.6.6.1, networks: 198.51.100.0/30, 10.10.1.0/30, 10.10.1.4/30

## VPN

> **Note — Packet Tracer limitation:** The ASA in PT does not display `show crypto isakmp sa` or `show crypto ipsec sa` output even when the tunnel is active. VPN functionality is verified by end-to-end ping below.

![VPN proof — Branch to HQ ping](../../images/SMLC-BR-FW1/vpn_branch_to_hq_ping.png)
> SMLC-BR-TechOps-PC1 pinging HQ HSRP gateway 172.16.20.1 — 4/4 replies, 0% loss. Traffic travels encrypted through the IPsec tunnel between SMLC-BR-FW1 (198.51.100.2) and SMLC-HQ-FW1 (203.0.113.2).

- Peer: 203.0.113.2 (SMLC-HQ-FW1 OUTSIDE)
- Transform: esp-aes esp-sha-hmac
- IKEv1 group 2 (PT limitation)
- Crypto map CMAP on OUTSIDE interface

## NAT

- BRANCH-MGMT-INSIDE1/2: 172.17.10.0/24 → OUTSIDE dynamic interface
- BRANCH-LAN-INSIDE1/2: 172.17.20.0/22 → OUTSIDE dynamic interface
- BRANCH-WLAN-INSIDE1/2: 172.17.48.0/22 → OUTSIDE dynamic interface

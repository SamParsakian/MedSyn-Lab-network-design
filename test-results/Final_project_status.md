# MedSyn Network — Final Project Status
Last updated: 2026-06-05

---

## Overall Result: PROJECT COMPLETE ✓

---

## What Is Working (Verified)

| Area | Status | Detail |
|------|--------|--------|
| HQ LAN routing (VLAN10/20/50 SVIs) | ✓ DONE | Ping HSRP VIP 172.16.20.1 — 4/4 |
| HQ → DMZ (all 6 servers reachable) | ✓ DONE | Ping 10.10.10.12 — 4/4 |
| HQ → Internet (NAT/PAT via FW1/FW2) | ✓ DONE | Ping 4.4.4.1 — 4/4 |
| IPsec VPN HQ ↔ Branch | ✓ DONE | 5/5 once SA established. PC-to-PC confirmed. |
| Branch internal routing | ✓ DONE | Ping 172.17.20.1 — 5/5 |
| Branch → Internet (NAT via SMLC-BR-FW1) | ✓ DONE | Ping 4.4.4.1 — 5/5 |
| Branch → HQ LAN via VPN | ✓ DONE | Ping 172.16.20.1 — 5/5 |
| DHCP — HQ wired (all departments) | ✓ DONE | All PCs get 172.16.20.x/22, GW 172.16.20.1, DNS 10.10.10.12 |
| DHCP — WLAN/VLAN50 (all APs) | ✓ DONE | All APs get 172.16.48.x/22, GW 172.16.50.1, DNS 10.10.10.12 |
| DHCP servers (6 pools) | ✓ DONE | SMLC-DHCP1 and SMLC-DHCP2 — identical pools for HQ and Branch |
| HSRP (HQ + Branch, VLANs 10/20/50) | ✓ DONE | Active/Standby confirmed |
| EtherChannel Po1 (HQ + Branch core switches) | ✓ DONE | Both sites confirmed |
| OSPF (all sites) | ✓ DONE | Routes redistributing correctly |
| SMLC-HQ-WLC1 + all 5 LAP-PT APs | ✓ DONE | All registered via CAPWAP |
| Wireless clients (HQ departments) | ✓ DONE | Clients connect to WLC WLANs, get 172.16.48.x/22 via DHCP |

---

## Device Configuration — All Complete

| Device | Config File |
|--------|-------------|
| INTERNET | configs/ISP/INTERNET.md |
| ISP-HQ1, ISP-HQ2, ISP-BR1 | configs/ISP/ |
| SMLC-HQ-FW1, SMLC-HQ-FW2 | configs/HQ/ |
| SMLC-BR-FW1 | configs/Branch/ |
| SMLC-HQ-CoreSW1, SMLC-HQ-CoreSW2 | configs/HQ/ |
| SMLC-BR-CoreSW1, SMLC-BR-CoreSW2 | configs/Branch/ |
| SMLC-DMZ-SW1 | configs/DMZ/ |
| HQ access switches (5) | configs/HQ/ |
| Branch access switches (4) | configs/Branch/ |
| DMZ servers (6) + DHCP pools | configs/DMZ/SMLC-DMZ-Servers.md |
| SMLC-HQ-WLC1 | configs/HQ/ |
| HQ APs (5) | configs/HQ/ |

---

## Design Decisions

| Item | Decision |
|------|----------|
| Branch end-device DHCP | Static IPs retained. Centralised DHCP across VPN requires NAT exemption — documented as academic design trade-off. All connectivity verified with static IPs. |

---

## Known Packet Tracer Limitations (not config errors)

| Issue | Notes |
|-------|-------|
| VPN SA cold-start | First ping after idle: 0–20%. After SA establishes: 5/5. Normal PT behaviour. |
| LACP Port-channel1 | PT does not form LACP reliably. `channel-group mode on` used. Non-critical. |

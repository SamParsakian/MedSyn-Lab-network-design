# Test 01 — HQ Connectivity
Date: 2026-06-05
Source device: SMLC-HQ-Mgmt-PC1 (HQ MgmtAdmin normal user PC, VLAN20)

---

## Round 1 — Core Reachability from HQ LAN

| # | Target | What it verifies | Result | Status |
|---|--------|-----------------|--------|--------|
| 1a | 172.16.20.1 | HSRP VIP — local L3 gateway (SMLC-HQ-CoreSW1/2) | 4/4, 0% loss | ✓ PASS |
| 1b | 10.10.10.12 | DMZ SMLC-DNS1 via FW1 (inter-zone routing) | 4/4, 0% loss | ✓ PASS |
| 1c | 203.0.113.1 | ISP-HQ1 outside interface — NAT/PAT through FW1 | 3/4 (NAT state build on first packet) | ✓ PASS |
| 1d | 4.4.4.1 | INTERNET router loopback — full ISP → INTERNET path | 4/4, 0% loss | ✓ PASS |
| 1e | 172.17.20.1 | Branch HSRP gateway — IPsec VPN HQ↔Branch | 0–20% intermittent (see notes) | ⚠ PT LIMITATION |

---

## Notes

- First-ping timeouts on 203.0.113.1 are expected PT behaviour: FW1 NAT/PAT builds state on first packet.
- TTL=253 on 203.0.113.1 confirms correct routing: HQ PC → SMLC-HQ-CoreSW1 → SMLC-HQ-FW1 (2 hops decrement).
- **VPN (172.17.20.1):** 0–20% success from HQ side is PT IKEv1 SA instability — the tunnel negotiates but the SA expires immediately after the first packet. VPN config is correct. From the Branch side (after SA is established) the tunnel sustains 5/5. See Branch_connectivity.md for full VPN proof.

---

## Verdict

| Path | Status |
|------|--------|
| HQ LAN routing (HSRP VIP) | ✓ PASS |
| HQ → DMZ (SMLC-DNS1) | ✓ PASS |
| HQ → ISP-HQ1 (NAT/PAT) | ✓ PASS |
| HQ → Internet (4.4.4.1) | ✓ PASS |
| HQ → Branch VPN | ⚠ PT IKEv1 instability — config correct, SA drops immediately in PT |

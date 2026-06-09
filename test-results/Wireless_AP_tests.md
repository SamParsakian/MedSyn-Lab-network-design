# Wireless AP Tests
Date: 2026-06-05

## Architecture

- SMLC-HQ-WLC1 (172.16.48.2) manages all LAP-PT APs via CAPWAP
- All APs auto-register when wired port is set to access VLAN50
- WLC pushes all WLANs: GUEST WIFI / AUDIT WIFI / EMPLOYEE WIFI / CORP WIFI
- All WLANs use WPA2-PSK
- Wireless clients get DHCP from HQ-VLAN50 pool: 172.16.48.x/22, GW 172.16.50.1, DNS 10.10.10.12

---

## AP Registration Tests

| AP | Switch Port | VLAN | GW (DHCP) | DNS (DHCP) | WLC Registered |
|----|-------------|------|-----------|------------|----------------|
| SMLC-HQ-MgmtAdmin-AP1 | SMLC-HQ-MgmtAdmin-SW1 Fa0/22 | VLAN50 | 172.16.50.1 ✓ | 10.10.10.12 ✓ | ✓ (172.16.48.10) |
| SMLC-HQ-BizOps-LAP | SMLC-HQ-BizOps-SW1 Fa0/23 | VLAN50 | 172.16.50.1 ✓ | 10.10.10.12 ✓ | ✓ |
| SMLC-HQ-Finance-LAP | SMLC-HQ-Finance-SW1 Fa0/22 | VLAN50 | 172.16.50.1 ✓ | 10.10.10.12 ✓ | ✓ |
| SMLC-HQ-TechOps-LAP | SMLC-HQ-TechOps-SW1 Fa0/23 | VLAN50 | 172.16.50.1 ✓ | 10.10.10.12 ✓ | ✓ |
| SMLC-HQ-ITInfra-LAP | SMLC-HQ-ITInfra-SW1 Fa0/23 | VLAN50 | 172.16.50.1 ✓ | 10.10.10.12 ✓ | ✓ |

---

## Wireless Client Tests

| Client | SSID Used | IP Received | Subnet | GW | Result |
|--------|-----------|-------------|--------|----|--------|
| SMLC-HQ-MgmtAdmin-TAB1 | GUEST WIFI | 172.16.48.24 | /22 | 172.16.50.1 | ✓ Connected |
| SMLC-HQ-BizOps-TAB | AUDIT WIFI | 172.16.48.22 | /22 | 172.16.50.1 | ✓ Connected |
| SMLC-HQ-ITInfra-LAP clients | any WLC SSID | 172.16.48.x | /22 | 172.16.50.1 | ✓ AP registered |

---

## Notes

- All WLC WLANs work with the same PSK — clients can use any SSID name
- Wireless clients connect to the nearest AP regardless of department (normal PT behaviour)
- All 5 APs confirmed registered with SMLC-HQ-WLC1

---

## Finance DHCP — Resolved

| Device | IP | Mask | GW | DNS | Result |
|--------|-----|------|----|-----|--------|
| SMLC-HQ-Finance-PC1 | 172.16.20.17 | 255.255.252.0 | 172.16.20.1 | 10.10.10.12 | ✓ DHCP working |

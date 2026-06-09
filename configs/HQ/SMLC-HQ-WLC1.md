# SMLC-HQ-WLC1 — CONFIRMED ✓
Date confirmed: 2026-06-05

## Device Type

- PT device: WLC (Wireless LAN Controller)
- Manages all HQ LAP-PT access points via CAPWAP protocol

## Physical Connection

- Wired uplink: **SMLC-HQ-CoreSW1 Gi1/0/10** (access VLAN50)

## Management Interface

| Field | Value |
|-------|-------|
| IPv4 Address | 172.16.48.2 |
| Subnet Mask | 255.255.252.0 |
| Default Gateway | 172.16.50.1 |
| DNS Server | 10.10.10.12 |

## WLANs (pushed to all registered APs)

| WLAN Name | SSID | Auth |
|-----------|------|------|
| EMPLOYEES | EMPLOYEE WIFI | WPA2-PSK |
| CORPORATE USERS | CORP WIFI | WPA2-PSK |
| EXTERNAL AUDITORS | AUDIT WIFI | WPA2-PSK |
| GUEST USERS | GUEST WIFI | WPA2-PSK |

## Notes

- All 4 WLANs broadcast across all registered APs via CAPWAP
- SMLC-HQ-CoreSW1 Gi1/0/10 must be access VLAN50 for WLC management connectivity
- APs register automatically when their wired uplink port is access VLAN50

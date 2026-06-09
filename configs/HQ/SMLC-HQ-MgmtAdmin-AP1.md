# SMLC-HQ-MgmtAdmin-AP1 — CONFIRMED ✓
Date confirmed: 2026-06-05

## Device Type

- Model: **LAP-PT** (Lightweight Access Point — managed by WLC via CAPWAP)
- All wireless config lives on WLC, not the AP

## Physical Connection

- Wired uplink: **SMLC-HQ-MgmtAdmin-SW1 Fa0/22** → access VLAN50

## Runtime Status

```
GigabitEthernet0:  Up   IP: 172.16.48.10/22   (DHCP from VLAN50 pool)
Dot11Radio0:       Up
CAPWAP Status:     Connected to 172.16.48.2    (SMLC-HQ-WLC1)
```

## WLANs Being Broadcast (defined on WLC)

- EMPLOYEES (EMPLOYEE WIFI)
- CORPORATE USERS (CORP WIFI)
- EXTERNAL AUDITORS (AUDIT WIFI)
- GUEST USERS (GUEST WIFI)

## Wireless Clients in MgmtAdmin Department

- SMLC-HQ-MgmtAdmin-LAP1 — laptop
- SMLC-HQ-MgmtAdmin-TAB1 — tablet
- SMLC-HQ-MgmtAdmin-MOB1 — smartphone

## Notes

- LAP-PT devices are centrally managed — SSID, security, and VLAN are all configured on WLC
- AP just registers with WLC and broadcasts whatever WLC pushes via CAPWAP

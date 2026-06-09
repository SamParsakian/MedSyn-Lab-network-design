# Naming Conventions — Sam Medsyn Lab Company

## Convention Format

`SMLC-[SITE]-[DEPT]-[DEVICE][NUMBER]`

| Part | Meaning |
|------|---------|
| `SMLC` | Sam Medsyn Lab Company |
| `SITE` | `HQ` or `BR` |
| `DEPT` | Department short name |
| `DEVICE` | Device type (SW, PC, PRN, LAP, TAB, MOB, AP, FW, etc.) |
| `NUMBER` | Sequential number |

**MgmtAdmin exception:** Normal user PCs and admin workstations use shorter role-based labels (`Mgmt-*` and `Admin-*`) to match the topology box. Infrastructure and wireless devices keep the full `MgmtAdmin-*` prefix.

---

## Department Codes

| Department | HQ Access Switch |
|------------|------------------|
| MgmtAdmin  | SMLC-HQ-MgmtAdmin-SW1 |
| BizOps     | SMLC-HQ-BizOps-SW1 |
| Finance    | SMLC-HQ-Finance-SW1 |
| TechOps    | SMLC-HQ-TechOps-SW1 |
| ITInfra    | SMLC-HQ-ITInfra-SW1 |

| Department | Branch Access Switch |
|------------|----------------------|
| TechOps    | SMLC-BR-TechOps-SW1 |
| FieldOps   | SMLC-BR-FieldOps-SW1 |
| BizOps     | SMLC-BR-BizOps-SW1 |
| Support    | SMLC-BR-Support-SW1 |

---

## Network Infrastructure

| Device |
|--------|
| SMLC-HQ-CoreSW1 |
| SMLC-HQ-CoreSW2 |
| SMLC-HQ-FW1 |
| SMLC-HQ-FW2 |
| SMLC-BR-CoreSW1 |
| SMLC-BR-CoreSW2 |
| SMLC-BR-FW1 |
| SMLC-DMZ-SW1 |
| SMLC-HQ-WLC1 |

---

## ISP and External

| Device |
|--------|
| INTERNET |
| ISP-HQ1 |
| ISP-HQ2 |
| ISP-BR1 |
| EXT-DNS1 |
| EXT-WEB1 |
| EXT-SW1 |

---

## DMZ Servers

| Device |
|--------|
| SMLC-DHCP1 |
| SMLC-DHCP2 |
| SMLC-DNS1 |
| SMLC-WEB1 |
| SMLC-MAIL1 |
| SMLC-FTP1 |

---

## HQ Endpoints — MgmtAdmin Department

| Device | Type |
|--------|------|
| SMLC-HQ-MgmtAdmin-SW1 | Access switch |
| SMLC-HQ-Mgmt-PC1 | Normal user PC (VLAN 20) |
| SMLC-HQ-Mgmt-PC2 | Normal user PC (VLAN 20) |
| SMLC-HQ-Mgmt-PRN1 | Printer (VLAN 20) |
| SMLC-HQ-Admin-PC1 | Admin workstation (VLAN 10) |
| SMLC-HQ-Admin-PC2 | Admin workstation (VLAN 10) |
| SMLC-HQ-MgmtAdmin-AP1 | Lightweight access point — wired uplink (VLAN 50) |
| SMLC-HQ-MgmtAdmin-LAP1 | Wireless laptop client |
| SMLC-HQ-MgmtAdmin-TAB1 | Wireless tablet client |
| SMLC-HQ-MgmtAdmin-MOB1 | Wireless smartphone client |

---

## Branch Endpoints

| Device |
|--------|
| SMLC-BR-TechOps-PC1 |
| SMLC-BR-FieldOps-PC1 |
| SMLC-BR-BizOps-PC1 |
| SMLC-BR-Support-PC1 |

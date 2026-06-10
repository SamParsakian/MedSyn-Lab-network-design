# CML Version — MedSyn Lab Company Network

Same enterprise network design implemented in **Cisco Modeling Labs (CML)** using IOSv/IOSvL2 images.

## Structure

```
cml-version/
├── Sam-MedSyn-Lab-Network-Design.yaml   — full CML topology (import this to recreate the lab)
├── configs/                             — running-config exports for all 33 devices (.txt)
│   ├── Firewalls:   SMLC-HQ-FW1/2, SMLC-BR-FW1
│   ├── Core SW:     SMLC-HQ-CoreSW1/2, SMLC-BR-CoreSW1/2
│   ├── Access SW:   HQ (MgmtAdmin, BizOps, Finance, TechOps, ITInfra)
│   │                Branch (TechOps, FieldOps, BizOps, Support)
│   ├── DMZ:         SMLC-DMZ-SW1, servers (DHCP, DNS, WEB, MAIL, FTP)
│   ├── ISP:         INTERNET, ISP-HQ1, ISP-HQ2, ISP-BR1
│   └── External:    EXT-SW1, EXT-DNS1
└── screenshots/                         — 11 annotated screenshots of the running lab
    ├── 01_topology-overview.png                — full lab topology in CML workbench
    ├── 02_HQ-department-groups.png             — HQ dept groups (MgmtAdmin/BizOps/Finance/TechOps/ITInfra)
    ├── 03_WAN-core-DMZ-area.png                — WAN core, ISPs, firewalls, DMZ cluster
    ├── 04_WAN-firewalls-ISP-topology.png       — dual-ISP + dual-firewall WAN close-up
    ├── 05_Branch-department-groups.png         — Branch dept groups (TechOps/FieldOps/BizOps/Support)
    ├── 06_Branch-topology-workbench.png        — Branch CoreSW1/2 + access switches
    ├── 07_HQ-MgmtAdmin-BizOps-groups.png      — MgmtAdmin & BizOps groups close-up
    ├── 08_MgmtAdmin-SW1-running-config.png     — CML config panel: SMLC-HQ-MgmtAdmin-SW1
    ├── 09_HQ-FW1-running-config.png            — CML config panel: SMLC-HQ-FW1 (ASA)
    ├── 10_ISP-HQ1-running-config.png           — CML config panel: ISP-HQ1 (IOS router)
    └── 11_lab-running-complete.png             — full lab running, all nodes up
```

## Notes

- Interface names differ from the PT version (Gi0/x style vs Fa0/x for WAN links)
- Core design, IP addressing, VLANs, OSPF (process 15), HSRP, and IPsec VPN are identical to the PT version
- To recreate: import the `.yaml` file into CML → start the lab → configs auto-apply via day0

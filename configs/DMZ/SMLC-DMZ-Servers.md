# DMZ Servers — CONFIRMED ✓
Date confirmed: 2026-06-04

All servers configured with static IPs via GUI → Desktop → IP Configuration.

| Server     | IP           | Subnet Mask         | Gateway    | DNS         |
|------------|--------------|---------------------|------------|-------------|
| SMLC-DHCP1 | 10.10.10.10  | 255.255.255.192 /26 | 10.10.10.1 | 10.10.10.12 |
| SMLC-DHCP2 | 10.10.10.11  | 255.255.255.192 /26 | 10.10.10.1 | 10.10.10.12 |
| SMLC-DNS1  | 10.10.10.12  | 255.255.255.192 /26 | 10.10.10.1 | 10.10.10.12 |
| SMLC-WEB1  | 10.10.10.13  | 255.255.255.192 /26 | 10.10.10.1 | 10.10.10.12 |
| SMLC-MAIL1 | 10.10.10.14  | 255.255.255.192 /26 | 10.10.10.1 | 10.10.10.12 |
| SMLC-FTP1  | 10.10.10.15  | 255.255.255.192 /26 | 10.10.10.1 | 10.10.10.12 |

All servers are on VLAN 100 (DMZ), connected via SMLC-DMZ-SW1 Fa0/2-7.  
Gateway: SMLC-HQ-FW1 Gi1/3 (10.10.10.1)

## DHCP Pools (on SMLC-DHCP1 and SMLC-DHCP2)

Both DHCP servers carry identical pools for redundancy:

| Pool Name   | Subnet          | Gateway      | DNS         |
|-------------|-----------------|--------------|-------------|
| HQ-VLAN10   | 172.16.10.0/24  | 172.16.10.1  | 10.10.10.12 |
| HQ-VLAN20   | 172.16.20.0/22  | 172.16.20.1  | 10.10.10.12 |
| HQ-VLAN50   | 172.16.48.0/22  | 172.16.50.1  | 10.10.10.12 |
| BR-VLAN10   | 172.17.10.0/24  | 172.17.10.1  | 10.10.10.12 |
| BR-VLAN20   | 172.17.20.0/22  | 172.17.20.1  | 10.10.10.12 |
| BR-VLAN50   | 172.17.48.0/22  | 172.17.50.1  | 10.10.10.12 |

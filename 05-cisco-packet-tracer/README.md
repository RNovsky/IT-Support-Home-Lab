# Cisco Packet Tracer — HQ and Branch Network Lab

## Overview

I built a simulated two-site network in Cisco Packet Tracer to practice VLANs, switching, routing, DHCP, DNS, HTTP, and access control lists.

The network connects a headquarters site (HQ) and a branch office. Internal users can access a web portal and a network printer, while guest traffic is restricted using extended IPv4 ACLs.

## Network Design

### Headquarters

- R1-HQ provides inter-VLAN routing using 802.1Q subinterfaces.
- SW1-HQ connects IT, HR, guest devices, a server, and a printer.
- SRV1-DNS-WEB provides DNS and HTTP services.
- PRN1-HQ uses a static IP address in the HR VLAN.

### Branch

- R2-BRANCH provides inter-VLAN routing for SALES and guest users.
- A branch switch connects the local PCs.
- Static routes provide connectivity between HQ and Branch.

### Addressing Plan

| Site | VLAN | Department | Subnet | Gateway |
|---|---|---|---|---|
| HQ | 10 | IT | 192.168.10.0/24 | 192.168.10.1 |
| HQ | 20 | HR | 192.168.20.0/24 | 192.168.20.1 |
| HQ | 40 | GUEST-HQ | 192.168.40.0/24 | 192.168.40.1 |
| Branch | 30 | SALES | 192.168.30.0/24 | 192.168.30.1 |
| Branch | 50 | GUEST-BRANCH | 192.168.50.0/24 | 192.168.50.1 |

| Device or Link | IPv4 Address |
|---|---|
| R1-HQ WAN interface | 10.0.0.1 |
| R2-BRANCH WAN interface | 10.0.0.2 |
| DNS/Web server | 192.168.10.10 |
| HQ printer | 192.168.20.20 |

## Configuration Steps

1. Configured the WAN link and tested connectivity between the routers.
2. Created VLANs and assigned switch access ports.
3. Configured 802.1Q trunks and router subinterfaces.
4. Added static routes for the remote VLANs on both routers.
5. Created local DHCP pools on R1-HQ and R2-BRANCH.
6. Assigned static IP settings to the server and printer.
7. Enabled DNS and added an A record for `portal.lab.test`.
8. Enabled HTTP and tested the portal from HQ and Branch.
9. Applied inbound extended ACLs to the guest subinterfaces.
10. Tested permitted and blocked traffic, then saved device configurations.

## DHCP

Each VLAN uses a DHCP range from `.100` through `.200`.

Addresses `.1`–`.99` and `.201`–`.254` are excluded from allocation to reserve space for gateways and static devices.

IT, HR, and SALES clients receive `192.168.10.10` as their DNS server. Guest pools do not distribute an internal DNS server.

## DNS and Web Services

The server uses the following DNS record:

| Name | Type | Address |
|---|---|---|
| portal.lab.test | A | 192.168.10.10 |

DNS resolution was tested with `nslookup`. The portal was accessed using `http://portal.lab.test` from IT at HQ and SALES at Branch.

## Guest Access Controls

| ACL | Router Interface | Direction |
|---|---|---|
| GUEST-HQ-IN | R1-HQ GigabitEthernet0/0.40 | Inbound |
| GUEST-BRANCH-IN | R2-BRANCH GigabitEthernet0/0.50 | Inbound |

Each ACL denies IPv4 traffic to the other four VLAN subnets and permits remaining IPv4 traffic.

The scope is routed IPv4 traffic entering these guest interfaces. This lab does not demonstrate Internet access or filtering between devices within the same VLAN.

## Validation

| Test | Result |
|---|---|
| R2 to R1 WAN ping | Passed |
| DHCP configuration on all five PCs | Passed |
| HR to IT connectivity | Passed |
| SALES to HQ connectivity | Passed |
| DNS resolution from IT | Passed |
| Portal access from IT and SALES | Passed |
| Printer connectivity from HR, IT, and SALES | Passed |
| Guest HQ to server and printer after ACL | Blocked |
| Guest Branch to SALES, server, and printer after ACL | Blocked |
| Guest gateway connectivity after ACL | Passed |
| SALES portal and printer access after ACL | Passed |
| DHCP renewal on both guest PCs after ACL | Passed; manually confirmed without screenshots |

ACL counters on R1-HQ showed matches for the denied IT and HR traffic. Other configured deny rules require their own tests to demonstrate coverage.

Printer testing covered network connectivity only, not drivers or print jobs.

## Troubleshooting

- Corrected a mistyped DNS address in the SALES DHCP pool and refreshed the client configuration.
- A Guest Branch client initially received an APIPA address. A repeated DHCP request succeeded; the original cause was not established.
- Compared guest connectivity before and after applying ACLs.


## Skills Practiced

- IPv4 addressing and subnetting
- VLANs, access ports, and 802.1Q trunks
- Router-on-a-stick inter-VLAN routing
- Static routing between sites
- DHCP pools and address exclusions
- DNS records and HTTP services
- Extended IPv4 ACLs
- Connectivity testing and troubleshooting

## Project Files

- [Packet Tracer lab (.pkt)](packet-tracer/hq-branch-network-lab.pkt)
- [Lab screenshots](screenshots/)

Download the `.pkt` file and open it in Cisco Packet Tracer to explore the network.

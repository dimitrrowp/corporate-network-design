### This folder contains network device configurations.

### Access Layer Scaling Note:
This configuration is reused for all other access switches. Only the interface numbers and the Management IP (VLAN 199) are changed to keep each switch unique.

### Core Redundancy Note:
CORE-SW2 uses the same settings as CORE-SW1 for VLANs, Routing, and SSH. The HSRP priority is set to 105 (Standby), and DHCP pools are mirrored to ensure the network stays up if one core fails.

### OSPF Configuration Note
The **BACKUP-ROUTER** uses the same OSPF configuration but with `router-id 2.2.2.2`. This setup ensures that both routers automatically exchange routing information with the CORE switches, maintaining network-wide reachability.

### Static Route & NAT Note
These settings secure internet access. **PRIMARY-ROUTER** acts as the main exit point, while **BACKUP-ROUTER** serves as the redundancy path. NAT (Network Address Translation) is configured to allow all internal networks (192.168.0.0/16) to access the internet using a single public IP address via PAT (Overload).

### IP Addressing Scheme
The network follows a structured IP addressing plan to ensure logical segmentation, scalability, and easy management.
VLAN Networks:

VLAN 10 – 192.168.10.0/24 --> Reception
VLAN 20 – 192.168.20.0/24 --> HR
VLAN 30 – 192.168.30.0/24 --> Finance
VLAN 40 – 192.168.40.0/24 --> IT
VLAN 50 – 192.168.50.0/24 --> NETAdmin
VLAN 60 – 192.168.60.0/24 --> ServiceDesk
VLAN 70 – 192.168.70.0/24 --> SALES 
VLAN 80 – 192.168.80.0/24 --> Logistics
VLAN 90 – 192.168.90.0/24 --> CS
VLAN 100 – 192.168.100.0/28 --> Servers
VLAN 199 - 192.168.199.0/24 --> Management

#### Transit & Infrastructure Networks (Point-to-Point)
CORE-SW1 ↔ CORE-SW2 (VLAN 999): 10.10.10.0/30 (L2/L3 EtherChannel Link)

CORE-SW1 ↔ PRIMARY ROUTER: 10.10.1.0/30 (Main Edge Link)

CORE-SW2 ↔ BACKUP ROUTER: 10.10.2.0/30 (Backup Edge Link)

Router ↔ ISP: 200.1.1.0/30 (Public Internet Peering)

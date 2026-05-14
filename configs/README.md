### This folder contains network device configurations.

### Access Layer Scaling Note:
This configuration is reused for all other access switches. Only the interface numbers and the Management IP (VLAN 199) are changed to keep each switch unique.

### Core Redundancy Note:
CORE-SW2 uses the same settings as CORE-SW1 for VLANs, Routing, and SSH. The HSRP priority is set to 105 (Standby), and DHCP pools are mirrored to ensure the network stays up if one core fails.

### OSPF Configuration Note
The **BACKUP-ROUTER** uses the same OSPF configuration but with `router-id 2.2.2.2`. This setup ensures that both routers automatically exchange routing information with the CORE switches, maintaining network-wide reachability.

### Static Route & NAT Note
These settings secure internet access. **PRIMARY-ROUTER** acts as the main exit point, while **BACKUP-ROUTER** serves as the redundancy path. NAT (Network Address Translation) is configured to allow all internal networks (192.168.0.0/16) to access the internet using a single public IP address via PAT (Overload).

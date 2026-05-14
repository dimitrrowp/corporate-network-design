### This folder contains network device configurations.

### Note on Access Layer Scaling:
This configuration is reused for all other access switches. Only the interface numbers and the Management IP (VLAN 199) are changed to keep each switch unique.

### Note on Core Redundancy:
CORE-SW2 uses the same settings as CORE-SW1 for VLANs, Routing, and SSH. The HSRP priority is set to 105 (Standby), and DHCP pools are mirrored to ensure the network stays up if one core fails.



# Corporate-Network-Design

This project is a simple implementation of a corporate network for a three-floor organization.  
The goal is to separate departments, improve network performance, and provide basic redundancy.

## Overview
![Network Topology](https://github.com/dimitrrowp/corporate-network-design/blob/5abe3b127964216eb0ab6125de27e1e1ec0ea04c/Screenshot%202026-05-14%20175927.png)

The network is designed using VLANs for each department, with routing handled by multilayer switches.  
Basic technologies like OSPF, HSRP, DHCP, and NAT are included to simulate a real enterprise environment.

## Structure
- configs/ → device configurations (routers & switches)
- docs/ → project documentation
- images/ → network topology

## Technologies Used
- VLANs (network segmentation)
- OSPF (routing)
- HSRP (redundancy)
- DHCP (automatic IP assignment)
- NAT (external access)

## Notes
This project is created for learning purposes and demonstrates fundamental networking concepts.

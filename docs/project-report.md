# Corporate Network Design Report

## Abstract
This project presents the design and implementation of a three-floor corporate network based on a collapsed core architecture. The network utilizes VLAN segmentation, inter-VLAN routing, and OSPF dynamic routing to ensure efficient communication between departments. High availability is achieved through HSRP and redundant links, while DHCP services provide automatic IP address assignment. Additionally, NAT is configured for external connectivity, and SSH ensures secure remote management. The final design delivers a scalable, reliable, and secure network solution.

## Introduction
This project focuses on designing a network for a three-floor organization. Each department is placed in a separate VLAN in order to improve performance and keep the network traffic organized.
The network is built using a collapsed core architecture, where multilayer switches are used for both switching and routing. Technologies such as OSPF, HSRP, and DHCP are implemented to provide connectivity, redundancy, and automatic IP address assignment.
SSH is configured to allow secure remote access only from specific networks, while NAT is used on the router to provide access to external networks.
The main goal of this project is to create a network that is reliable, easy to manage, and able to handle failures without interrupting connectivity.

## Network Topology Description
The network is designed using a three-floor hierarchical structure based on a collapsed core architecture. Each floor contains one access switch responsible for connecting end devices and one multilayer switch that performs both Layer 2 and Layer 3 functions. 

The multilayer switches act as the core of the network and are interconnected using the OSPF dynamic routing protocol over a dedicated transit network (VLAN 999). This enables fast convergence and dynamic route exchange between the core devices. 

Each multilayer switch is connected to a dedicated edge router. OSPF is also established between each multilayer switch and its respective router, ensuring dynamic routing within the internal and edge layers. 

The edge routers are connected to the ISP using static routing, providing controlled and simplified external connectivity.

Each access switch is dual-homed to both multilayer switches through trunk links, providing high availability and eliminating single points of failure. This ensures continuous network operation even if one multilayer switch fails.
VLAN segmentation is implemented across all floors to logically separate departments and control broadcast domains, improving both performance and security.

## Network Design

The network is designed using a collapsed core architecture, where multilayer switches handle both Layer 2 and Layer 3 operations.  

These switches act as default gateways for all VLANs using SVIs. HSRP is used to provide redundancy and ensure that if one device fails, another takes over automatically.  

DHCP is configured with a split-scope approach to maintain reliable IP address distribution.  

Access switches are connected to both multilayer switches, which helps avoid single points of failure and improves overall network reliability.

## Testing and Verification

The network was tested to ensure proper functionality, redundancy, and security.

### Connectivity Tests
- Successful ping between devices in different VLANs (Inter-VLAN routing verified)
- End-to-end connectivity between internal network and external (ISP)

### DHCP Verification
- Automatic IP address assignment confirmed for all VLANs
- Correct default gateway and DNS server received by clients

### Redundancy Tests
- Port-channel remains operational when one physical link fails
- Access switches maintain connectivity when one uplink fails (failover to second CORE switch)
- HSRP failover tested – standby device successfully takes over as active gateway

### Routing Verification
- OSPF neighbor relationships successfully established
- Routes dynamically learned and updated

### Security Tests
- SSH remote access works only from allowed networks (192.168.40.0 and 192.168.50.0)
- Unauthorized networks are denied access


## Conclusion
The implemented network provides a scalable, secure, and highly available solution based on a collapsed core architecture.
By integrating VLAN segmentation, inter-VLAN routing, OSPF dynamic routing, HSRP redundancy, DHCP services, and NAT for external connectivity, the network ensures reliable communication and fault tolerance.
All design goals were successfully achieved, including redundancy, efficient traffic management, and secure remote access.

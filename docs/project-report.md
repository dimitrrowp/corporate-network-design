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

##VLAN and Floor Distribution
Floor 1: VLAN 10, 20, 30
Floor 2: VLAN 40, 50, 60
Floor 3: VLAN 70, 80, 90
Server VLAN: VLAN 100
The network is logically segmented using VLANs, with each department assigned a dedicated subnet. This design improves security, reduces broadcast domains, and enhances overall network performance.
### Floor 1 
   Floor 1 includes the following departments:
-	Reception (VLAN 10 – 192.168.10.0/24)
-	Human Resources (HR) (VLAN 20 – 192.168.20.0/24)
-	Finance (VLAN 30 – 192.168.30.0/24)
### Floor 2
   Floor 2 includes:
-	IT Department (VLAN 40 – 192.168.40.0/24)
-	Network Administration (VLAN 50 – 192.168.50.0/24)
-	Management (VLAN 60 – 192.168.60.0/24)
### Floor 3
   Floor 3 includes:
-	Sales (VLAN 70 – 192.168.70.0/24)
-	Logistics (VLAN 80 – 192.168.80.0/24)
-	Customer Support (CS) (VLAN 90 – 192.168.90.0/24)

In addition, a separate server network is implemented:
- Server Network (VLAN 100 – 192.168.100.0/28)
This VLAN is used for centralized services such as servers and is not tied to a specific floor, ensuring controlled and secure access from all departments.


## Network Design

The network is designed using a collapsed core architecture, where multilayer switches handle both Layer 2 and Layer 3 operations.  

These switches act as default gateways for all VLANs using SVIs. HSRP is used to provide redundancy and ensure that if one device fails, another takes over automatically.  

DHCP is configured with a split-scope approach to maintain reliable IP address distribution.  

Access switches are connected to both multilayer switches, which helps avoid single points of failure and improves overall network reliability.

##Technologies Implemented
### VLAN
   Each department is assigned to a separate VLAN to isolate traffic, reduce broadcast domains, and improve overall network performance.
### Inter-VLAN Routing
   Inter-VLAN communication is achieved using Switch Virtual Interfaces (SVIs) configured on the multilayer switches.
### OSPF Routing
   OSPF is configured between the multilayer switches and the edge routers to enable dynamic routing and fast convergence within the internal network.
### DHCP
   DHCP services are configured on both multilayer switches using a split-scope design. The address pools are divided to provide redundancy and ensure continuous IP address allocation in case of device failure.
### SSH Configuration
   SSH is configured on all multilayer switches, access switches, and routers to allow secure remote management. Access is restricted using access control lists (ACLs), permitting only specific networks (e.g., 192.168.40.0 and 192.168.50.0).
### Port Security
   Port security can be implemented on access switch ports to enhance network security by restricting unauthorized devices.


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

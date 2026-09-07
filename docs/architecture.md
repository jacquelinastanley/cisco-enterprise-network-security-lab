# Architecture

## Design goal

Create a resilient multi-site enterprise network in Cisco Packet Tracer that supports departmental segmentation, dynamic routing, redundant gateway services, centralized wireless management, shared server services, and Layer 2 security controls.

## Sites

### Kuala Lumpur HQ

The HQ network is segmented into Management, Human Resources, Design, and Delivery VLANs. A multilayer switch provides inter-VLAN routing and trunks connect the access switches back to the Layer 3 distribution point.

### Krung Thep remote branch

The branch combines wired and wireless access, multiple R&D floor segments, an IT segment, management, voice, and a dedicated WLC management network. Two routers provide HSRP-based gateway redundancy.

### Server farm

A dedicated server-farm segment hosts DNS, HTTP/HTTPS, FTP, and backup DHCP services. The server farm is connected to the wider routed topology so users at both sites can reach shared services.

## Routing and switching layers

- **Access switching:** endpoint VLAN assignment and unused-port isolation
- **Distribution / Layer 3 switching:** SVI-based inter-VLAN routing
- **WAN routing:** dynamic routing using OSPF between major network segments
- **First-hop redundancy:** HSRP at the remote site
- **Layer 2 resilience:** EtherChannel and STP

## Wireless design

The remote branch separates WLC management from user traffic. Lightweight access points are centrally managed by the WLC. FlexConnect concepts are used to keep branch client forwarding/authentication functional locally while maintaining centralized control.

## Reliability choices

- HSRP provides active/standby router failover.
- EtherChannel reduces the impact of a single physical uplink failure.
- STP protects redundant Layer 2 paths from loops.
- A backup DHCP service reduces dependency on a single DHCP source.

## Security design

The lab evaluates four Layer 2 attack classes:

1. STP manipulation
2. VLAN hopping / switch spoofing
3. MAC address spoofing
4. CDP reconnaissance

Mitigations include Root Guard, BPDU Guard, explicit access-port configuration, DTP suppression, port-security policies, blackhole VLANs, and CDP disablement where discovery is not required.

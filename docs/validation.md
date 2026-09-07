# Validation Checklist

Use this checklist after opening the Packet Tracer topology.

## Layer 2

- [ ] VLANs exist on the expected switches
- [ ] Access ports are assigned to the correct VLANs
- [ ] Native VLANs are configured as designed
- [ ] Unused interfaces are assigned to the blackhole VLAN
- [ ] Trunk links carry the required VLANs only
- [ ] EtherChannel member links are bundled and forwarding
- [ ] STP has a stable root bridge and expected forwarding/blocking roles

Useful commands:

```text
show vlan brief
show interfaces trunk
show etherchannel
show etherchannel summary
show spanning-tree
```

## Layer 3

- [ ] SVIs are up/up
- [ ] Inter-VLAN routing is working
- [ ] OSPF routes appear in the routing table
- [ ] Remote networks are reachable
- [ ] HSRP active/standby states match the design

Useful commands:

```text
show ip interface brief
show ip route
show standby
```

## DHCP and wireless

- [ ] Wireless clients obtain addresses dynamically
- [ ] DHCP pools contain the expected ranges/options
- [ ] DHCP bindings appear after clients request leases
- [ ] WLC-managed APs are visible and operational

Useful commands:

```text
show ip dhcp pool
show ip dhcp binding
```

## Server services

- [ ] DNS resolves the internal web-service hostname
- [ ] HTTP/HTTPS page is reachable
- [ ] FTP authentication/transfer succeeds
- [ ] Server-farm clients can reach both sites

## End-to-end routing

Test traffic between branch and HQ endpoints:

```text
ping <remote-host>
traceroute <remote-host>
```

A documented cross-site test completed with **4 packets sent, 4 received, 0 lost**.

## Security controls

- [ ] BPDU Guard / Root Guard applied where appropriate
- [ ] Access-facing ports do not dynamically negotiate trunks
- [ ] Port security limits learned MAC addresses
- [ ] Violation action behaves as expected
- [ ] CDP is disabled on devices/interfaces where it is not needed

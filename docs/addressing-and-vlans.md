# Addressing and VLANs

## Kuala Lumpur HQ

| Department | VLAN | Network | Default gateway |
|---|---:|---|---|
| Management | 10 | `192.168.10.0/24` | `192.168.10.1` |
| Human Resources | 20 | `192.168.20.0/24` | `192.168.20.1` |
| Design | 30 | `192.168.30.0/24` | `192.168.30.1` |
| Delivery | 40 | `192.168.40.0/24` | `192.168.40.1` |
| Native | 100 | N/A | N/A |
| Blackhole / unused ports | 200 | N/A | N/A |

## Krung Thep remote branch

The branch design uses the following logical VLAN structure:

| VLAN | Purpose |
|---:|---|
| 5 | WLC Management |
| 10 | Management Network |
| 20 | IT Department |
| 30 | R&D Floor 1 |
| 40 | R&D Floor 2 |
| 50 | R&D Floor 3 |
| 60 | Voice |
| 99 | Native VLAN |
| 200 | Blackhole / unused ports |

The original lab uses multiple `/24` IPv4 networks across the branch and a separate WLC management segment. When publishing the Packet Tracer file, keep this document synchronized with the exact interface addresses in the `.pkt` topology.

## Server farm

The documented server-farm segment uses `192.180.100.0/24` with a default gateway at `192.180.100.1`.

Documented endpoints include:

- DNS server: `192.180.100.2`
- HTTP server: `192.180.100.3`
- FTP server: `192.180.100.5`
- PC0: `192.180.100.11`
- PC1: `192.180.100.12`

## Addressing note

This repository preserves the addressing used in the original lab where it is clearly documented. Before using the design outside Packet Tracer, replace public-looking lab ranges with RFC1918 private addressing and produce a formal subnet allocation plan.

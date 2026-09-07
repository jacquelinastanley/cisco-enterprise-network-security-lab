# Layer 2 Security Testing

> These scenarios are documented as defensive lab exercises in an isolated Packet Tracer environment.

## 1. STP manipulation

### Risk

A rogue switch can attempt to advertise superior BPDUs and influence root-bridge selection. If successful, traffic paths may be redirected or network availability may be affected.

### Defensive controls

- **Root Guard** on ports where a superior BPDU should never be accepted
- **BPDU Guard** on edge/access ports where switches should not appear

### Verification

Use:

```text
show spanning-tree
```

Confirm that the intended root bridge remains in control and edge ports are protected.

---

## 2. VLAN hopping / switch spoofing

### Risk

An attacker may try to make an access-facing port negotiate a trunk and gain visibility into traffic from multiple VLANs.

### Defensive controls

```text
switchport mode access
switchport nonegotiate
```

Also use dedicated native VLANs and blackhole VLANs for unused interfaces.

### Verification

```text
show interfaces trunk
show vlan brief
```

Access ports should not appear as dynamically negotiated trunks.

---

## 3. MAC address spoofing

### Risk

An unauthorized endpoint may impersonate an approved MAC address to bypass basic Layer 2 trust assumptions.

### Defensive controls

```text
switchport port-security
switchport port-security maximum 1
switchport port-security mac-address sticky
switchport port-security violation restrict
```

The lab also considers stronger enterprise access control through 802.1X/RADIUS as a future improvement.

### Verification

```text
show port-security
show port-security interface <interface>
show run | section port-security
```

---

## 4. CDP reconnaissance

### Risk

CDP can reveal neighboring Cisco devices and useful topology information to an attacker with local Layer 2 access.

### Defensive control

Disable CDP when it is no longer required:

```text
no cdp run
```

### Verification

```text
show cdp neighbors
show cdp neighbors detail
```

After CDP is disabled globally, the device should report that CDP is not enabled.

## Security improvement roadmap

The wider design identifies the following additional controls:

- IPS for inline detection and automated response
- IDS / SIEM-style monitoring for alerting and visibility
- VPN for protected communication between trusted endpoints/sites

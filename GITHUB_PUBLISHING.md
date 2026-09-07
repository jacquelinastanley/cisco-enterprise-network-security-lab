# GitHub Publishing Checklist

## Recommended repository name

`cisco-enterprise-network-security-lab`

## Recommended description

> Multi-site Cisco Packet Tracer lab featuring VLAN segmentation, OSPF, HSRP, EtherChannel, STP, WLC, server services, and Layer 2 security hardening.

## Before publishing

- [ ] Add the `.pkt` file to `packet-tracer/`
- [ ] Add a clean topology screenshot to `assets/`
- [ ] Remove university/assignment references from screenshots and Packet Tracer notes
- [ ] Remove names, student IDs, marks, rubrics, and peer-evaluation material
- [ ] Verify all links in the README
- [ ] Run the validation checklist

## Initialize the repository

```bash
git init
git add .
git commit -m "Initial commit: enterprise network resilience and security lab"
git branch -M main
git remote add origin <YOUR_GITHUB_REPOSITORY_URL>
git push -u origin main
```

## Suggested topics

`cisco` `packet-tracer` `networking` `ospf` `vlan` `hsrp` `etherchannel` `stp` `network-security` `cybersecurity` `homelab` `portfolio-project`

# Network Segmentation Principles

## Objective

Reduce lateral movement and minimize attack paths inside the infrastructure.

---

## Current Architecture State

Current lab architecture uses a flat LAN:

```text
192.168.10.0/24
```

In this design:

- endpoints communicate directly at Layer 2,
- traffic does not necessarily traverse the firewall,
- OPNsense cannot fully inspect east-west traffic,
- lateral movement is easier for attackers.

---

## Why Segmentation Matters

A firewall only filters routed traffic.

If two systems are inside the same subnet:

- ARP resolution occurs directly,
- systems communicate peer-to-peer,
- traffic bypasses Layer 3 filtering.

Segmentation forces traffic through controlled inspection points.

---

## Recommended Architecture

Example segmented architecture:

```text
VLAN 10 - USERS      192.168.10.0/24
VLAN 20 - SERVERS    192.168.20.0/24
VLAN 30 - DATABASES  192.168.30.0/24
VLAN 40 - ADMIN      192.168.40.0/24
VLAN 50 - SOC        192.168.50.0/24
```

All inter-VLAN communication should traverse OPNsense.

---

## Security Principles

### Deny by Default

Only explicitly authorized flows should be allowed.

---

### Least Privilege

Systems should communicate only when operationally required.

Examples:

- APP01 -> DB01:5432 allowed
- USER VLAN -> DB VLAN denied
- Kali workstation isolated from production servers

---

### Reduce Attack Surface

Restrict:

- SMB exposure
- RDP exposure
- database ports
- SSH access
- administrative interfaces

---

## Security Benefits

Proper segmentation:

- limits lateral movement,
- slows attackers,
- improves detection visibility,
- isolates compromises,
- simplifies monitoring,
- enforces security boundaries.

---

## SOC Perspective

Segmentation improves:

- firewall telemetry,
- anomaly detection,
- east-west traffic visibility,
- incident containment,
- forensic analysis.

---

## Future Lab Evolution

Planned improvements:

- multiple VMnet segments,
- routed VLAN simulation,
- inter-zone firewall rules,
- east-west traffic monitoring,
- Zero Trust style filtering.

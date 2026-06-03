# Security Architecture Principles

## Objective

This document summarizes core cybersecurity principles applied to enterprise infrastructure design.

Cybersecurity is not based on a single tool.

It is based on:

- reducing attack surface,
- limiting trust relationships,
- controlling access,
- detecting abnormal activity,
- preparing for compromise.

---

# Assume Breach Mindset

A secure architecture assumes that:

```text
A compromise will eventually happen.
```

The objective is therefore to:

- reduce the probability of compromise,
- reduce attacker movement,
- reduce business impact,
- improve visibility,
- accelerate detection and response.

---

# Principle of Least Privilege

Users, systems and applications should only receive:

```text
The minimum permissions necessary.
```

Examples:

- users should not have administrator rights,
- applications should not use database superuser accounts,
- servers should only expose required services,
- network flows should be explicitly authorized.

---

# Network Segmentation

Flat networks increase lateral movement opportunities.

Recommended architecture:

```text
Users VLAN
Servers VLAN
Database VLAN
Administration VLAN
SOC VLAN
```

Traffic between zones should pass through:

- firewalls,
- ACLs,
- monitoring points.

Segmentation limits attacker propagation.

---

# Deny by Default

Security rules should follow:

```text
Default deny.
```

Only explicitly authorized communications should be allowed.

Examples:

- APP01 -> DB01:5432 allowed,
- user workstations -> database denied,
- unrestricted SMB exposure denied.

---

# Identity Security

Identity is one of the primary attack targets.

Critical protections include:

- strong password policies,
- MFA,
- account lockout policies,
- Kerberos hardening,
- privileged account separation,
- privileged access monitoring.

---

# Human Factor

Even hardened infrastructures remain vulnerable to:

- phishing,
- social engineering,
- credential theft,
- malicious attachments,
- user mistakes.

The human factor is frequently the initial compromise vector.

Security awareness is therefore essential.

---

# Logging and Monitoring

Security visibility is critical.

Important telemetry sources include:

- firewall logs,
- endpoint logs,
- Active Directory logs,
- Sysmon events,
- authentication logs,
- application logs,
- database logs.

Logs should be centralized into a SIEM.

---

# Defense in Depth

No single security control is sufficient.

Effective architectures combine:

- segmentation,
- hardening,
- monitoring,
- detection,
- backups,
- access control,
- patch management,
- incident response.

---

# Incident Preparedness

Organizations must prepare for compromise.

Important capabilities include:

- backups,
- recovery procedures,
- incident response playbooks,
- forensic visibility,
- containment strategies,
- business continuity planning.

---

# Security Philosophy

Cybersecurity maturity is not:

```text
Preventing every attack.
```

It is:

```text
Reducing risk, limiting impact, detecting compromise quickly, and recovering efficiently.
```

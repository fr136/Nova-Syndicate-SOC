# Principle of Least Privilege

## Definition

The principle of least privilege states that users, systems and applications should only receive the minimum permissions required to perform their tasks.

---

## Why It Matters

Excessive permissions increase:

- attack surface,
- lateral movement possibilities,
- privilege escalation risks,
- credential abuse impact.

Least privilege reduces the consequences of compromise.

---

## Infrastructure Examples

### Database Access

Bad practice:

```text
Any workstation can reach PostgreSQL directly.
```

Recommended:

```text
Only APP01 should access DB01 on TCP/5432.
```

---

### Administrative Accounts

Bad practice:

```text
Shared administrator accounts.
```

Recommended:

```text
Dedicated admin accounts with restricted usage.
```

---

### Network Access

Bad practice:

```text
Flat LAN with unrestricted communication.
```

Recommended:

```text
Segmented VLANs with deny-by-default firewall rules.
```

---

### Linux Services

Recommended hardening:

- disable root SSH login,
- restrict SSH exposure,
- use SSH keys,
- remove unused services,
- limit sudo permissions.

---

### Active Directory

Recommended hardening:

- separate admin and user accounts,
- apply GPO restrictions,
- enable account lockout policies,
- restrict privileged group membership,
- monitor authentication events.

---

## Security Outcomes

Applying least privilege:

- limits attacker movement,
- reduces blast radius,
- improves monitoring quality,
- simplifies incident response,
- enforces operational discipline.

---

## SOC Perspective

Least privilege improves:

- anomaly detection,
- suspicious access identification,
- alert quality,
- investigation precision.

---

## Lab Evolution Goals

Future improvements planned in this homelab:

- segmented infrastructure,
- restricted database access,
- dedicated administration zones,
- hardened Linux services,
- Active Directory policy hardening.

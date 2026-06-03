# Active Directory Reconnaissance Scenario

## Objective

Simulate internal Active Directory reconnaissance from a compromised workstation and validate detection visibility through Wazuh SIEM.

---

## Scenario Context

| Component | Value |
|---|---|
| Attacker VM | Kali Linux |
| Target | DC01 |
| Domain | nova.local |
| Target IP | 192.168.10.10 |
| Monitoring platform | Wazuh |
| Firewall | OPNsense |

---

## Attack Commands

### Nmap service discovery

```bash
nmap -Pn -sV 192.168.10.10
```

### Active Directory enumeration

```bash
enum4linux 192.168.10.10
```

---

## Observed Services

Detected services included:

- Kerberos
- LDAP
- SMB
- RPC
- DNS
- NetBIOS
- WinRM

Domain discovered:

```text
nova.local
```

---

## Wazuh Detections

Observed detections:

- Active scanning behavior
- Network service discovery
- Authentication activity visibility
- Windows event collection
- Reconnaissance telemetry

Example detection:

| Rule | Description |
|---|---|
| T1595.002 | Active Scanning |

---

## MITRE ATT&CK Mapping

| Technique | Description |
|---|---|
| T1595.002 | Active Scanning |
| T1046 | Network Service Discovery |
| T1018 | Remote System Discovery |
| T1087 | Account Discovery |
| T1078 | Valid Accounts |

---

## Investigation Workflow

1. Detection appears in Wazuh security events.
2. Analyst identifies reconnaissance source IP.
3. Correlation performed with OPNsense firewall logs.
4. Analyst validates targeted services and exposed protocols.
5. Internal reconnaissance behavior classified under MITRE ATT&CK.

---

## Defensive Recommendations

- Segment workstation VLANs from critical infrastructure.
- Restrict LDAP and SMB exposure.
- Enable advanced Sysmon telemetry.
- Detect repeated enumeration activity.
- Harden Active Directory authentication protocols.
- Monitor abnormal scanning frequency.

---

## Lessons Learned

This scenario demonstrates how quickly an attacker can enumerate an Active Directory environment once connected to an internal LAN.

The exercise validates:

- SOC visibility,
- centralized telemetry,
- firewall monitoring,
- AD exposure awareness,
- detection engineering fundamentals.

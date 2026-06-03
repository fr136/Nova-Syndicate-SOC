# SOC Playbook - Active Directory Reconnaissance

## Detection Objective

Detect suspicious internal reconnaissance activity targeting Active Directory services.

---

## Potential Indicators

- Nmap scans
- enum4linux execution
- SMB enumeration
- LDAP enumeration
- Repeated authentication attempts
- Abnormal service discovery activity

---

## Detection Sources

| Source | Description |
|---|---|
| Wazuh | Security events and telemetry |
| Sysmon | Process creation events |
| OPNsense | Firewall logs |
| Windows Event Logs | Authentication activity |

---

## Investigation Steps

1. Identify source IP.
2. Validate targeted assets.
3. Review process execution telemetry.
4. Correlate with firewall activity.
5. Determine whether activity is authorized.
6. Escalate if malicious reconnaissance is confirmed.

---

## Containment Actions

- Isolate offending workstation.
- Block source IP.
- Disable compromised accounts.
- Restrict SMB and LDAP exposure.
- Increase monitoring level.

---

## MITRE ATT&CK Mapping

| Technique | Description |
|---|---|
| T1595.002 | Active Scanning |
| T1046 | Network Service Discovery |
| T1018 | Remote System Discovery |
| T1087 | Account Discovery |

---

## Status

Draft playbook for homelab SOC simulation.

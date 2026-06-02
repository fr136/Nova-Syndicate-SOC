# APP01 Nmap Scan Detection

## Objective

Validate that the Nova Syndicate SOC lab can detect reconnaissance activity against a monitored application server.

## Lab context

| Component | Role | IP |
|---|---|---|
| Kali Linux | Attack simulation host | 192.168.10.60 |
| APP01 | Nginx / Flask application server | 192.168.10.50 |
| WAZUH01 | SIEM / Wazuh manager | 192.168.10.30 |
| OPNsense | Firewall / gateway | 192.168.10.1 |

## Attack simulation

Command executed from Kali Linux:

```bash
nmap -A 192.168.10.50
```

Observed target exposure:

```text
22/tcp open  ssh     OpenSSH 9.2p1 Debian 2+deb12u10
80/tcp open  http    nginx 1.22.1
```

## Detection result

Wazuh generated security events on APP01 after the scan.

Observed alert examples:

```text
Rule ID: 31101
Description: Web server 400 error code.
Level: 5
Agent: APP01
```

```text
Rule ID: 31151
MITRE: T1595.002
Tactic: Reconnaissance
Description: Multiple web server 400 error codes from same source IP.
Level: 10
Agent: APP01
```

## MITRE ATT&CK mapping

| Technique | Name | Tactic |
|---|---|---|
| T1595.002 | Active Scanning | Reconnaissance |

## SOC analysis

The Nmap aggressive scan triggered malformed or uncommon HTTP requests against nginx. These requests generated multiple HTTP 400 responses. Wazuh correlated repeated 400 errors from the same source and raised a higher-severity reconnaissance alert.

This validates:

- agent-based log collection on APP01,
- nginx log ingestion by Wazuh,
- MITRE ATT&CK mapping,
- detection of active scanning behavior,
- initial SOC triage workflow.

## Evidence

Related evidence generated during the lab:

- Wazuh security events screenshot: `screenshots/NMAP - WAZUH.png`
- OPNsense firewall live view screenshot: `screenshots/Liveview OPNSENSE.png`
- Wazuh MITRE ATT&CK PDF report: `reports/wazuh-module-agents-004-mitre-1780395712.pdf`

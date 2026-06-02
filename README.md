# Nova Syndicate SOC

Enterprise SOC / Blue Team homelab built with VMware, Wazuh SIEM, Active Directory, PostgreSQL and Flask applications.

This project simulates the modernization of a multi-site enterprise infrastructure with centralized monitoring, authentication management, database services and security supervision.

---

## Infrastructure Overview

| VM | Role | Operating System | IP Address | Status |
|---|---|---|---|---|
| DC01 | Active Directory / DNS | Windows Server 2022 | 192.168.10.10 | Active |
| FS01 | File Server / Shared folders | Windows Server 2022 | 192.168.10.20 | Active |
| WAZUH01 | SIEM / Monitoring | Debian 12 | 192.168.10.30 | Active |
| DB01 | PostgreSQL Database Server | Debian 12 | 192.168.10.40 | Active |
| APP01 | Flask / Nginx Application Server | Debian 12 | 192.168.10.50 | Active |
| KALI | Offensive security workstation | Kali Linux | 192.168.10.60 | Active |
| OPNsense | Firewall / Gateway | FreeBSD / OPNsense | 192.168.10.1 | Active |

---

## Technologies

- VMware Workstation
- Windows Server 2022
- Debian 12
- Kali Linux
- OPNsense Firewall
- Active Directory
- Wazuh SIEM
- Sysmon
- PostgreSQL
- Python Flask
- Nginx
- RBAC permissions
- Centralized logging
- Linux & Windows monitoring
- MITRE ATT&CK mapping

---

## Implemented Features

### Active Directory

- Domain deployment
- Organizational Units
- User management
- Authentication monitoring
- Shared folders with RBAC permissions

### Wazuh SIEM

- Windows and Linux agents deployment
- Centralized log collection
- Authentication event visibility
- Sysmon integration
- Security event monitoring
- MITRE ATT&CK mapping
- CIS benchmark visibility
- Reconnaissance detection
- Web attack detection
- Agent health monitoring

### Database Infrastructure

- PostgreSQL deployment
- Database initialization
- Remote application connectivity
- SQL service monitoring
- PostgreSQL exposure analysis with Nmap NSE scripts

### Application Server

- Nginx deployment
- Python Flask application
- Application-to-database communication
- Linux monitoring with Wazuh
- Web attack simulation

### Firewall & Network Monitoring

- OPNsense deployment
- Centralized firewall logging
- LAN/WAN segmentation
- Live traffic monitoring
- Syslog forwarding tests
- Firewall event visibility through Wazuh

---

## Offensive Security Simulations

Current attack simulations performed from Kali Linux:

```bash
nmap -A 192.168.10.50
nmap -sV --script vuln 192.168.10.40
nikto -h http://192.168.10.50
```

Detected behaviors:

- Active scanning
- Web reconnaissance
- HTTP 400 error bursts
- XSS attempts
- SQL injection attempts
- Shellshock attempts
- Suspicious URL access
- Vulnerability scanning

---

## Security Monitoring

Current detection capabilities:

- Failed Windows logons
- Successful Windows authentication events
- Sysmon process creation events
- Linux server registration monitoring
- Multi-agent monitoring through Wazuh
- Security event centralization
- Nmap reconnaissance detection
- Web attack correlation
- MITRE ATT&CK classification

Observed MITRE ATT&CK mapping:

| Technique | Description |
|---|---|
| T1595.002 | Active Scanning |

---

## Repository Structure

```text
Nova-Syndicate-SOC/
|
|-- README.md
|-- architecture/
|-- docs/
|-- docs/attack-scenarios/
|-- wazuh/
|-- active-directory/
|-- db01-postgresql/
|-- app01-flask/
|-- scripts/
|-- screenshots/
|-- reports/
```

---

## Screenshots Included

- Wazuh security events
- MITRE ATT&CK detections
- OPNsense live firewall logs
- Nmap reconnaissance scans
- Wazuh agents status
- PostgreSQL exposure analysis
- Flask application deployment
- Active Directory structure

---

## Reports & Evidence

Included evidence:

- Wazuh MITRE ATT&CK report
- Reconnaissance detection screenshots
- Firewall live monitoring screenshots
- Nmap scan outputs
- Web attack detections

The exported Wazuh report contains:

- reconnaissance detections,
- privilege escalation alerts,
- defense evasion detections,
- discovery activity,
- vulnerability scanning telemetry,
- SQL injection attempts,
- XSS attempts,
- Shellshock detections.

---

## Next Steps

- Full Flask ↔ PostgreSQL integration
- SSH brute-force detection scenarios
- Sigma rules integration
- Custom Wazuh detection rules
- SOC playbooks documentation
- Network segmentation hardening
- Active Directory attack simulations
- Sysmon advanced telemetry
- Threat hunting dashboards

---

## Documentation

The repository includes technical documentation covering:

- Enterprise SOC architecture
- VMware virtual networking
- Wazuh deployment
- OPNsense firewall configuration
- MITRE ATT&CK mapping
- Centralized monitoring strategy
- Incident simulation scenarios
- Attack detection workflows

---

## Author

Franck Rouane  
Junior Cybersecurity Analyst | SOC | Blue Team | Infrastructure Security
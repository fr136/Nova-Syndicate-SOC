# Nova Syndicate SOC

Enterprise SOC / Blue Team homelab built with VMware, Wazuh SIEM, Active Directory, PostgreSQL and Flask applications.

This project simulates the modernization of a multi-site enterprise infrastructure with centralized monitoring, authentication management, database services and security supervision.

---

## Infrastructure Overview

| VM | Role | Operating System | IP Address | Status |
|---|---|---|---|---|
| DC01 | Active Directory / DNS | Windows Server 2022 | 192.168.2.10 | Active |
| FS01 | File Server / Shared folders | Windows Server 2022 | 192.168.2.20 | Active |
| WAZUH01 | SIEM / Monitoring | Debian 12 | 192.168.2.30 | Active |
| DB01 | PostgreSQL Database Server | Debian 12 | 192.168.2.40 | Active |
| APP01 | Flask / Nginx Application Server | Debian 12 | 192.168.2.50 | Active |

---

## Technologies

- VMware Workstation
- Windows Server 2022
- Debian 12
- Active Directory
- Wazuh SIEM
- Sysmon
- PostgreSQL
- Python Flask
- Nginx
- RBAC permissions
- Centralized logging
- Linux & Windows monitoring

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

### Database Infrastructure

- PostgreSQL deployment
- Database initialization
- Remote application connectivity
- SQL service monitoring

### Application Server

- Nginx deployment
- Python Flask application
- Application-to-database communication
- Linux monitoring with Wazuh

---

## Security Monitoring

Current detection capabilities:

- Failed Windows logons
- Successful Windows authentication events
- Sysmon process creation events
- Linux server registration monitoring
- Multi-agent monitoring through Wazuh
- Security event centralization

---

## Repository Structure

```text
Nova-Syndicate-SOC/
|
|-- README.md
|-- architecture/
|-- docs/
|-- wazuh/
|-- active-directory/
|-- db01-postgresql/
|-- app01-flask/
|-- scripts/
|-- screenshots/
```

---

## Screenshots Included

- Active Directory OU structure
- Wazuh dashboard
- Wazuh agents status
- Flask application deployment
- PostgreSQL database creation
- Database connectivity tests
- Windows monitoring events
- File server permissions

---

## Next Steps

- Full Flask ↔ PostgreSQL integration
- Incident simulation scenarios
- Kali Linux attack simulations
- Detection rules improvement
- Backup procedures
- Sigma rules integration
- Network segmentation expansion
- SOC playbooks documentation

---

## Documentation

The repository includes a full technical architecture document describing:

- Enterprise context and constraints
- Infrastructure modernization strategy
- VLAN segmentation
- Virtualization architecture
- Security monitoring strategy
- PRA / PCA objectives
- Wazuh supervision architecture

---

## Author

Franck Rouane  
Junior Cybersecurity Analyst | SOC | Blue Team | Infrastructure Security

# Network Architecture Diagram

## Logical topology

```mermaid
flowchart LR
    Internet((Internet))
    VMwareNAT[VMware NAT / VMnet8\n192.168.2.0/24]

    subgraph FW[OPNsense Firewall]
        WAN[WAN em0\n192.168.2.138/24]
        LAN[LAN em1\n192.168.10.1/24]
    end

    subgraph LANSEG[Internal SOC LAN / VMnet2\n192.168.10.0/24]
        DC01[DC01\nWindows Server 2022\nAD / DNS\n192.168.10.10]
        FS01[FS01\nWindows Server 2022\nFile Server\n192.168.10.20]
        WAZUH[WAZUH01\nDebian 12\nWazuh Manager / Indexer / Dashboard\n192.168.10.30]
        DB01[DB01\nDebian 12\nPostgreSQL\n192.168.10.40]
        APP01[APP01\nDebian 12\nNginx / Flask\n192.168.10.50]
        KALI[KALI\nOffensive workstation\n192.168.10.60]
    end

    Internet --- VMwareNAT --- WAN
    WAN --- LAN
    LAN --- DC01
    LAN --- FS01
    LAN --- WAZUH
    LAN --- DB01
    LAN --- APP01
    LAN --- KALI

    APP01 -- Wazuh agent telemetry --> WAZUH
    DB01 -- Wazuh agent telemetry --> WAZUH
    DC01 -- Wazuh agent + Windows logs --> WAZUH
    FS01 -- Wazuh agent + Windows logs --> WAZUH
    KALI -- Nmap / enum4linux / Nikto simulations --> APP01
    KALI -- AD reconnaissance simulations --> DC01
```

## IP plan

| Host | Role | IP |
|---|---|---|
| OPNsense LAN | Firewall gateway | 192.168.10.1 |
| DC01 | Active Directory / DNS | 192.168.10.10 |
| FS01 | File server | 192.168.10.20 |
| WAZUH01 | SIEM | 192.168.10.30 |
| DB01 | PostgreSQL | 192.168.10.40 |
| APP01 | Nginx / Flask | 192.168.10.50 |
| KALI | Offensive workstation | 192.168.10.60 |

## Security logic

- OPNsense provides the LAN gateway and outbound NAT.
- Wazuh collects endpoint telemetry from Linux and Windows agents.
- Kali is used only as an internal lab attacker.
- APP01 and DB01 simulate exposed internal Linux services.
- DC01 simulates a Windows enterprise identity backbone.
- The lab validates offensive activity detection through Wazuh and MITRE ATT&CK mapping.

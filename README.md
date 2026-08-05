# Centralized Security and Infrastructure Monitoring with Wazuh and Zabbix

A centralized monitoring project combining security event detection, system integrity monitoring, infrastructure availability, and performance supervision in a Proxmox-based virtualized environment.

## Overview
This project was completed during a cybersecurity internship and focused on improving visibility across a virtualized infrastructure.

The solution combined Wazuh for security monitoring with Zabbix for availability and performance monitoring. It covered Proxmox hosts, Linux systems, selected network equipment, and centralized dashboards for security and operational analysis.

All information published in this repository is sanitized. Internal addresses, credentials, hostnames, organization-specific data, and confidential configurations are excluded or replaced with generic values.

## Objectives
The main objectives were to:

- Centralize security and infrastructure monitoring
- Monitor Proxmox hosts and their critical services
- Detect unauthorized or unexpected file modifications
- Monitor system availability, disk usage, and resource consumption
- Collect security and operational events in centralized dashboards
- Monitor a FortiGate firewall through restricted read-only SNMP access
- Reduce false positives and improve alert relevance
- Validate monitoring through controlled test scenarios

## Architecture

The monitoring environment included:

- Wazuh Manager, Indexer, and Dashboard
- Zabbix Server and Web Interface
- Proxmox VE hosts
- Linux and Windows workloads
- FortiGate firewall monitoring through SNMP
- Wazuh and Zabbix agents
- Centralized dashboards and alerting mechanisms

A sanitized architecture diagram will be added to this section.

## Technologies
| Area | Technologies |
|---|---|
| Security monitoring | Wazuh, File Integrity Monitoring, custom rules, MITRE ATT&CK |
| Infrastructure monitoring | Zabbix, agent-based monitoring, SNMP, triggers |
| Virtualization | Proxmox VE |
| Network monitoring | FortiGate, SNMPv2c, ICMP |
| Operating systems | Linux, Windows Server |
| Administration | Bash, PowerShell, SSH |
| Visualization | Wazuh Dashboard, Zabbix Dashboard |

## Implementation

### Wazuh security monitoring

Wazuh agents were used to collect system events and monitor security-relevant activity on the Proxmox hosts.

The implementation included:

- Linux log collection
- File Integrity Monitoring
- Monitoring of Proxmox configuration paths
- Custom detection and correlation rules
- Saved searches for security investigation
- Dashboard creation
- Alert validation
- Noise reduction through targeted exclusions

### Zabbix infrastructure monitoring

Zabbix was used to monitor infrastructure health, availability, and performance.

The implementation included:

- Proxmox host onboarding
- Agent availability monitoring
- CPU, memory, swap, and disk monitoring
- Static disk-usage thresholds
- Disk-capacity forecasting
- ICMP availability checks
- Trigger replication across monitored hosts
- Dashboard and alert configuration

### FortiGate monitoring

The FortiGate firewall was monitored using read-only SNMP access restricted to the Zabbix server.

The monitoring scope included:

- Device availability
- Interface status
- Interface traffic
- Resource utilization
- SNMP communication validation

## Detection and Monitoring Examples

Examples developed or validated during the project include:

- Changes to monitored Proxmox configuration files
- Repeated security events within a defined time window
- Wazuh agent disconnection
- Proxmox host unavailability
- High disk utilization
- Forecasted disk-capacity exhaustion
- FortiGate availability and interface monitoring

## Validation

| Test scenario | Expected result |
|---|---|
| Stop a monitored agent | An availability or agent-disconnection alert is generated |
| Modify a monitored test file | A File Integrity Monitoring alert is generated |
| Reach a disk-usage threshold | The corresponding Zabbix trigger changes state |
| Simulate repeated matching events | A correlated Wazuh alert is generated |
| Interrupt ICMP availability | The host-unavailable trigger is activated |
| Query the FortiGate through SNMP | Authorized monitoring data is returned |

Only controlled and non-destructive validation methods were used.

## Project Structure

```text
wazuh-zabbix-proxmox-monitoring/
├── README.md
├── architecture/
├── documentation/
├── wazuh/
│   ├── configurations/
│   ├── rules/
│   └── queries/
├── zabbix/
│   ├── triggers/
│   └── templates/
├── screenshots/
└── validation/

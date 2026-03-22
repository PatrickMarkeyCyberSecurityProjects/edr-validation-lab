# Environment

## Overview
This lab simulates a small enterprise-style blue-team environment with centralized monitoring and cross-platform endpoints.

---

## Virtualization Platform
- Oracle VirtualBox

---

## Network Design
### Adapter Model
- **Adapter 1: NAT**
  - used for internet access
  - package downloads and updates
- **Adapter 2: Host-Only Adapter**
  - used for isolated lab communication
  - subnet: `192.168.56.0/24`

### Host-Only Host Adapter
- Adapter: VirtualBox Host-Only Ethernet Adapter
- Host IP: `192.168.56.1`
- Subnet Mask: `255.255.255.0`

---

## Lab Systems

### Wazuh Server
- Hostname: `wazuh-server`
- OS: Ubuntu Server 22.04
- Role: SIEM / centralized monitoring
- Base Memory: 8192 MB
- CPU: 4
- Disk: 80 GB
- Adapter 1: NAT
- Adapter 2: Host-Only
- NAT IP: `10.0.2.15`
- Host-Only IP: `192.168.56.103`

### Windows Endpoint
- Hostname: `Win10-Endpoint`
- OS: Windows 10 Home 10.0.19045.3803
- Role: monitored endpoint
- Base Memory: 6144 MB
- CPU: 2
- Disk: 60 GB
- Adapter 1: NAT
- Adapter 2: Host-Only
- NAT IP: `10.0.2.15`
- Host-Only IP: `192.168.56.101`

### Linux Endpoint
- Hostname: `linux-endpoint`
- OS: Ubuntu Server 22.04
- Role: monitored Linux endpoint
- Base Memory: 4096 MB
- CPU: 2
- Disk: 30 GB
- Adapter 1: NAT
- Adapter 2: Host-Only
- NAT IP: `10.0.2.15`
- Host-Only IP: `192.168.56.102`

---

## Monitoring / Telemetry Status

### Wazuh Server
- Wazuh install method: all-in-one quickstart installer
- Dashboard status: operational
- Manager status: installed
- Indexer status: installed
- Dashboard access: successful from host browser

### Windows Endpoint
- Wazuh Agent: installed and active
- Agent status: active in Wazuh
- Sysmon: installed
- Sysmon config in agent XML: added
- Telemetry in Wazuh: active
- Event review in Threat Hunting: working

### Linux Endpoint
- Endpoint deployed and networked
- Host-only connectivity established
- Wazuh agent onboarding: pending / next step

---

## Phase Status
### Completed
- Phase 1 — planning, repo setup, architecture, documentation
- Phase 2 — VM build, networking, validation
- Phase 3 — Wazuh deployment, dashboard recovery, Windows agent onboarding
- Phase 4 — Sysmon installation and Windows event visibility validation

### In Progress
- Sysmon-specific log validation and higher-value event filtering
- Linux agent onboarding
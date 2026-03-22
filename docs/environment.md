
---

# 🧾 3. `docs/environment.md` (UPDATED WITH REAL IPs)

```md
# Environment

## Overview
This lab simulates a small enterprise environment with centralized monitoring and multiple endpoints.

---

## Network Configuration
- NAT → Internet access
- Host-Only → Internal communication
- Range: 192.168.56.0/24

---

## Systems

### Wazuh Server
- Hostname: wazuh-server
- OS: Ubuntu Server 22.04
- Role: Monitoring / SIEM
- NAT IP: 10.0.2.15
- Host-Only IP: 192.168.56.103

---

### Windows Endpoint
- Hostname: WIN-ENDPOINT
- OS: Windows 10
- Role: Monitored endpoint
- NAT IP: 10.0.2.15
- Host-Only IP: 192.168.56.101

---

### Linux Endpoint
- Hostname: linux-endpoint
- OS: Ubuntu Server 22.04
- Role: Monitored endpoint
- NAT IP: 10.0.2.15
- Host-Only IP: 192.168.56.102

---

## Validation
- All systems communicate via Host-Only network
- Internet access verified via NAT
- Lab ready for telemetry ingestion

---

## Status
✅ Phase 2 Complete
# Environment

## Overview
This lab simulates a small enterprise-style environment with a central monitoring server and multiple endpoints across different operating systems. It is designed to support endpoint detection, investigation workflows, and detection validation.

---

## Host System

- Host OS: Windows (update if different)
- CPU:
- RAM:
- Available Disk Space:

---

## Virtualization Platform

- Platform: Oracle VirtualBox
- Network Configuration:
  - NAT (for internet access and updates)
  - Host-Only Network (for internal lab communication)

---

## Network Design

### Host-Only Network
- Network Range: 192.168.56.0/24
- Host IP: 192.168.56.1
- DHCP: Enabled

### Network Purpose
- NAT Adapter:
  - Used for internet access (updates, downloads, package installs)
- Host-Only Adapter:
  - Used for communication between lab systems
  - Isolated from external network traffic

---

## Lab Systems

### 1. Wazuh Server

- Hostname: wazuh-server
- Role: Central monitoring and detection platform
- OS: Ubuntu Server 22.04
- vCPU: 4
- RAM: 8 GB
- Disk: 80 GB

#### Network Configuration
- Adapter 1: NAT
- Adapter 2: Host-Only

#### IP Addresses
- NAT IP:
- Host-Only IP:

---

### 2. Windows Endpoint

- Hostname: WIN-ENDPOINT
- Role: Primary monitored endpoint (Windows)
- OS: Windows 10/11
- vCPU: 2
- RAM: 4–6 GB
- Disk: 60 GB

#### Network Configuration
- Adapter 1: NAT
- Adapter 2: Host-Only

#### IP Addresses
- NAT IP:
- Host-Only IP:

---

### 3. Linux Endpoint

- Hostname: linux-endpoint
- Role: Secondary monitored endpoint (Linux)
- OS: Ubuntu Server 22.04
- vCPU: 2
- RAM: 2–4 GB
- Disk: 30–40 GB

#### Network Configuration
- Adapter 1: NAT
- Adapter 2: Host-Only

#### IP Addresses
- NAT IP:
- Host-Only IP:

---

## Communication Model

- All endpoints send telemetry to the Wazuh server
- Internal communication occurs over the Host-Only network
- Internet access (updates, downloads) occurs over NAT
- Systems are isolated from the host network except where required

---

## Phase 2 Validation Checklist

- [ ] All VMs created and powered on
- [ ] All systems have internet access via NAT
- [ ] All systems have Host-Only IP addresses
- [ ] Wazuh server can ping Windows endpoint
- [ ] Wazuh server can ping Linux endpoint
- [ ] Windows endpoint can ping Wazuh server
- [ ] Linux endpoint can ping Wazuh server
- [ ] IP addresses documented above

---

## Notes

- Dual-network configuration (NAT + Host-Only) enables safe lab isolation while maintaining update capability
- Host-Only network is critical for detection, monitoring, and controlled communication
- This architecture will support endpoint telemetry ingestion and detection validation in later phases
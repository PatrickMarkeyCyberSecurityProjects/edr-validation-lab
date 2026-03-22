# Detection Validation & Endpoint Investigation Lab

## Overview
This project is a blue-team cybersecurity lab designed to simulate a realistic endpoint monitoring and investigation environment using:

- a centralized Wazuh SIEM server
- a Windows 10 endpoint
- a Linux endpoint
- VirtualBox networking with NAT and Host-Only adapters
- Sysmon for enhanced Windows telemetry
- analyst-style documentation, troubleshooting notes, and screenshots

The goal of the project is to build recruiter-visible proof of practical skills relevant to:

- SOC Analyst
- Security Analyst
- Cybersecurity Analyst
- Junior Security Engineer
- Detection / Security Operations roles

---

## Project Goals
- Build a multi-system blue-team lab from scratch
- Deploy and validate a working Wazuh SIEM environment
- Onboard and monitor a Windows endpoint
- Install and validate Sysmon for enhanced Windows telemetry
- Troubleshoot real-world networking, authentication, and telemetry issues
- Document setup, fixes, evidence, and outcomes in a recruiter-friendly way

---

## Lab Architecture
![Lab Architecture](architecture/diagrams/04_architecture_diagram_v1.png)

Initial architecture design showing endpoint, server, and network segmentation using NAT and host-only adapters.
The lab currently includes:

- **Wazuh Server** — Ubuntu Server 22.04
- **Windows Endpoint** — Windows 10
- **Linux Endpoint** — Ubuntu Server 22.04

### Network Design
- **Adapter 1: NAT** → internet access, package downloads, updates
- **Adapter 2: Host-Only** → internal lab communication on `192.168.56.0/24`

### Final Host-Only IP Plan
- **Wazuh Server** → `192.168.56.103`
- **Windows Endpoint** → `192.168.56.101`
- **Linux Endpoint** → `192.168.56.102`

---

## Current Status
### Completed
- GitHub repository and project structure created
- VirtualBox lab environment built
- NAT + Host-Only networking configured and validated
- Wazuh all-in-one deployment completed
- Wazuh dashboard access restored and validated
- Windows endpoint agent onboarded and active
- Sysmon downloaded and installed on Windows
- Windows endpoint activity generated and visible in Wazuh
- Threat Hunting workflow validated
- Sysmon-specific filter created in Wazuh

### In Progress
- Confirming deeper Sysmon-specific event visibility
- Linux endpoint Wazuh onboarding
- Detection validation scenarios

### Planned Next
- Linux agent onboarding
- Process creation and suspicious command detection
- Detection logic and investigation workflow documentation
- Incident-style writeups and screenshots

---

## Repository Structure
- `docs/` → project scope, architecture, environment, plans
- `notes/` → build journal and analyst notes
- `configs/` → tooling and configuration notes
- `screenshots/` → screenshot evidence and log
- `detections/` → planned detections and tracking
- `investigations/` → future investigation notes
- `scenarios/` → future simulated attack scenarios

---

## Key Skills Demonstrated So Far
- VirtualBox multi-VM lab design
- NAT vs Host-Only network segmentation
- Linux troubleshooting
- Windows troubleshooting
- Wazuh deployment and recovery
- Wazuh dashboard authentication recovery
- Endpoint onboarding
- Sysmon installation
- Telemetry validation
- SIEM navigation and event filtering
- Project documentation discipline

---

## Notable Troubleshooting Completed
- Fixed incorrect Git remote configuration
- Fixed VirtualBox adapter locking due to running state
- Restored missing Host-Only adapters in VirtualBox
- Brought Linux interfaces up manually
- Standardized static Host-Only addressing
- Recovered Wazuh dashboard access after service and credential issues
- Reset Wazuh admin credentials successfully
- Fixed Sysmon installation path issues
- Added Sysmon event channel collection to the Windows Wazuh agent config

---

## Screenshots / Evidence
See `screenshots/screenshot-log.md` for a running log of setup proof, troubleshooting, and milestone screenshots.

---

## Why This Project Matters
This project is structured to demonstrate not just “lab completion,” but the practical workflow of:

- building security infrastructure
- onboarding telemetry sources
- validating logging pipelines
- identifying and fixing broken components
- documenting changes like a real analyst / engineer


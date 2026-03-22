# Architecture Notes

## Lab Design
This project uses a centralized Wazuh deployment with multiple monitored endpoints to simulate a practical blue-team monitoring environment.

### Core Systems
- Wazuh Server
- Windows Endpoint
- Linux Endpoint

---

## Network Model
### NAT
Used for:
- internet access
- package downloads
- updates
- Wazuh and Sysmon downloads

### Host-Only
Used for:
- communication between the host and VMs
- communication between Wazuh and endpoints
- isolated lab traffic

### Static Host-Only IP Plan
- Wazuh Server → `192.168.56.103`
- Windows Endpoint → `192.168.56.101`
- Linux Endpoint → `192.168.56.102`

---

## Wazuh Deployment Notes
Wazuh was installed using the all-in-one installation approach to deploy:
- Wazuh dashboard
- Wazuh manager
- Wazuh indexer

The environment required multiple troubleshooting steps before dashboard access worked consistently.

---

## Major Troubleshooting Performed

### 1. Git / Repository Issue
- Incorrect remote URL was configured initially
- Resolved by updating Git origin and pushing properly

### 2. VirtualBox Adapter Lock Issue
- Network settings could not be changed while VMs were running
- Resolved by fully powering off VMs before reconfiguration

### 3. Host-Only Adapter Reset / Missing
- VMs temporarily lost Adapter 2
- Re-added Host-Only adapter to all VMs

### 4. Linux Interface State Issues
- Host-Only interfaces were present but in a DOWN state
- Brought interfaces up manually and verified addressing

### 5. Dashboard Not Reachable
- Browser initially returned `ERR_CONNECTION_REFUSED`
- Confirmed service state, port 443 listening, and host connectivity
- Final issue traced to missing / inconsistent configuration and host-only adapter state

### 6. Wazuh Dashboard Credentials
- Installation-generated credentials were not captured at first
- Passwords were regenerated using the Wazuh password tool
- Successful login achieved afterward

### 7. Sysmon Visibility Issue
- Sysmon installed locally, but relevant event visibility in Wazuh required explicit event channel ingestion configuration
- Added the Sysmon Event Channel block to `ossec.conf`

---

## Telemetry Flow
### Windows Endpoint
- Wazuh Agent installed and active
- Sysmon installed on endpoint
- Sysmon event channel added to Wazuh agent config
- Events visible in Threat Hunting

### Linux Endpoint
- Deployed and reachable
- Planned next: Wazuh agent onboarding and telemetry validation

---

## Analyst / Engineer Value
This architecture demonstrates:
- virtualization and network segmentation
- SIEM deployment
- endpoint onboarding
- authentication recovery
- telemetry troubleshooting
- event visibility validation
- project documentation discipline

---

# 2. Replace `notes/build-journal.md` with this

```md
# Build Journal

This journal tracks the lab build from setup through telemetry validation, including issues, fixes, and outcomes.

---

## Entry 1 — Phase 1 Project Setup

### Objective
Set up the project structure, GitHub repository, and documentation framework.

### Completed
- Created project folder structure
- Added documentation files
- Initialized Git repository
- Connected local repo to GitHub
- Created architecture notes and screenshot log

### Issues
- Incorrect Git remote URL
- Push attempted before initial commit existed

### Resolution
- Corrected remote URL
- Created first commit
- Successfully pushed repo

### Outcome
Project repository successfully created and structured.

---

## Entry 2 — VirtualBox Adapter Lock Issue

### Issue
Unable to configure Adapter 2 while VMs were active.

### Root Cause
VirtualBox locks adapter settings when a VM is running or saved.

### Resolution
Powered off VMs fully and re-opened settings.

### Outcome
Restored ability to configure NAT + Host-Only networking.

---

## Entry 3 — Windows Network Validation

### Objective
Validate Windows endpoint networking.

### Result
- NAT IP: `10.0.2.15`
- Host-Only IP: `192.168.56.101`

### Outcome
Windows endpoint correctly configured for internet access and internal lab communication.

---

## Entry 4 — Wazuh Host-Only Interface Fix

### Issue
Wazuh server host-only interface existed but was down.

### Resolution
Brought the interface up manually and verified addressing.

### Outcome
Host-only communication restored on Wazuh server.

---

## Entry 5 — Linux Endpoint Deployment

### Objective
Add Linux endpoint to the lab.

### Result
- Linux endpoint deployed
- NAT IP validated
- Host-Only IP validated as `192.168.56.102`

### Outcome
Linux endpoint added successfully and reachable.

---

## Entry 6 — Windows Firewall ICMP Issue

### Issue
Wazuh server could not ping the Windows endpoint.

### Root Cause
Windows firewall blocked ICMP by default.

### Resolution
Allowed ICMP traffic on Windows.

### Outcome
Internal connectivity validated.

---

## Entry 7 — Full Network Validation

### Objective
Confirm end-to-end lab connectivity.

### Final Host-Only IP Plan
- Wazuh Server: `192.168.56.103`
- Windows Endpoint: `192.168.56.101`
- Linux Endpoint: `192.168.56.102`

### Outcome
All systems successfully communicate over the host-only subnet.

---

## Entry 8 — Wazuh Services Not Found

### Issue
Attempted to access Wazuh dashboard, but services were not found on the server.

### Root Cause
Wazuh stack had not yet been installed.

### Outcome
Confirmed that a full Wazuh installation was required.

---

## Entry 9 — Wazuh All-in-One Installation

### Objective
Deploy the Wazuh stack.

### Actions
- Downloaded Wazuh installer with curl
- Executed all-in-one installation command

### Installed
- Wazuh Dashboard
- Wazuh Manager
- Wazuh Indexer

### Outcome
Wazuh platform installed successfully.

---

## Entry 10 — Dashboard Access Troubleshooting

### Issue
Dashboard was not reachable from the host browser.

### Troubleshooting
- Checked service status
- Verified port 443 listening
- Verified host-only connectivity
- Rechecked Host-Only adapter state on host and guest systems

### Outcome
Confirmed service/network dependencies required for dashboard access.

---

## Entry 11 — Wazuh Admin Credential Recovery

### Issue
Reached login page but could not log in due to incorrect or unknown admin credentials.

### Resolution
Used Wazuh password tool to reset credentials.

### Outcome
Recovered working admin credentials.

---

## Entry 12 — Successful Wazuh Dashboard Login

### Objective
Validate full access to the SIEM from the host machine.

### Outcome
Successfully logged into the Wazuh dashboard.

### Lesson Learned
Dashboard access depends on correct service state, host-only connectivity, and synchronized credentials.

---

## Entry 13 — Windows Wazuh Agent Download and Install

### Objective
Onboard the Windows endpoint into Wazuh.

### Actions
- Downloaded Windows Wazuh agent
- Used Wazuh server IP during setup
- Installed and configured the agent

### Outcome
Windows endpoint connected to Wazuh successfully.

---

## Entry 14 — Windows Agent Service Validation

### Objective
Confirm the endpoint agent is healthy.

### Validation
Checked Windows Services console and verified the Wazuh Windows Agent was running.

### Outcome
Agent service confirmed healthy and active.

---

## Entry 15 — Windows Endpoint Active in Wazuh

### Objective
Confirm the endpoint appears centrally in Wazuh.

### Result
Windows endpoint appeared as active in the Wazuh dashboard.

### Outcome
First endpoint successfully onboarded into the SIEM.

---

## Entry 16 — Sysmon Download

### Objective
Add richer Windows telemetry to the lab.

### Actions
- Downloaded Sysmon from Microsoft Sysinternals
- Staged files in `C:\Tools\Sysmon`

### Outcome
Sysmon binaries prepared for installation.

---

## Entry 17 — Sysmon Installation Path Issue

### Issue
Initial Sysmon install attempts failed.

### Root Cause
PowerShell was running from the wrong directory and the executable path was not correct.

### Resolution
Ran Sysmon from `C:\Tools\Sysmon` using the proper executable path.

### Outcome
Installation path issue resolved.

---

## Entry 18 — Sysmon Installed Successfully

### Objective
Enable enhanced Windows telemetry.

### Actions
Installed Sysmon successfully from PowerShell.

### Outcome
Sysmon installed on the Windows endpoint.

---

## Entry 19 — Generated Windows Activity for Validation

### Objective
Create fresh telemetry to verify visibility in Wazuh.

### Actions
Ran:
- `ipconfig`
- `mkdir C:\Temp\LabTest`
- `notepad`

### Outcome
Generated activity for event validation.

---

## Entry 20 — Initial Event Visibility in Wazuh

### Objective
Validate event ingestion from the Windows endpoint.

### Result
Windows events became visible in Threat Hunting, but most were generic / vulnerability-related rather than the richer endpoint activity desired.

### Outcome
Confirmed end-to-end event flow exists.

---

## Entry 21 — Added Sysmon Event Channel Collection to Wazuh Agent

### Objective
Improve Sysmon-related visibility in Wazuh.

### Actions
Updated `ossec.conf` with:

```xml
<localfile>
  <location>Microsoft-Windows-Sysmon/Operational</location>
  <log_format>eventchannel</log_format>
</localfile>


## Entry 22 — Threat Hunting Navigation and Filter Setup

### Issue
Initially had trouble reviewing the right logs because I was in summary-style dashboard views instead of the raw event workflow.

### Resolution
Switched into the **Events** view inside Wazuh Threat Hunting and created a provider-based filter to isolate Sysmon-related logs.

### Filter Used
- Field: `data.win.system.providerName`
- Operator: `is`
- Value: `Microsoft-Windows-Sysmon`

### Outcome
Established the correct event-review workflow for isolating higher-value endpoint telemetry instead of relying only on overview dashboards.

### Lesson Learned
In SIEM workflows, the difference between overview dashboards and raw event views is critical for investigations and detection validation.


## Entry 23 — Current State Before Break

### Working
- Wazuh server deployed and accessible
- Wazuh dashboard login successful
- Windows endpoint active in Wazuh
- Windows agent service validated
- Sysmon downloaded and installed
- Windows activity generated
- Events visible in Threat Hunting
- Sysmon event channel block added to `ossec.conf`
- All three VMs running and networked

### Pending
- Confirm local Sysmon logs in Event Viewer
- Confirm Sysmon-specific events visible in Wazuh
- Onboard Linux endpoint into Wazuh
- Start process-creation detection validation
- Build first detection use case

### Outcome
The lab has moved beyond basic infrastructure and now has a functioning SIEM, one active monitored Windows endpoint, installed Sysmon, live event visibility, and a documented workflow for continuing into detection engineering.

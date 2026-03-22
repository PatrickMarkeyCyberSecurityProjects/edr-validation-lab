# Build Journal

This journal tracks each phase of the lab build, including setup work, issues encountered, fixes applied, and validation steps.

---

## Entry 1 — Phase 1 Project Setup

### Objective
Set up project structure and GitHub repository

### Completed
- Created structured repo with folders and documentation
- Initialized Git and connected to GitHub
- Created architecture diagram
- Set up screenshot tracking

### Issues
- Incorrect Git remote URL
- Push failed initially

### Fix
- Updated remote using `git remote set-url`
- Created initial commit before pushing

### Outcome
Repository successfully created and structured

---

## Entry 2 — VirtualBox Adapter Lock Issue

### Issue
Unable to configure Adapter 2

### Root Cause
VM was running / saved state

### Fix
- Powered off VM completely
- Reconfigured network adapters

### Outcome
Enabled:
- NAT (Adapter 1)
- Host-Only (Adapter 2)

---

## Entry 3 — Windows Network Validation

### Result
- NAT IP: 10.0.2.15
- Host-Only IP: 192.168.56.101

### Outcome
Windows endpoint correctly configured

---

## Entry 4 — Wazuh Host-Only Interface Issue

### Issue
Interface `enp0s8` was DOWN

### Fix
```bash
sudo ip link set enp0s8 up
sudo dhclient enp0s8

---

## Entry 5 — Linux Endpoint Deployment

### Result
- NAT IP: 10.0.2.15
- Host-Only IP: 192.168.56.102

### Outcome
Linux endpoint successfully added

---

## Entry 6 — Windows Firewall Blocking ICMP

### Issue
Ping to Windows failed

### Root Cause
Windows firewall blocks ICMP

### Fix
netsh advfirewall firewall add rule name="Allow ICMPv4-In" protocol=icmpv4 dir=in action=allow

### Outcome
Ping successful

---

## Entry 7 — Full Network Validation

### Systems 
Wazuh: 192.168.56.103
Windows: 192.168.56.101
Linux: 192.168.56.102

### Result
All systems communicate successfully

### Status
✅ Phase 2 Complete
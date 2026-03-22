# Architecture Notes

## Lab Design
- Wazuh Server (central monitoring)
- Windows Endpoint
- Linux Endpoint

---

## Network
- NAT → external access
- Host-Only → internal communication

---

## Issues and Fixes

### VirtualBox Adapter Lock
- Cause: VM running
- Fix: Power off VM

---

### Linux Interface Down
- Cause: Interface not activated
- Fix:
  - ip link set enp0s8 up
  - dhclient enp0s8

---

### Windows ICMP Blocked
- Cause: Firewall
- Fix:
netsh advfirewall firewall add rule name="Allow ICMPv4-In" protocol=icmpv4 dir=in action=allow

---

## Outcome
Fully functional multi-system lab with validated networking
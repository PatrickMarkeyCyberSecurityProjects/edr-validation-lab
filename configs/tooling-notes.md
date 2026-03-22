# Tooling Notes

## Virtualization
- Oracle VirtualBox

## Operating Systems
- Ubuntu Server 22.04
- Windows 10

## Core Security Platform
- Wazuh v4.14.4
- all-in-one Wazuh deployment

## Endpoint Monitoring
### Windows
- Wazuh Windows Agent installed
- Sysmon v15.15 installed

### Linux
- Ubuntu endpoint deployed
- Wazuh agent onboarding pending

---

## Network
- NAT + Host-Only dual-adapter model
- Host-only subnet: `192.168.56.0/24`
- Static host-only IPs standardized

---

## Sysmon Notes
- Sysmon downloaded from Microsoft Sysinternals
- Installed from `C:\Tools\Sysmon`
- Initial installation issue caused by running command from wrong directory
- Default install completed successfully
- Wazuh agent config updated with:

```xml
<localfile>
  <location>Microsoft-Windows-Sysmon/Operational</location>
  <log_format>eventchannel</log_format>
</localfile>
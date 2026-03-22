# Architecture Notes

## Planned Systems
- Wazuh server
- Windows endpoint
- Optional Linux endpoint

## Data Flow
- Endpoint telemetry -> Wazuh manager
- Alerts -> dashboard -> investigation workflow

## Network Design
- NAT for package downloads and updates
- Host-only for lab-internal communication

## Purpose
Simulate a small endpoint-focused security monitoring environment suitable for detection validation and investigation practice.
---
id: "example-tool::2025-12-19T03-12-00Z_incident_tcp-timeouts"
type: incident
severity: critical
occurredAt: "2025-12-19T03:12:00Z"
recordedAt: "2025-12-19T08:10:00Z"
title: "TCP timeouts causing periodic disconnects"
softwareKey: "example-tool"
deploymentKey: "prod-werk1-linie2-m7"
versionFrom: "1.3.8"
versionTo: "1.3.8"
labels: ["tcp", "timeout", "prod"]
references:
  - type: ticket
    label: "INC-1234"
    url: "https://tickets.example/INC-1234"
createdBy: "admin"
---
## Symptom
Disconnects every ~30 seconds, causing production pauses.

## Root Cause
Network keep-alive setting changed on switch without coordination.

## Fix
Switch config reverted. Added reconnect backoff in client.

## Prevention
- Mandatory `configuration_change` entry for network changes
- Canary deployment for Linie2

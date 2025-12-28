---
id: "example-tool::2025-12-20T09-00-00Z_correction_tcp-timeouts"
type: correction
severity: info
occurredAt: "2025-12-20T09:00:00Z"
recordedAt: "2025-12-20T09:00:00Z"
title: "Correction: root cause details for TCP timeouts incident"
softwareKey: "example-tool"
deploymentKey: "prod-werk1-linie2-m7"
labels: ["correction"]
references: []
createdBy: "admin"
correctionForId: "example-tool::2025-12-19T03-12-00Z_incident_tcp-timeouts"
changeReason: "Additional evidence from switch audit log"
---
## Correction
Root cause was specifically a keep-alive timeout reduction from 60s to 10s on port group Linie2.

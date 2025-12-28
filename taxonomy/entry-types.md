# Entry Types (v0.1)

- `release` — new software version available (global) or deployed (local with deploymentKey)
- `deployment_update` — update performed on a deployment/instance
- `incident` — outage, malfunction, user-impacting failure
- `outage` — planned/unplanned downtime event
- `maintenance` — routine maintenance work (cleanup, rotation, housekeeping)
- `security` — security-relevant event (patch, mitigation, advisory)
- `configuration_change` — config change (app/network/infra) affecting behavior
- `architecture_decision` — decision that changes structure/approach
- `inventory_change` — tool introduced, deprecated, retired, moved
- `correction` — correction of a previous entry
- `note` — general note that doesn't fit others

# SoftwareLogBook SPEC v0.1

## 1. Purpose
Define a minimal, portable and diff-friendly standard to document:
- multiple software tools in one organization
- deployments/instances per tool (PCs, machines, VMs, containers, embedded)
- lifecycle events as append-only logbook entries

## 2. Repository layout

software//
software.md
deployments/.md
entries/.md

_global/
entries/*.md

taxonomy/.md
templates/.md

### 2.1 `softwareKey`
- lowercase
- `a-z0-9-`
- unique within repository
Examples: `conapp-core-server`, `hr-reporting`, `vendor-plc-suite`

### 2.2 One entry = one file
Each event gets its own file under `entries/`.
This minimizes merge conflicts and keeps history readable.

## 3. File format: Frontmatter + Markdown body
All domain files (`software.md`, deployments, entries) use:

- YAML frontmatter between `---` lines
- Markdown body after frontmatter

## 4. Domain objects

### 4.1 Software record (`software/<softwareKey>/software.md`)
Required frontmatter fields:
- `id`: stable identifier (string; UUID/ULID recommended)
- `key`: must match folder name
- `name`: display name
- `category`: see `taxonomy/categories.md`
- `owner`: team/person/department
- `criticality`: low|medium|high
- `status`: active|deprecated|retired
- `createdAt`: ISO 8601 datetime
- `createdBy`: string

Optional:
- `vendorName`
- `supportContact`
- `documentationUrl`
- `tags`: list of strings
- `references`: list of Reference objects (see 4.4)

### 4.2 Deployment record (`software/<softwareKey>/deployments/*.md`)
Required:
- `id`
- `softwareKey`
- `deploymentKey`: unique within this software (slug recommended)
- `environment`: see `taxonomy/environments.md`
- `locationPath`: string (recommended: `Site/Area/Line/Machine`)
- `hostType`: pc|machine|vm|container|embedded|unknown
- `hostIdentifier`: hostname/assetTag/serial/instanceId
- `installedVersion`: string (semver recommended)
- `status`: active|offline|retired
- `createdAt`
- `createdBy`

Optional:
- `os`
- `architecture` (x64|arm64|...)
- `networkHint` (optional; avoid secrets)
- `references`: list of Reference
- `tags`: list

### 4.3 Entry (`software/<softwareKey>/entries/*.md` or `_global/entries/*.md`)
Required:
- `id`: stable entry id
- `type`: see `taxonomy/entry-types.md`
- `severity`: see `taxonomy/severities.md`
- `occurredAt`: ISO 8601 datetime
- `recordedAt`: ISO 8601 datetime
- `title`: short summary
- `softwareKey`: optional for global entries, required for software-scoped entries
- `deploymentKey`: optional (set if deployment-specific)
- `createdBy`: string

Optional:
- `versionFrom`, `versionTo`
- `labels`: list of strings
- `references`: list of Reference
- `correctionForId`: id of entry being corrected (append-only correction)
- `supersedesId`: id of entry being superseded
- `changeReason`: string

Rules:
- An entry MUST relate to either:
  - `softwareKey` (software-scoped), or
  - be in `_global/entries/` (global policy/event), optionally with `softwareKey`.
- If `deploymentKey` is set, `softwareKey` SHOULD be set as well.

### 4.4 Reference object

type: repo|docs|ticket|vendor|cve|release|build|other
label: string
url: string (URL/URI)
externalId: string (optional)
note: string (optional)

See `taxonomy/reference-types.md`.

## 5. Append-only policy
- Do not silently edit past entries.
- Corrections are new entries (`type: correction`) referencing `correctionForId`.
- If editing is unavoidable (typo), do it via a dedicated correction entry anyway.
- Git history is part of the audit trail.

## 6. Naming conventions
### 6.1 Entry file name
Recommended:
`YYYY-MM-DD_<type>_<short-slug>.md`

Examples:
- `2025-12-19_incident_tcp-timeouts.md`
- `2025-12-28_release_1.4.0.md`

### 6.2 `deploymentKey`
Recommended:
`<env>-<site>-<line>-<machine>` (free, but consistent)
Example: `prod-werk1-linie2-m7`

## 7. Security & data hygiene
- Never store secrets in logbook files.
- Avoid sensitive network details unless necessary.
- Prefer internal identifiers over personal data.

## 8. Compatibility
- This SPEC is versioned as `v0.1`.
- Future versions must remain backward readable.

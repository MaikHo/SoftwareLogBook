# SoftwareLogBook

SoftwareLogBook is a logbook for software systems using Markdown files with YAML frontmatter.

## Motivation and scope
SoftwareLogBook documents software tools, their deployments, and lifecycle events in a form that can be read and reviewed without special tooling.

Why files + Markdown + Git:
- Plain text is easy to read, diff, and review.
- Git provides history, accountability, and append-only discipline.
- The structure stays usable even in low-tooling environments.

Intended scenarios:
- Small to mid-sized inventories of internal or vendor tools.
- Teams that want a single, auditable place for releases, incidents, and maintenance notes.
- Environments where a lightweight, repository-based logbook is sufficient.

What this is not:
- Not a CMDB.
- Not a ticketing system.
- Not a monitoring system.

## Core concepts (high level)
- Software: a record describing a tool and its ownership context.
- Deployment: an installed instance of a software tool in an environment.
- Entry: an append-only event record (e.g., release, incident, maintenance).
- Global entry: an event or policy that applies across tools.
- Corrections: a dedicated entry that references the entry being corrected.

## Repository structure
- `software/<softwareKey>/`: per-tool folder.
- `software/<softwareKey>/software.md`: software record.
- `software/<softwareKey>/deployments/`: deployment records.
- `software/<softwareKey>/entries/<YYYY>/`: tool-specific logbook entries by year.
- `_global/entries/<YYYY>/`: global logbook entries by year.
- `taxonomy/`: shared enums and reference types.
- `templates/`: starter templates for new records.

## Minimal workflow
1. Create a new software record using `templates/software.template.md`.
2. Add deployment records using `templates/deployment.template.md`.
3. Add entries using `templates/entry.template.md` (release, incident, maintenance).
4. If something needs correction, add a new entry with `type: correction` that references the original entry.

## Further reading
- `SPEC.md`: source of truth for structure and rules.
- `CONTRIBUTING.md`: naming, uniqueness, and append-only guidance.
- `GUARDRAILS.md`: recommended validation checks and hygiene guidance.

## Viewer and tooling (optional)
The repository is fully usable without any tooling. Viewers or CLI tools can be built on top, but they are not part of the standard.

## License
MIT (see `LICENSE`)

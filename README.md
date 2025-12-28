# SoftwareLogBook

A service logbook for software systems — lightweight, repository-friendly, and readable without tooling.

## What this is
SoftwareLogBook is a **standardized folder + Markdown format** to document:
- software tools used in an organization
- their deployments (machines/PCs/instances)
- lifecycle events (releases, incidents, maintenance, security, decisions)

It is designed to be:
- **human-readable**
- **diff-friendly**
- **portable**
- **tool-agnostic**
- **MIT licensed**

## Quick start
1. Copy `templates/software.template.md` into `software/<softwareKey>/software.md`
2. Add deployments under `software/<softwareKey>/deployments/`
3. Add logbook entries under `software/<softwareKey>/entries/<YYYY>/`

## Viewer tooling (optional)
A future viewer can parse frontmatter metadata and render timelines, dashboards, and graphs.
The repo remains usable even without a viewer.

## License
MIT (see `LICENSE`)

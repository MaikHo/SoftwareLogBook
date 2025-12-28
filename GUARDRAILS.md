# Guardrails

## Recommended checks
- YAML frontmatter parses and required fields exist.
- `occurredAt` and `recordedAt` are ISO 8601.
- `type`, `severity`, `environment`, `hostType`, `status` match taxonomy enums.
- `id` values are unique repo-wide.
- `type: correction` entries include `correctionForId` and it exists.
- Entry path year matches `occurredAt` (fallback: `recordedAt`).
- No placeholder values like `"..."` remain in example or template files.

## Security and privacy
- Do not store secrets (tokens, passwords, API keys).
- Avoid personal data; prefer internal identifiers.

# Contributing

## Naming rules
- `softwareKey` must match `^[a-z0-9-]+$` and be unique in the repo.
- `deploymentKey` should be unique within a software and follow `<env>-<site>-<line>-<machine>`.
- Entry filenames must follow `YYYY-MM-DD_<type>_<short-slug>.md` under `entries/<YYYY>/`.

## ID uniqueness
- All `id` values must be unique across the repository.
- Recommended entry `id` format: `<scopeKey>::<timestamp>_<type>_<slug>`.
  - `scopeKey` is the `softwareKey` for software entries, or `global` for `_global/entries/`.

## Append-only policy
- Do not edit past entries.
- Use a new entry with `type: correction` and `correctionForId` to fix or clarify prior entries.

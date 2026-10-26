# Weigh-in Log

A tiny offline-first weight log that runs as an installable web app (PWA) on Android.

- All data is stored **on the device** (browser storage). Nothing is sent anywhere.
- Works offline after the first visit.
- Export/import as CSV for backup.

## Install on Android
1. Open the GitHub Pages URL in Firefox or Chrome.
2. Menu (⋮) → **Install** / **Add app to Home screen**.

## Data model (ready for future sync)
`localStorage["weighin.records.v1"]`:

```json
{ "2026-10-26": { "kg": 78.4, "updatedAt": 1793001234567 },
  "2026-10-25": { "deleted": true, "updatedAt": 1792990000000 } }
```

One record per date; the latest `updatedAt` wins. Deletes are kept as tombstones so they can sync too.

## Updating
Edit files, bump `VERSION` in `sw.js`, push. The app picks up the new version on the next online launch.

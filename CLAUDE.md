# Home Dashboard — Project Rules

## Bank Transaction Data

- **CSV files are read-only.** Never write to, modify, or delete any bank transaction file. The File System Access API directory picker must always use `mode: 'read'`.
- **Transactions are loaded once and cached.** Once a CSV has been parsed into memory, do not re-read it from disk automatically (e.g. on tab switch, page interaction, or timer). Only reload transaction data when the user explicitly triggers it — for example by clicking "Open Folder".
- **Past transactions are static.** Treat all rows in a `Data_Export_*.csv` as immutable historical records. Never mutate, filter out, or discard parsed transaction rows during a session.

## General

- This is a single-file vanilla JS app (`index.html`). Keep it that way — no build tools, no npm dependencies, no external scripts beyond the Google Fonts link already present.
- Budget limits (per-category spending targets) are the only user-editable budget data and are persisted in `localStorage`.

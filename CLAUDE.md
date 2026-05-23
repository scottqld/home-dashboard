# Home Dashboard — Project Rules

## Bank Transaction Data

- **CSV files are read-only.** Never write to, modify, or delete any bank transaction file. The File System Access API directory picker must always use `mode: 'read'`.
- **Transactions are persisted in IndexedDB** (`home-dashboard-budget` database, `transactions` store). On startup, data loads from IndexedDB — no CSV access required. The `imported_files` store tracks which filenames have already been processed.
- **Import is incremental and explicit.** "Open Folder" scans for `Data_Export_*.csv` files, imports only files not already in `imported_files`, and appends their rows to the `transactions` store. Never re-import a file that has already been recorded.
- **Past transactions are static.** Treat all rows in a `Data_Export_*.csv` as immutable historical records. Never mutate, filter out, or discard parsed transaction rows.

## General

- This is a single-file vanilla JS app (`index.html`). Keep it that way — no build tools, no npm dependencies, no external scripts beyond the Google Fonts link already present.
- Budget limits (per-category spending targets) are the only user-editable budget data and are persisted in `localStorage`.

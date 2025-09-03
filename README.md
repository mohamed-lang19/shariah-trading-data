# Shariah Trading Data

This repository contains data snapshots and logs for a France‑based, Shariah‑compliant equity trading system.  All dates and timestamps are recorded in UTC (YYYY‑MM‑DD format), and the data is validated against JSON Schema definitions stored in the `schemas/` directory.

## Directory structure

- `data/` – Latest snapshots:
  - `holdings.json` – Daily snapshot of current portfolio holdings, prices, compliance ratios, and news.
  - `watchlist.json` – Weekly snapshot of the screened universe and watchlist candidates.
  - `purification.json` – Ledger of realised gains, dividends, and purification calculations.

- `archives/` – Historical snapshots.  Files are named `{name}_{YYYY‑MM‑DD}.json` and are created automatically whenever a new snapshot is written.

- `logs/` – Append‑only NDJSON logs capturing each action taken by the data pipeline.  File names follow `activity_{YYYY‑MM‑DD}.ndjson` and contain one JSON object per action.

- `schemas/` – JSON Schema files used to validate the structure of the data files.

## Usage

The data pipeline ensures that every update to `data/` files is backed up, validated against its schema, and logged.  Schemas can be used by downstream consumers to programmatically validate data integrity.

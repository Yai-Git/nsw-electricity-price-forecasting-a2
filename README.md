# NSW electricity-price forecasting — A2 notebook

This public repository contains the self-contained reproducibility notebook for a
machine-learning study of eight-hour NSW1 electricity-price forecasting from
five-minute market data.

Open `09_final_public_a2.ipynb` in Google Colab and run it from top to bottom. The
notebook:

- installs the frozen package versions;
- downloads the fixed `a2-data-v1` release asset without authentication;
- verifies the exact file size and SHA-256 checksum before loading the CSV;
- validates the dataset schema, timestamps and continuity segments;
- constructs leakage-safe training, validation, development and test samples;
- reproduces the seasonal-naive, Ridge and Random Forest experiments; and
- stops if a resource safeguard or frozen-result assertion fails.

The dataset is not stored in this repository. It is downloaded from the separate,
data-only repository release:

`https://github.com/Yai-Git/nsw-electricity-price-data-a2/releases/download/a2-data-v1/prices_NSW1_5min_prepared.csv`

Expected dataset properties:

- Size: `14,238,528` bytes
- SHA-256: `d9a3059fb517eabbdabfa2016b1195fef29eeff0bce00c0b60d7defeab0cddb7`
- Rows: `348,371`
- Date range: `2021-10-01 00:05:00` to `2025-01-22 15:50:00`

The complete Random Forest sequence requires at least 4 GiB and 30% available system
memory; at least 5 GiB available is recommended. The notebook does not weaken its
approved process, memory or runtime limits after a failure.

Data source: Australian Energy Market Operator (AEMO), NEMWeb market data. The dataset
is an assignment-specific prepared NSW1 extract and is not an official AEMO
redistribution format. AEMO material is used with attribution in accordance with
[AEMO's Copyright Permissions](https://www.aemo.com.au/privacy-and-legal-notices/copyright-permissions).

Only the notebook and this README belong in this repository. It intentionally excludes
the dataset, report, PDF, predictions, feature matrices, target matrices, fitted models
and personal project notes.

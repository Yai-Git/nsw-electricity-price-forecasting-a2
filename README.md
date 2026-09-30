# NSW1 electricity-price forecasting — A2 notebook

This repository contains the public reproducibility notebook for a comparison of
seven forecasting implementations and a daily seasonal-naive baseline for NSW1
electricity prices.

Open `09_final_public_a2.ipynb` in Google Colab and run it from top to bottom. The
default workflow:

- downloads the fixed public NSW1 dataset and verifies its size and SHA-256 checksum;
- validates the schema, chronology, recorded five-minute spacing and two data gaps;
- reconstructs and validates the one-row mapping to the archived research series;
- downloads a compact archived-forecast bundle from the fixed `a2-evidence-v1` release;
- verifies file hashes, decoded-array hashes, shapes, dtypes, forecast origins and targets;
- recalculates pooled and per-window point metrics and probabilistic CRPS; and
- stops if an input or frozen result differs from the approved evidence.

The notebook also contains model-specific preparation, training and inference paths for
ARIMA, Random Forest, quantile LightGBM, DLinear, N-HiTS, Sundial and a MOMENT linear
probe. These expensive paths are disabled by default because they require different
libraries and compute environments. They were checked locally against the archived
forecasts before publication. The exact historical checkpoint revisions for Sundial and
MOMENT were not recorded, so numerical matches do not establish exact historical
checkpoint identity.

## Fixed public inputs

Prepared NSW1 dataset:

`https://github.com/Yai-Git/nsw-electricity-price-data-a2/releases/download/a2-data-v1/prices_NSW1_5min_prepared.csv`

- Size: `14,238,528` bytes
- SHA-256: `d9a3059fb517eabbdabfa2016b1195fef29eeff0bce00c0b60d7defeab0cddb7`
- Rows: `348,371`
- Date range: `2021-10-01 00:05:00` to `2025-01-22 15:50:00`

Compact archived-metric evidence:

`https://github.com/Yai-Git/nsw-electricity-price-forecasting-a2/releases/tag/a2-evidence-v1`

The release contains protocol metadata, forecast origins, targets, reconstructable
seasonal-naive forecasts, seven archived point-forecast arrays, LightGBM and Sundial
probabilistic samples, historical timing metadata and a checksum manifest. It contains
no model weights or fitted objects.

Data source: Australian Energy Market Operator (AEMO), NEMWeb market data. The dataset
is an assignment-specific prepared NSW1 extract and is not an official AEMO
redistribution format. AEMO material is used with attribution in accordance with
[AEMO's Copyright Permissions](https://www.aemo.com.au/privacy-and-legal-notices/copyright-permissions).

The repository tree contains only this README and the notebook. The dataset and compact
evidence are supplied as fixed release assets; the report, PDF, feature matrices,
targets, fitted models, model weights and personal project notes are not stored here.

# Data Cleaning & Normalization Pipeline

Ceramic analysis FS Louie

## 1 . Objective

Provide a reproducible pipeline that converts the heterogeneous raw spreadsheet into tidy, analysis‑ready CSVs suitable for QGIS/ArcGIS visualizations.

## 2 . Files & Columns

* **Input**: `Ceramic analysis FS Louie.xlsx` (417 rows)
  Key columns referenced: `pattern`, `year opened`, `year closed`, `earliest year for artifact`, `latest year for artifact`, `Vessel form`, `Restuarant Name`, `Is it in the 1960 Catalog?`
* **Auxiliary**: `1960 restaurants.xlsx` (68 rows) – restaurant names for catalog check.

## 3 . Pattern Normalization

**Goal** : collapse hundreds of free‑text pattern strings into a small, interpretable legend.

Canonical classes adopted:

* Bird and Flower (BF)
* Dragon and Phoenix (DP)
* God of Longevity (GL)
* Women / Characters (TW)
* Individualized Logo (IL)
* Lustre Floral (LF)
* Custom / Misc Pattern (CP)
* Other (OT – audit catch‑all)

Implementation highlights:

* Lower‑case, trim input → regex search against legend.
* Blank, “0”, or “nan” → Custom / Misc Pattern.
* Counts after cleaning (example run): Women/Characters 140; Dragon & Phoenix 85; etc.
* Output: `..._clean.csv`

## 4 . Year Columns Standardization

Challenges: mixed formats (Excel dates, ranges like “1955‑60”, phrases like “still open”).
Solution:

1. Parse each cell into `(min_year, max_year)` using `cell_to_range()` helper.
2. Convert back to a compact string via `rng_to_string()`.
3. Preserve semantic hints (e.g. “still open” →  empty max year with today’s year if needed).
   Produces trustworthy numeric sliders for GIS.
   Output: `..._dates_clean.csv`

## 5 . Vessel Form Classification

Canonical labels: Tea Cup, Saucer, Ash Tray, Bowl, Plate, Platter, Dish, Tea Pot, Spoon, Vase, Other.
Simple keyword look‑ups power `normalize_vessel()`.
Example counts: Tea Cup 253; Ash Tray 88; …
Output: `..._vessel_clean.csv`

## 6 . 1960 Catalog Flag Verification

Logic:

* Build lowercase lookup set from the catalog.
* For each row in full dataset, set `Is it in the 1960 Catalog?` to “yes” when the restaurant name appears in the lookup (existing “yes” preserved).
  Output: `..._1960flag.csv`

## 7 . Outputs & Naming Convention

Each step writes a new CSV sibling to the source file, suffixed with the cleaned aspect.
Example: `Ceramic analysis FS Louie_clean.csv`, `Ceramic analysis FS Louie_dates_clean.csv`, etc.

## 8 . Usage Notes

1. Run the scripts inside Google Colab or a local Jupyter session with `pandas ≥ 2`.
2. Keep a versioned copy of the raw spreadsheet; do not overwrite.
3. After cleaning, load the final CSV into QGIS. Style by the canonical pattern field or use year ranges for temporal filters.

## 9 . Next Steps

* Validate outliers in the “Other” pattern bucket.
* Geocode owner surnames to probe spatial clustering.
* Extend the pipeline with unit tests to guard regex changes.


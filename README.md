# F.S. Louie Mid-Century Ceramic Analysis

This repository contains the data-processing, GIS analysis, and visualization scripts related to the research on mid-century ceramic distributions by F.S. Louie Importing Co. The analyses provide insights into patterns, chronological developments, and regional clustering of ceramic supplies to Chinese-American restaurants from 1950 to 1989.

---

## Project Overview

This research investigates the spatial and temporal distribution patterns of ceramic dinnerware, focusing on motifs such as Bird-and-Flower, Dragon-and-Phoenix, and Twin Women, imported and distributed by F.S. Louie. It leverages archival records, GIS data, and ceramic artifact analysis to understand business strategies, distribution logistics, and historical migration of restaurant clusters.

---

## Repository Structure

* **01\_pattern\_clean.ipynb**: Cleans and standardizes ceramic pattern labels from the original archival dataset.

* **02\_year\_parse.ipynb**: Normalizes and formats inconsistent date information for restaurant openings and closings.

* **03\_vessel\_form.ipynb**: Categorizes vessel forms (e.g., tea cups, plates) for streamlined analysis.

* **excel\_to\_csv\_converter.py**: Converts raw Excel data into CSV format for easier analysis and integration with other scripts.

---

## GIS Analysis Workflow

1. **Data Preprocessing**:

   * Label normalization
   * Date formatting and consistency checks
   * Vessel form classification

2. **Spatial Analysis**:

   * Geocoding restaurant locations
   * Kernel density estimation for restaurant distribution over decades
   * DBSCAN clustering to identify key distribution clusters
   * Getis-Ord Gi\* hotspot analysis to detect significant spatial clusters

3. **Visualization**:

   * Export and classification of GIS layers (QGIS)
   * Production of hotspot maps and cluster visualizations

---

## Dependencies

Ensure you have the following Python packages installed:

* `pandas`
* `numpy`
* `geopandas`
* `scikit-learn`
* `matplotlib`
* `seaborn`

Installation:

```bash
pip install pandas numpy geopandas scikit-learn matplotlib seaborn
```

---

## Data Sources

* **Business Records**: Baldwin-Kee Family Papers (Invoice Ledger, 1950–1989)
* **Printed Catalogs**: F.S. Louie Co. catalogs (1960 & 1983)
* **Ceramic Artifacts**: Wilkie Ceramic Collection, Archaeological Research Facility, UC Berkeley

---

## Usage

Clone the repository:

```bash
git clone [repository-link]
```

Navigate to the project directory and run notebooks in order:

1. Data cleaning
2. Date parsing
3. Vessel form categorization

Execute GIS analyses using outputs from these scripts.

---

## Contribution

Contributions, suggestions, and issue reports are welcome. Feel free to submit pull requests or open issues to enhance the research and analysis.

---

## License

This project is open-source and available under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

## Contact

For questions or further collaboration, please contact:

* **\[Junjie Xiong]**
* **\[junjiexiong@berkeley.edu]**

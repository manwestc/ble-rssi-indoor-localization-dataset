![DOI](https://zenodo.org/badge/DOI/XXXXX.svg)
![License](https://img.shields.io/badge/license-CC--BY--4.0-blue)
![Dataset](https://img.shields.io/badge/type-dataset-green)

# BLE RSSI Fingerprint Dataset for Smartphone-Based Indoor Localization

This repository contains a Bluetooth Low Energy (BLE) RSSI fingerprint dataset collected for indoor localization experiments using a smartphone receiver and six BLE beacons deployed in a real university building.

The dataset was collected in two indoor areas of the **Escuela Superior de Ingeniería Informática de Albacete (ESIIAB), Universidad de Castilla-La Mancha, Spain**, and is intended to support research on indoor positioning, wireless sensing, and machine learning for location estimation.

The dataset accompanies the following data article:

> **A Bluetooth Low Energy RSSI fingerprint dataset for smartphone-based multi-floor indoor localization with multiple transmission power levels**

Additional documentation describing the experimental environment is provided in the **technical report included in this repository**.

---

# Dataset Overview

The dataset contains Bluetooth Low Energy **Received Signal Strength Indicator (RSSI)** fingerprints collected using:

- **6 BLE beacons** (MOKO SMART H2)
- **1 smartphone receiver** (Xiaomi Mi 9T Pro)

The measurement environment was divided into **28 labeled sectors** across two floors:

| Floor | Number of sectors |
|------|------|
| First floor | 7 sectors (1A–7A) |
| Ground floor | 21 sectors (1B–21B) |

For each sector, RSSI measurements were collected from the six deployed beacons.

Three beacon **transmission power levels** were evaluated:
```
-8 dBm
-4 dBm
0 dBm
```
For each sector and transmission power configuration, **approximately 100 RSSI samples** were collected.

---

# Repository Structure
```
BLE_RSSI_Indoor_Localization_Dataset/

README.md

data/
Tx_8.csv
Tx_8A.csv
Tx_8B.csv
Tx_4.csv
Tx_4A.csv
Tx_4B.csv
Tx0.csv
Tx0A.csv
Tx0B.csv

metadata/
variable_codebook.csv
sector_metadata.csv
beacon_metadata.csv

images/
first_floor_layout.pdf
ground_floor_layout.pdf
first_floor_environment.jpg
ground_floor_environment.jpg

documentation/
technical_report_environment.pdf

Notebooks
Tx_8.ipynb
Tx_8A.ipynb
Tx_8B.ipynb
Tx_4.ipynb
Tx_4A.ipynb
Tx_4B.ipynb
Tx0.ipynb
Tx0A.ipynb
Tx0B.ipynb
```

The notebooks included in this repository allow researchers to reproduce the exploratory analyses and baseline experiments reported in the associated technical documentation.

---

# Dataset Files

The **data/** directory contains the processed RSSI fingerprint datasets.

The naming convention follows the format: `Tx_POWER[Floor].csv`

where:

- `Tx_8` → transmission power **−8 dBm**
- `Tx_4` → transmission power **−4 dBm**
- `Tx0` → transmission power **0 dBm**

and

- `A` → first floor dataset
- `B` → ground floor dataset
- no suffix → combined dataset (both floors)

Example:

| File | Description |
|-----|-----|
| Tx_8.csv | Combined dataset (both floors) at −8 dBm |
| Tx_8A.csv | First-floor dataset at −8 dBm |
| Tx_8B.csv | Ground-floor dataset at −8 dBm |

---

# Dataset Variables

Each dataset file contains **7 columns**.

| Variable | Type | Description |
|--------|--------|--------|
| B1 | numeric | RSSI value (dBm) from beacon B1 |
| B2 | numeric | RSSI value (dBm) from beacon B2 |
| B3 | numeric | RSSI value (dBm) from beacon B3 |
| B4 | numeric | RSSI value (dBm) from beacon B4 |
| B5 | numeric | RSSI value (dBm) from beacon B5 |
| B6 | numeric | RSSI value (dBm) from beacon B6 |
| sector | categorical | Label of the sector where the measurement was recorded |

---

# Measurement Environment

The measurements were conducted in two indoor areas of the ESIIAB building:

### First-floor area

- Corridor environment
- Approximate size: **10.5 m × 2.4 m**
- Divided into **7 sectors (1A–7A)**

### Ground-floor area

- Open indoor area
- Approximate size: **10.5 m × 6 m**
- Divided into **21 sectors (1B–21B)** arranged in a **3 × 7 grid**

The smartphone receiver was positioned **approximately at the center of each sector** during data acquisition.

Detailed floor layouts and photographs of the environment are provided in the **images/** folder.

---

# Beacon Deployment

Six BLE navigation beacons (**MOKO SMART H2**) were deployed during the measurement campaign.

The devices were labeled: `B1, B2, B3, B4, B5, B6`

Deployment characteristics:

- rectangular deployment geometry
- approximate **6 m spacing between adjacent beacons**
- **6 m distance between opposite beacon pairs**
- installed at approximately **6 m height**

This configuration provided spatial coverage across both measurement areas.

---

# Data Acquisition Procedure

RSSI measurements were collected using a **Xiaomi Mi 9T Pro smartphone** acting as the receiver device.

The following mobile applications were used:

| Tool | Purpose |
|-----|-----|
BeaconX Pro | Beacon configuration |
BLE Scanner and Logger | RSSI data acquisition |

Measurement procedure:

1. Configure beacon transmission power
2. Verify beacon detection using BLE scan
3. Position the smartphone at the center of the sector
4. Start RSSI logging
5. Record approximately **100 samples per sector**
6. Export measurements as CSV files

The acquisition campaign was repeated for each transmission power level.

---

# Potential Use Cases

The dataset can be used for:

- indoor localization benchmarking
- RSSI fingerprinting research
- machine learning experiments
- wireless signal propagation analysis
- feature engineering and preprocessing studies
- multi-floor indoor positioning research
- educational demonstrations in wireless sensing and data science

---

# Baseline Benchmark Results

Exploratory machine learning experiments were conducted to provide an illustrative reference benchmark for the dataset.

The best observed classification results across several models are summarized below:

| Tx (dBm) | First floor | Ground floor | All floors |
|------|------|------|------|
| -8 | 73.29% / 0.775 m | 64.95% / 0.621 m | 62.68% / 0.523 m |
| -4 | 73.43% / 0.820 m | 58.38% / 0.426 m | 58.00% / 0.551 m |
| 0 | 70.86% / 0.635 m | 59.71% / 0.672 m | 59.04% / 0.463 m |

These results correspond to the **best-performing models observed in exploratory experiments** and should be interpreted as reference baseline values.

---

# Limitations

- Data were collected in **a single university building**
- Only **one receiver device** was used
- Measurements correspond to **one beacon model**
- The beacon deployment configuration remained **fixed during the campaign**
- The dataset contains **RSSI fingerprints only** (no inertial or orientation data)

---

# Citation

If you use this dataset in your research, please cite the associated data article: `Citation to be added after publication`

---

# License

Apache license 2.0.






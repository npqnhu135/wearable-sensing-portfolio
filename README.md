# Wearable Sensing Portfolio

> Three low-cost wearable sensing prototypes built without dedicated laboratory access, characterized under controlled protocols and released with raw data, firmware, and analysis pipelines. **Total bill of materials: USD $46.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![Reproducibility](https://img.shields.io/badge/reproducibility-Run%20All-brightgreen.svg)](#reproducing-the-results)
[![Status: undergraduate research](https://img.shields.io/badge/status-undergraduate%20research-orange.svg)](#about-this-work)

**Author:** Nguyen Phan Quynh Nhu — Human-Centered Engineering, Class of 2028, Fulbright University Vietnam
**Report date:** May 2026 · **Last updated:** May 2026

📄 **[Research Summary (PDF)](RESEARCH_SUMMARY.pdf)**
📂 **[Lab setup & full capture photos (Google Drive)](https://drive.google.com/drive/folders/1KDHBZTqG8OIstBDkzPv-oR9viV3r7mc4?usp=drive_link))**

---

## Table of contents

1. [Abstract](#abstract)
2. [Key result](#key-result)
3. [The three tracks](#the-three-tracks)
4. [Repository structure](#repository-structure)
5. [Installation and dependencies](#installation-and-dependencies)
6. [Reproducing the results](#reproducing-the-results)
7. [Hardware used](#hardware-used)
8. [Limitations and known issues](#limitations-and-known-issues)
9. [About this work](#about-this-work)
10. [How to cite](#how-to-cite)
11. [License and acknowledgments](#license-and-acknowledgments)
12. [Contact](#contact)

---

## Abstract

Continuous vital-sign monitoring in resource-limited clinical settings is gated by three intersecting constraints: device cost, battery life, and sensor robustness outside the laboratory. This portfolio presents three independently characterized wearable-sensing prototypes built without dedicated laboratory access, each targeting a distinct physical modality.

A **TEC1-12706 thermoelectric module** is characterized under a three-phase graded heat stimulus, achieving a 9.6 °C hot-side temperature differential with quantified asymmetric heating-versus-cooling kinetics. A **DIY piezoresistive force sensor**, assembled from kitchen-grade materials (EVA sponge, aluminium foil, steel-wool mesh) at a bill of materials under USD $1, detects 222 discrete press events across a 0–777 ADC dynamic range. An **AD8232 single-lead ECG analog front-end** is reported here with a 70.1 % rail-saturation failure mode, documented intentionally with root-cause diagnosis and a specific hardware remediation plan — in the interest of reproducibility for resource-limited builds.

All raw data, firmware, and analysis notebooks are released openly to enable independent verification by other groups in similar settings.

---

## Key result

![TEG hot-side temperature under three-phase graded stimulus](01_teg_thermal_response/figures/fig1_thermal_response.png)

**Figure 1 — TEC1-12706 hot-side thermal response.** Three-phase graded heat stimulus produced ΔT = 1.6, 6.4, and 9.6 °C peaks above a 33.6 °C baseline (top panel, smoothed trace in red). The instantaneous rate of change (bottom panel) reveals asymmetric kinetics: rise τ ≈ 60 s, decay τ ≈ 180 s — implicating cold-side thermal resistance as the rate-limiting parameter, consistent with the wearable thermoelectric generator literature consensus.

See [`01_teg_thermal_response/`](01_teg_thermal_response/) for the full analysis notebook and raw data.

---

## The three tracks

| # | Track | Modality | Result | BOM | Folder |
|---|---|---|---|---|---|
| 1 | **Thermoelectric energy harvesting** | Heat → voltage (reverse Seebeck) | ✅ ΔT 9.6 °C, asymmetric kinetics quantified | $9 | [`01_teg_thermal_response/`](01_teg_thermal_response/) |
| 2 | **Piezoresistive pressure sensor** | Force → resistance change | ✅ 222 events detected, 0–777 ADC range | <$1 | [`02_pressure_sensor/`](02_pressure_sensor/) |
| 3 | **ECG analog front-end** | Biopotential → ADC | ⚠️ 70.1 % rail saturation — root cause identified, fix proposed | $11 | [`03_ecg_diagnostic/`](03_ecg_diagnostic/) |

Each folder contains a self-contained `README.md`, an executable `analysis.ipynb`, the raw CSV data under `data/`, and the key result figure under `figures/`. All notebooks regenerate their figures from raw CSV via *Restart Kernel → Run All*.

The inclusion of a documented failure mode (Track 3) is intentional and reflects a reproducibility-first ethos: future researchers attempting similar builds in resource-limited settings benefit more from a published failure mode with diagnosis than from a re-recorded "successful" trace whose provenance is undocumented. See Section 4.3 of the research report for the full failure characterization and Section 4.4 for the proposed remediation.

---

## Repository structure

```
wearable-sensing-portfolio/
├── README.md                              ← this file
├── RESEARCH_SUMMARY.pdf                   ← 6-page report (PDF)
├── lab_photos.pdf                         ← 17-page hardware documentation
├── LICENSE                                ← MIT
├── .gitignore
│
├── 01_teg_thermal_response/
│   ├── README.md                          ← track-specific protocol + interpretation
│   ├── analysis.ipynb                     ← thermal analysis pipeline
│   ├── data/
│   │   └── teg_data_summary.csv           ← 1107 samples, 1 Hz, 19.1 min recording
│   └── figures/
│       └── fig1_thermal_response.png      ← key result, Figure 1 above
│
├── 02_pressure_sensor/
│   ├── README.md
│   ├── analysis.ipynb                     ← event detection + amplitude/duration analysis
│   ├── data/
│   │   └── pressure_press_demo.csv        ← 45-second demonstration recording
│   └── figures/
│       └── fig_pressure_analysis.png      ← 4-panel result
│
└── 03_ecg_diagnostic/
    ├── README.md
    ├── analysis.ipynb                     ← saturation diagnosis + spectral characterization
    ├── data/
    │   └── ecg_raw_250hz.csv              ← 139,766 samples at 250 Hz, 559 s
    └── figures/
        └── fig_ecg_diagnostic.png         ← 3-panel diagnostic
```

---

## Installation and dependencies

Tested on Windows 11 and Ubuntu 22.04 with Python 3.11.7. CPython 3.11+ is recommended.

### Option A — Quick install (pip)

```bash
git clone https://github.com/npqnhu135/wearable-sensing-portfolio.git
cd wearable-sensing-portfolio
pip install -r requirements.txt
jupyter lab
```

### Option B — Reproducible environment (conda)

```bash
git clone https://github.com/npqnhu135/wearable-sensing-portfolio.git
cd wearable-sensing-portfolio
conda env create -f environment.yml
conda activate wearable-sensing
jupyter lab
```

### Pinned dependencies (`requirements.txt`)

```
numpy==1.26.4
pandas==2.2.0
scipy==1.13.0
matplotlib==3.8.3
jupyterlab==4.1.5
```

No GPU is required. End-to-end notebook execution takes under 30 seconds per track on a standard laptop (i5-1135G7 or comparable).

---

## Reproducing the results

Every figure and statistic claimed in the research report can be regenerated from the raw CSV via the following commands. Each notebook is structured to run cleanly from a fresh kernel.

| Track | Result claimed | Command | Expected output |
|---|---|---|---|
| 1 | TEG thermal response, peak ΔT 9.6 °C | `jupyter lab 01_teg_thermal_response/analysis.ipynb` → Run All | `figures/fig1_thermal_response.png` + per-phase metrics table |
| 2 | 222 press events, 0–777 ADC range | `jupyter lab 02_pressure_sensor/analysis.ipynb` → Run All | `figures/fig_pressure_analysis.png` + `press_events.csv` |
| 3 | 70.1 % rail saturation, 30 Hz oscillation | `jupyter lab 03_ecg_diagnostic/analysis.ipynb` → Run All | `figures/fig_ecg_diagnostic.png` + saturation statistics |

If any of these commands fail to reproduce the stated result, please open an issue.

---

## Hardware used

All measurements were acquired on a personal workspace without access to dedicated laboratory infrastructure. Hardware procured locally in Ho Chi Minh City, Vietnam (May 2026).

| Role | Component | Notes |
|---|---|---|
| Microcontroller + ADC | ESP32-S3 (YOLO:UNO board) | 12-bit ADC, 250 Hz sustained sampling verified |
| Thermoelectric module | TEC1-12706, 40 × 40 × 4 mm | Bi₂Te₃ pellets, ~2.5 Ω internal resistance |
| Cold-side heat sink | Intel stock CPU cooler | Cu base + Al fins, passive cooling |
| Hot-side temperature sensor | DS18B20 | 12-bit resolution, ±0.5 °C absolute, ≈750 ms conversion |
| ECG analog front-end | AD8232 breakout | Single-lead, single-supply 3.3 V |
| Pressure sensor (DIY) | EVA sponge + Al foil + steel wool | <$1 BOM, no commercial part |
| Reference electrodes | Ag/AgCl gel pads, Lead-I configuration | Disposable medical-grade |
| Power | 9 V battery + LM7805 regulator | Isolated from laptop USB |
| Programmable heat source | Silicone heat pad (~5 W) + bench DC supply | Three intensity steps |

Analysis was performed on a Windows 11 laptop (Python 3.11.7, no GPU).

---

## Limitations and known issues

This work is undergraduate research and explicitly does not claim novel scientific contributions. The following limitations should be considered when interpreting results:

- **TEG characterization** used a rigid bench geometry (CPU cooler + foil-and-foam phantom) rather than skin contact under clothing. Reported ΔT values are therefore optimistic relative to a real wearable boundary condition. No P-vs-R_load curve was measured; internal resistance and maximum power point are not yet extracted.
- **Pressure sensor** is not force-calibrated; ADC counts cannot be converted to Newtons. Firmware-side threshold gating precludes recovery of baseline drift. Estimated sampling rate (~50 Hz) likely undersamples brief manual taps.
- **ECG front-end** produced no usable biological signal in this build. The downstream NeuroKit2 pipeline and the planned PhysioNet MIT-BIH benchmark comparison were therefore not exercised on real data. The proposed hardware fix (REF pin biasing, isolated supply) is recorded but not yet validated.

Planned next-iteration work is itemized in Section 6 of the research report.

---

## About this work

This portfolio was assembled as preparation for PhD applications in the Fall 2027 admission cycle. The longer-term research direction is **signal processing and sensor fusion for multimodal physiological estimation under low-power, low-quality-signal constraints**, with the OUCRU Vietnam dengue patient monitoring use case as the initial application target.

The decision to release both quantitative results (Tracks 1 and 2) and a documented failure mode with diagnosis (Track 3) reflects a deliberate commitment to reproducibility-first practice — particularly for research conducted in resource-limited settings, where silent failure modes carry a higher cost to future researchers attempting similar builds.

---

## How to cite

If you reference this portfolio in academic or technical work, please cite as:

```bibtex
@misc{nguyen2026wearable,
  author       = {Nguyen, Phan Quynh Nhu},
  title        = {Wearable Sensing Portfolio: A Three-Modality Low-Cost Prototype
                  for Resource-Limited Vital-Sign Monitoring},
  year         = {2026},
  month        = {May},
  howpublished = {\url{https://github.com/npqnhu135/wearable-sensing-portfolio}},
  note         = {Undergraduate research portfolio, Fulbright University Vietnam}
}
```

A machine-readable `CITATION.cff` is provided at the repository root.

---

## License and acknowledgments

Code and documentation are released under the [MIT License](LICENSE). Raw data files are released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — you may reuse them with attribution.

**Acknowledgments.** This work was conducted as a self-directed undergraduate project. Datasets referenced for benchmarking purposes are the property of their respective original creators: the [PhysioNet MIT-BIH Arrhythmia Database](https://physionet.org/content/mitdb/1.0.0/) (Goldberger et al., 2000), used as the intended reference benchmark for Track 3.

---

## Contact

- **Email:** nhu.nguyen.240109@student.fulbright.edu.vn (primary) · npqnhu.work@gmail.com (backup)
- **LinkedIn:** [linkedin.com/in/qnhuphnguyn](https://www.linkedin.com/in/qnhuphnguyn)
- **Repository:** [github.com/npqnhu135/wearable-sensing-portfolio](https://github.com/npqnhu135/wearable-sensing-portfolio)

For questions about the protocols, reproducing the results, or the proposed ECG hardware fix, please open an issue on this repository or send an email.

# Wearable Sensing Portfolio

Three low-cost wearable-sensing prototypes built without dedicated lab access, each
targeting a distinct physical modality. Total bill of materials under **USD $50**.

**Nguyen Phan Quynh Nhu** · Human-Centered Engineering, Class of 2028
Fulbright University Vietnam · 

📄 **[Research summary (PDF)](RESEARCH_SUMMARY.pdf)**

---

## The three tracks

| # | Track | Modality | Status | Folder |
|---|---|---|---|---|
| 1 | **Thermoelectric energy harvesting** | Heat → voltage (Seebeck effect) | ✅ Quantitative result | [`01_teg_thermal_response/`](01_teg_thermal_response/) |
| 2 | **Piezoresistive pressure sensor** | Force → resistance change | ✅ Quantitative result | [`02_pressure_sensor/`](02_pressure_sensor/) |
| 3 | **ECG analog front-end** | Biopotential → ADC | ⚠️ Documented failure mode + diagnosis | [`03_ecg_diagnostic/`](03_ecg_diagnostic/) |

Each track is a self-contained folder with raw data, analysis notebook, and a key
figure. All notebooks reproduce their figures from raw CSV via `Run All`.

---

## Quick reproduce

```bash
git clone https://github.com/<username>/wearable-sensing-portfolio.git
cd wearable-sensing-portfolio
pip install pandas numpy matplotlib scipy jupyterlab
jupyter lab
```

Open any of the three `analysis.ipynb` notebooks and run all cells.

---

## What this portfolio demonstrates

- **End-to-end hardware → firmware → signal-processing pipeline** built on
  off-the-shelf parts (ESP32-S3, TEC1-12706, AD8232, DS18B20)
- **Three distinct sensing modalities** characterized under controlled protocols
- **Honest reporting of a failure mode** with root-cause analysis and a specific
  hardware fix proposed for the next iteration
- **Reproducibility-first practice**: raw data + version-controlled analysis + 
  pinned dependencies

---

## Application context

The longer-term goal is body-powered continuous vital-sign monitoring for
resource-limited clinical settings — specifically dengue patient monitoring at
district hospitals in Vietnam (OUCRU collaboration target). This portfolio
establishes the foundational measurement and characterization capability for the
hardware components that would constitute such a system.

---

## Contact

- Email: `nhu.nguyen.240109@student.fulbright.edu.vn` | 'npqnhu.work@gmail.com'
- LinkedIn: `www.linkedin.com/in/qnhuphnguyn`
- This repo: `https://github.com/npqnhu135/wearable-sensing-portfolio.git`

*Last updated: May 2026*

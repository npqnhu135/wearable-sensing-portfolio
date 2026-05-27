# Wearable Sensing Portfolio

**Nguyen Phan Quynh Nhu** — Human-Centered Engineering, Fulbright University Vietnam (Co28)
Building hardware + signal-processing for body-powered wearable health sensors.
*Preparing for PhD application Fall 2027.*

---

## Research direction

I'm building the measurement and signal-processing pipeline for body-powered,
ultra-low-power wearable health sensors — using off-the-shelf components today so
I can hit the ground running when I get into a proper materials lab.

The intended application is **dengue and febrile-illness vital-sign monitoring
in low-resource clinical settings**, in alignment with units such as OUCRU
Vietnam (Wellcome Trust-funded).

---

## Projects

### 1. Smart Vibrating Wristband Alarm
Project Lead, Design System Thinking course (Spring 2026, Prof. Kien Truong).
TPU/PLA flexible housing for rigid microcontroller, iterated through 12+ prototypes.
→ [01_smart_vibrating_wristband/](./01_smart_vibrating_wristband/)

### 2. Thermoelectric Body-Heat Harvesting *(active)*
Characterizing a TEC1-12706 module operated as a TEG with ESP32-S3 + DS18B20.
Three-phase graded heat stimulus reaching ΔT_max = 9.6°C above 33.6°C baseline.
→ [02_thermoelectric_body_harvesting/](./02_thermoelectric_body_harvesting/)

### 3. DIY Textile ECG Electrode *(active)*
Dry foil/foam electrode interfaced with AD8232, validated against Ag/AgCl gel
electrodes. Quantitative comparison against PhysioNet MIT-BIH reference in progress.
→ [03_diy_textile_ecg_electrode/](./03_diy_textile_ecg_electrode/)

### 4. AI-Powered Smart Load Management System
Top 5 finalist, NEXGen 2025 accelerator.
→ [04_smart_load_management/](./04_smart_load_management/)

---

## Technical stack

- **Hardware:** ESP32-S3 (YOLO:UNO), AD8232 ECG AFE, DS18B20, TEC1-12706, AD8232, breadboard rapid-prototype.
- **Firmware:** Arduino / PlatformIO (C/C++).
- **Signal processing & analysis:** Python — NumPy, SciPy, pandas, matplotlib, [wfdb](https://github.com/MIT-LCP/wfdb-python), [NeuroKit2](https://github.com/neuropsychology/NeuroKit).
- **Mech design / prototyping:** Fusion 360, 3D printing (PLA, TPU).
- **Coursework:** Sensors Measurement and Analysis · Electronics Devices and Circuits · Signals Systems and Control.

---

## Research summary (PDF)

[docs/RESEARCH_SUMMARY.pdf](./docs/RESEARCH_SUMMARY.pdf) — 4-page document explaining
motivation, methods, preliminary results, and trajectory toward PhD.

---

## Contact

- Email: `nhu.nguyen.240109@student.fulbright.edu.vn` or 'npqnhu.work@gmail.com'
- LinkedIn: www.linkedin.com/in/qnhuphnguyn
- YouTube demos: [link]

---

*Last updated: May 2026.*

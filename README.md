# 🕋 Smart Hajj Bracelet System | نظام سوار الحج الذكي

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Random%20Forest-green)
![IoT](https://img.shields.io/badge/IoT-ESP32%20%7C%20LoRaWAN-orange)
![Database](https://img.shields.io/badge/Database-SQL%20SQLite-lightgrey)
![Status](https://img.shields.io/badge/Status-Research%20Prototype-yellow)
![License](https://img.shields.io/badge/License-Academic-red)

**An AI-powered wearable system for Hajj pilgrim safety, health monitoring, and crowd management**

[🌐 Live Simulator](https://ai.studio/apps/af9e2f98-e442-4832-9e43-daaa30c1f79e) • [📄 Research Paper](#) • [📊 Dashboard Demo](#)

</div>

---

## 🏆 Key Results

| Metric | Value |
|--------|-------|
| ML Model Accuracy | **99.4%** |
| Emergency Recall | **92.8%** |
| Simulation Readings | **1,500 sensor records** |
| Emergency Alerts Detected | **49 / 49 (100%)** |
| Edge AI Inference Time | **< 3ms @ 42mW** |
| Datasets Used | **100,000+ real records** |

---

## 📌 Problem Statement

Every year, **2+ million pilgrims** from 180 countries perform Hajj under extreme heat (45°C+) across geographically constrained holy sites. The 2015 Mina stampede killed over 2,400 people. Current systems (Nusuk Smart Card) only provide NFC identification — no health monitoring, no AI prediction, no crowd alerts.

**This system addresses all five critical gaps simultaneously.**

---

## ✨ System Features

- 🤖 **AI Risk Prediction** — Random Forest classifier (99.4% accuracy) running on Edge AI
- 💓 **Real-time Health Monitoring** — Heart rate, SpO2, body temperature via MAX30102
- 👥 **Crowd Management** — Density detection + AI-optimized rerouting (Dijkstra)
- 📡 **3-Tier Communication** — 4G → BLE Mesh → LoRaWAN (works without internet)
- ♿ **Full Accessibility** — Audio (Arabic + English), haptic, LED for deaf/visually impaired
- 🔐 **Cybersecurity** — SHA-256 hashing + AES-256 encryption
- 🗄️ **SQL Database** — 5 tables, real-time simulation, live dashboard
- 🔋 **5-Day Battery** — LiPo 500mAh + flexible solar film + duty cycling

---

## 🏗️ System Architecture

```
Smart Bracelet (ESP32 + Sensors)
        │
        ├── Tier 1: 4G/5G via smartphone gateway
        ├── Tier 2: BLE 5.0 Mesh (peer-to-peer)
        └── Tier 3: LoRaWAN SOS (no internet needed)
                │
                ▼
    ┌───────────────────────────┐
    │   Cloud / SQL Database    │
    └───────────────────────────┘
        │           │           │
   Group Leader  Emergency   Ministry
   Dashboard     Center      Dashboard
```

---

## 🛠️ Hardware Components

| Component | Model | Purpose |
|-----------|-------|---------|
| Microcontroller | ESP32 | Edge AI + BLE 5.0 + Wi-Fi |
| PPG Sensor | MAX30102 | Heart rate + SpO2 |
| IMU | MPU-6050 | Fall detection |
| GPS | u-blox M8N | Location tracking |
| LoRa Radio | SX1276 | Emergency SOS offline |
| Display | 1.54" E-ink | Zero-power status display |

---

## 🧠 Machine Learning Model

- **Algorithm:** Random Forest (n=300 trees, max_depth=15)
- **Training Data:** 100,000+ real records from 3 Kaggle/Google datasets
- **Classes:** Emergency / Warning / Safe
- **Edge Deployment:** Converted to C++ via `micromlgen` → ESP32 firmware (48KB)

### Performance

```
              precision    recall   f1-score
Emergency       98.4%      92.8%     95.5%
Warning         99.4%      99.8%     99.6%
Safe           100.0%     100.0%    100.0%
Overall Accuracy: 99.4%
```

---

## 🗄️ Database Schema

```sql
Pilgrims        (Passport_Hash, Name, Nationality, Blood_Type, Special_Needs)
Sensor_Readings (Reading_ID, Pilgrim_Hash, HR, SpO2, Temp, GPS, Risk_Level)
Alerts_Log      (Alert_ID, Pilgrim_Hash, Severity, Timestamp, Resolved)
Campaign_Groups (Campaign_ID, Leader_Name, Phone, Total_Pilgrims)
Services_GIS    (Service_ID, Type, GPS_Coordinates, Capacity)
```

---

## 📁 Repository Structure

```
hajj-smart-bracelet/
│
├── 📓 notebooks/
│   ├── 01_data_analysis.ipynb        # EDA + visualizations
│   ├── 02_feature_engineering.ipynb  # Feature creation
│   ├── 03_ml_model.ipynb             # Random Forest training
│   ├── 04_simulation.ipynb           # 1,500 readings simulation
│   └── 05_dashboard.ipynb            # Live SQL dashboard
│
├── 📊 data/
│   └── datasets_info.md              # Dataset sources + links
│
├── 📄 research/
│   └── Hajj_Smart_Bracelet_Paper.pdf # Full research paper
│
├── 🎮 simulator/
│   └── link.md                       # Google AI Studio simulator link
│
└── README.md
```

---

## 🚀 Quick Start

### Run in Google Colab

```python
# Clone and open any notebook directly in Colab
# 1. Go to colab.research.google.com
# 2. File → Open notebook → GitHub tab
# 3. Paste this repo URL
```

### Required Libraries

```python
pip install pandas numpy scikit-learn matplotlib seaborn sqlite3 micromlgen
```

---

## 📊 Datasets Used

| Dataset | Source | Records |
|---------|--------|---------|
| Hajj & Umrah Crowd Management | Kaggle | 10,000 |
| Wearable Sensor Health Monitor | Google Dataset Search | 60,000 |
| IoT Patient Monitoring | Google Dataset Search | 30,000 |

---

## 🌐 Live Demo

👉 **[Interactive Simulator on Google AI Studio](https://ai.studio/apps/af9e2f98-e442-4832-9e43-daaa30c1f79e)**

The simulator includes:
- Smart Bracelet with 4 health scenarios
- Group Leader Dashboard (50 pilgrims)
- Central Command & Control Room
- Technical Architecture viewer

---

[📄 Research Paper](https://github.com/rawanmekky024-bot/hajj-smart-bracelet/blob/main/Hajj_FINAL_Rawan_Mekky%202026%20Project%20Diploma%20.pdf)

**"An AI-Powered Smart Bracelet System for Hajj Pilgrim Safety, Health Monitoring, and Crowd Management"**

- **Author:** Rawan Nasser Abd Elmoneam Mekky
- **Supervisor:** Dr. Mahmoud Shams
- **Institution:** Faculty of Artificial Intelligence, Kafrelsheikh University
- **Year:** 2026
- **Target Journal:** MDPI Sensors (Q1)

---

## 🔮 Future Work

- [ ] Hardware prototype (ESP32 + MAX30102 + u-blox GPS)
- [ ] LSTM upgrade for 20+ minute advance warning
- [ ] CNN crowd density from overhead cameras
- [ ] Multilingual NLP (Arabic, Urdu, Indonesian, Turkish, Farsi)
- [ ] Federated learning for privacy-preserving model updates
- [ ] Ministry of Hajj pilot program — Hajj 2027

---

## 👩‍💻 Author

**Rawan Nasser** | AI Diploma Student  
Faculty of Artificial Intelligence, Kafrelsheikh University  
Background: Al-Azhar University (Sharia) + Applied AI

---

## 📄 License

This project is for academic and research purposes.  
© 2026 Rawan Nasser — Kafrelsheikh University

---

<div align="center">
<i>Built to protect every pilgrim. لحماية كل حاج.</i>
</div>

# IoT-Enabled Marine Buoy Networking Simulation  

[![Python](https://img.shields.io/badge/Python-3.7%2B-blue.svg)](https://www.python.org/)  
[![IoT](https://img.shields.io/badge/IoT-Simulation-orange.svg)](#)  
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)  

A lightweight **simulation of networked marine buoys** equipped with IoT sensors for real-time environmental monitoring. The project demonstrates how distributed sensing, mesh communication, and basic analytics can transform how we study and protect marine ecosystems.  

> **Why it matters:** Showcases the potential of IoT and data pipelines in advancing environmental sustainability and smart monitoring solutions.  

---

## 🔧 Features  
- **Sensor simulation:** Temperature, turbidity, pH, salinity, and battery drain.  
- **Wireless mesh networking:** LoRa-like and Zigbee-like protocol presets (latency, RSSI, packet loss).  
- **Data pipeline:** Store results in SQLite and CSV, with basic anomaly detection (e.g., turbidity spikes, low battery).  
- **Dashboard:** Minimal Flask UI with REST API to view the latest readings.  
- **Reproducibility:** Seeded RNG ensures repeatable runs.  

---

## 📁 Project Structure  
```
marine-buoy-sim/
├─ README.md
├─ requirements.txt
├─ docker/
│  └─ Dockerfile
├─ data/out/                # SQLite + CSV outputs
├─ src/
│  ├─ common/               # Shared utilities
│  ├─ sensors/              # Buoy sensor models
│  ├─ network/              # Mesh + protocol simulation
│  ├─ pipeline/             # Storage + ingest pipeline
│  └─ dashboard/            # Flask dashboard
├─ tests/                   # Unit tests
└─ docs/                    # Diagrams, screenshots
```

---

## 🚀 Quickstart  

### 1) Install dependencies  
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### 2) Run a simulation  
```bash
python src/pipeline/run_simulation.py --nodes 8 --duration 600 \
  --protocol lora --out-dir data/out --seed 42
```
Outputs:  
- `data/out/marine.db` (SQLite database)  
- `data/out/readings.csv` (CSV of sensor data)  

### 3) Launch dashboard  
```bash
FLASK_APP=src/dashboard/app.py flask run
# open http://127.0.0.1:5000
```

---

## 🧠 How It Works  
1. **Buoy nodes** generate sensor readings at intervals.  
2. **Mesh network** adds realistic wireless behavior (delay, RSSI, packet loss).  
3. **Pipeline** persists data to SQLite and CSV, tagging anomalies.  
4. **Dashboard** provides a REST API + simple UI for monitoring.  

---

## 🧪 Tests  
```bash
pytest -q
```

---

## 🗺️ Roadmap  
- Add MQTT broker bridge.  
- Geospatial map overlay for buoy positions.  
- ML-based anomaly detection (coral bleaching, temperature outliers).  
- Docker Compose demo with simulation + dashboard.  

---

## 📚 Tech Stack  
- **Python 3.7+**  
- **Flask** for dashboard  
- **SimPy** for event-driven simulation  
- **SQLite + pandas** for storage/reporting  

---

## 📝 License  
This project is licensed under the **MIT License**. See [LICENSE](LICENSE).  

---

## 🙌 Acknowledgments  
- Inspired by IoT research in environmental monitoring.  
- Thanks to open-source simulation and data-science communities.  

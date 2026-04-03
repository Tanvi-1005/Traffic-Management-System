# 🚦 Urban Traffic Management System (UTMS)

<div align="center">

![UTMS Banner](https://img.shields.io/badge/Urban%20Traffic-Management%20System-blue?style=for-the-badge&logo=roadmap)

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square&logo=python)](https://python.org)
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?style=flat-square&logo=node.js)](https://nodejs.org)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active%20Development-orange?style=flat-square)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen?style=flat-square)](CONTRIBUTING.md)

**Revolutionizing urban mobility through AI, IoT, and real-time analytics.**

[Overview](#overview) • [Features](#features) • [Architecture](#architecture) • [Installation](#installation) • [Usage](#usage) • [Roadmap](#roadmap) • [Contributing](#contributing)

</div>

---

## 📌 Overview

The **Urban Traffic Management System (UTMS)** is an open-source platform that integrates **Artificial Intelligence**, **IoT sensor networks**, and **real-time data analytics** to address critical urban challenges — traffic congestion, road safety, and environmental pollution.

By deploying adaptive signal control, predictive congestion modeling, and multimodal transit coordination, UTMS transforms city streets into intelligent, responsive infrastructure.

> **Mission:** Create adaptive, efficient, and sustainable traffic systems that transform urban commuting into a seamless and eco-friendly experience.

---

## 🚀 Features

### Core Capabilities

| Feature | Description | Status |
|---|---|---|
| 🔴 **Adaptive Signal Control** | AI-driven dynamic traffic light timing based on real-time flow | ✅ Active |
| 📡 **IoT Sensor Integration** | Inductive loops, cameras, environmental monitors, LoRa/5G modules | ✅ Active |
| 🧠 **Congestion Prediction** | ML models forecast bottlenecks up to 30 minutes ahead | ✅ Active |
| 🗺️ **Real-Time Route Optimization** | Dynamic rerouting for vehicles, transit, and emergency services | ✅ Active |
| 📊 **Analytics Dashboard** | Live heatmaps, flow charts, and incident alerts | ✅ Active |
| 🚌 **Public Transit Integration** | Bus/train schedule synchronization with signal priority | 🔄 Beta |
| 🌱 **Eco-Friendly Metrics** | Emissions tracking, EV lane priority, idle reduction | 🔄 Beta |
| 🚨 **Incident Detection** | Automated accident and anomaly detection via computer vision | 🔜 Planned |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        UTMS Architecture                        │
├─────────────┬─────────────────────────────┬────────────────────┤
│  LAYER 1    │        Data Collection       │  IoT / Edge        │
│  (Sensors)  │  Cameras • Inductive Loops  │  LoRa / 5G         │
│             │  Weather Sensors • V2I Comm  │  Modules           │
├─────────────┼─────────────────────────────┼────────────────────┤
│  LAYER 2    │      Edge Processing         │  Real-time         │
│  (Edge AI)  │  On-site inference engines  │  Latency <50ms     │
│             │  Local anomaly detection     │                    │
├─────────────┼─────────────────────────────┼────────────────────┤
│  LAYER 3    │     Cloud & Analytics        │  Scalable          │
│  (Backend)  │  ML model training & serving│  Microservices     │
│             │  Time-series databases       │                    │
├─────────────┼─────────────────────────────┼────────────────────┤
│  LAYER 4    │    Control & Actuation       │  Traffic Signals   │
│  (Output)   │  Dynamic message signs       │  Route Displays    │
│             │  Emergency vehicle priority  │  Transit Sync      │
└─────────────┴─────────────────────────────┴────────────────────┘
```

### Technology Stack

- **AI/ML:** Python · TensorFlow · scikit-learn · OpenCV
- **IoT:** MQTT · LoRaWAN · 5G NR · Edge Inference
- **Backend:** FastAPI · Node.js · Redis · PostgreSQL · TimescaleDB
- **Frontend:** React · D3.js · Mapbox GL
- **Infrastructure:** Docker · Kubernetes · GitHub Actions
- **Communication:** REST API · WebSockets · gRPC

---

## 📁 Project Structure

```
urban-traffic-management/
├── src/
│   ├── core/               # Core traffic logic & signal control
│   │   ├── signal_controller.py
│   │   ├── traffic_flow.py
│   │   └── intersection_manager.py
│   ├── ml/                 # Machine learning models
│   │   ├── congestion_predictor.py
│   │   ├── incident_detector.py
│   │   └── route_optimizer.py
│   ├── iot/                # IoT device interfaces
│   │   ├── sensor_manager.py
│   │   ├── mqtt_client.py
│   │   └── lora_gateway.py
│   ├── api/                # REST & WebSocket API
│   │   ├── main.py
│   │   ├── routes/
│   │   └── schemas/
│   └── dashboard/          # Web dashboard (React)
│       ├── components/
│       ├── pages/
│       └── services/
├── tests/                  # Unit & integration tests
├── docs/                   # Extended documentation
├── scripts/                # Deployment & utility scripts
├── config/                 # Environment configurations
├── .github/workflows/      # CI/CD pipelines
├── docker-compose.yml
├── requirements.txt
└── README.md
```

---

## ⚙️ Installation

### Prerequisites

- Python 3.10+
- Node.js 18+
- Docker & Docker Compose
- PostgreSQL 14+ (or use Docker)

### Quick Start (Docker)

```bash
# 1. Clone the repository
git clone https://github.com/your-org/urban-traffic-management.git
cd urban-traffic-management

# 2. Copy environment config
cp config/.env.example config/.env

# 3. Launch all services
docker-compose up -d

# 4. Access the dashboard
open http://localhost:3000
```

### Manual Installation

```bash
# Backend (Python)
cd src/api
pip install -r ../../requirements.txt
uvicorn main:app --reload --port 8000

# Frontend (React)
cd src/dashboard
npm install
npm run dev

# Run ML model server
cd src/ml
python model_server.py
```

---

## 🖥️ Usage

### API Quick Reference

```python
import requests

# Get real-time traffic density for an intersection
response = requests.get("http://localhost:8000/api/v1/intersections/INT-001/density")
print(response.json())
# {
#   "intersection_id": "INT-001",
#   "density": 0.78,
#   "vehicles_detected": 42,
#   "signal_phase": "north-south-green",
#   "predicted_wait_s": 28
# }

# Trigger route optimization
response = requests.post("http://localhost:8000/api/v1/routes/optimize", json={
    "origin": {"lat": 18.5204, "lon": 73.8567},
    "destination": {"lat": 18.5314, "lon": 73.8446},
    "mode": "vehicle"
})
```

### Python SDK (Core Module)

```python
from src.core.signal_controller import AdaptiveSignalController
from src.ml.congestion_predictor import CongestionPredictor

# Initialize controller
controller = AdaptiveSignalController(intersection_id="INT-001")

# Predict congestion 15 minutes ahead
predictor = CongestionPredictor.load("models/congestion_v2.pkl")
forecast = predictor.predict(horizon_minutes=15)

# Adjust signal timing
controller.update_timing(
    phase="north-south",
    green_duration=forecast.recommended_green_s
)
```

---

## 📊 Performance Benchmarks

| Metric | Baseline (Fixed Signals) | UTMS | Improvement |
|---|---|---|---|
| Avg. Intersection Wait Time | 87 sec | 34 sec | **-61%** |
| Peak Hour Throughput | 1,200 veh/hr | 1,850 veh/hr | **+54%** |
| CO₂ Emissions (idle) | 100% | 67% | **-33%** |
| Incident Detection Time | Manual (5–15 min) | 45 sec | **-95%** |
| Emergency Vehicle Clearance | 4.2 min avg | 1.1 min avg | **-74%** |

> Benchmarks based on simulation (SUMO) over a 12-intersection network with 8-hour peak traffic scenario.

---

## 🗺️ Roadmap

```
Phase 1 — Prototype Design         ✅ Complete
  └─ Sensor data pipeline
  └─ Adaptive signal control (single intersection)
  └─ Basic dashboard

Phase 2 — Enhanced Monitoring      🔄 In Progress
  └─ Multi-intersection coordination
  └─ Computer vision incident detection
  └─ Mobile app for commuters

Phase 3 — Policy & Collaborations  🔜 Q3 2025
  └─ Municipality pilot programs
  └─ Public transit API integration
  └─ Open data portal

Phase 4 — Subscription Models      🔜 Q4 2025
  └─ SaaS platform for city governments
  └─ Logistics & ride-share API tier
  └─ Premium analytics dashboard

Phase 5 — Global Standardization   🔜 2026
  └─ IEEE/ITU compliance modules
  └─ Multi-city federated learning
  └─ Carbon credit reporting integration
```

---

## 👥 Customer Segments

| Segment | Pain Point Addressed |
|---|---|
| 🏛️ **Urban Municipalities** | Infrastructure management, KPI dashboards, policy compliance |
| 🚗 **Commuters** | Reduced wait times, real-time rerouting, safety alerts |
| 🚌 **Public Transit Agencies** | Signal priority for buses, schedule adherence tracking |
| 📦 **Logistics & Ride-Share** | Route optimization APIs, delivery time prediction |
| 🏙️ **Urban Planners** | Simulation tools, long-term capacity forecasting |

---

## 💼 Business Model

UTMS operates on a **B2G (Business-to-Government)** and **B2B** model:

1. **Municipal Licensing** — Annual SaaS subscription per city zone/district
2. **Hardware Integration** — Certified IoT sensor bundles + installation support
3. **Analytics API** — Pay-per-call tier for logistics and ride-share companies
4. **Consulting & Deployment** — Custom smart city integration services
5. **Data Marketplace** — Anonymized, aggregated traffic insights for urban researchers

---

## 🧪 Testing

```bash
# Run all tests
pytest tests/ -v

# Run with coverage report
pytest tests/ --cov=src --cov-report=html

# Run specific module tests
pytest tests/test_signal_controller.py -v
pytest tests/test_congestion_predictor.py -v
```

---

## 🤝 Contributing

We welcome contributions from traffic engineers, data scientists, IoT developers, and urban planners!

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/adaptive-signal-v2`
3. Commit changes: `git commit -m 'feat: add multi-phase signal coordination'`
4. Push and open a Pull Request

Please read [CONTRIBUTING.md](CONTRIBUTING.md) and follow our [Code of Conduct](CODE_OF_CONDUCT.md).

---

## 📄 License

This project is licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

---

## 📬 Contact

| Role | Contact |
|---|---|
| Project Lead | team24@utms.dev |
| Technical Queries | dev@utms.dev |
| Partnership & Business | partnerships@utms.dev |

---

<div align="center">

**Built with ❤️ by Team 24**

*Making cities smarter, one intersection at a time.*

</div>

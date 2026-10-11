# Project-Apex
Project Apex is an autonomous off-grid LoRa telemetry mesh. It uses 3 Heltec V3s running custom C++ firmware for multi-hop packet routing and sensors, wired to an 8GB Raspberry Pi 5 base station running a Python FastAPI dashboard and SQLite database. Built for rugged, solar-powered deployment.


---

## Bill of Materials 

| Item | Qty | Purpose & Justification |
| :--- | :---: | :--- |
| **Heltec V3 (ESP32 LoRa)** | **3** | Required for mesh testing (2 remote field nodes + 1 base coordinator). Minimum 3 nodes needed to evaluate multi-hop packet relaying and signal propagation. |
| **Raspberry Pi 5 (8GB)** | **1** | Acts as the edge base-station server running the MQTT broker, SQLite database, and FastAPI web dashboard backend. |
| **Solar Panels & MPPT Modules** | **2** | Provides autonomous, continuous off-grid power for the remote field nodes deployed outdoors. |
| **BME280 Sensor Module** | **2** | Precision temperature, humidity, and atmospheric pressure data acquisition for field nodes. |
| **Pinecil V2 Soldering Iron** | **1** | Portable USB-C soldering iron required for assembling and wiring custom power distribution and sensor harnesses. |

---

## Technical Implementation

### 1. Remote Field Nodes (Heltec V3)
* **Firmware:** Custom C++ built using ESP-IDF / Arduino IDE with **RadioLib** for low-level packet control.
* **Protocol:** Custom binary serialization protocol designed to compress telemetry payloads and minimize airtime.
* **Power Management:** Configured with deep-sleep duty cycles coupled with solar MPPT chargers for autonomous field operation.

### 2. Edge Gateway & Dashboard (Raspberry Pi 5)
* **Ingestion Pipeline:** Python-based daemon listening to serial/USB telemetry from the coordinator node.
* **Backend:** FastAPI server providing real-time data streaming via WebSockets and local SQLite storage.
* **Frontend/UI:** Local web dashboard visualizing node health, RSSI signal strength, and live environmental metrics.

---

## Development Roadmap

- [ ] **Phase 1:** Bench testing individual Heltec V3 modules and establishing raw serial communication.
- [ ] **Phase 2:** Developing custom C++ sensor reading and radio transmission firmware.
- [ ] **Phase 3:** Setting up the Raspberry Pi 5 Linux environment, Python ingestion pipeline, and SQLite database.
- [ ] **Phase 4:** Assembling weather-proof enclosures, integrating solar power systems, and field-testing multi-hop routing range.

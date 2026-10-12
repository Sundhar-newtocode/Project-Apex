# Project-Apex
Project Apex is an autonomous off-grid LoRa telemetry mesh. It uses 3 Heltec V3s running custom C++ firmware for multi-hop packet routing and sensors, wired to an 8GB Raspberry Pi 5 base station running a Python FastAPI dashboard and SQLite database. Built for rugged, solar-powered deployment.



---

##  Step-by-Step Assembly Guide

1. **Power Circuit Assembly:** Solder the solar panel output to the MPPT charger input module. Connect the battery terminal to the Heltec V3 power pins using JST connectors.
2. **Sensor Wiring:** Solder the BME280 sensor breakout pins to the Heltec V3 I2C pins (SDA/SCL) and 3.3V power rails using the Pinecil V2 soldering iron.
3. **Base Station Setup:** Connect the 3rd Heltec V3 module directly to the Raspberry Pi 5 USB 3.0 port via a USB-C data cable.
4. **Enclosure Mounting:** Mount the remote field nodes inside weather-resistant enclosures with solar panels angled upward.

---

##  Firmware Flashing Guide

1. Open **Arduino IDE** or **VS Code (PlatformIO / ESP-IDF)**.
2. Install the **ESP32 Board Package** (`v3.x.x`) and the **RadioLib** library.
3. Select board: **Heltec WiFi LoRa 32(V3)**.
4. Clone this repository and open `firmware/field_node/field_node.ino`.
5. Connect the Heltec V3 via USB, select the COM port, and click **Upload**.

---

##  Bill of Materials (BOM)

| Item | Qty | Justification | Link |
| :--- | :---: | :--- | :--- |
| **Heltec V3 (ESP32 LoRa)** | 3 | Required for mesh validation (2 remote field nodes + 1 base coordinator). | [Robu.in](https://robu.in/) |
| **Raspberry Pi 5 (8GB)** | 1 | Central edge gateway server running SQLite & FastAPI backend. | [Robu.in](https://robu.in/) |
| **Solar Panel & Charger** | 2 | Autonomous outdoor power for field nodes. | [Robu.in](https://robu.in/) |
| **BME280 Sensor Module** | 2 | Temperature, humidity, and barometric pressure acquisition. | [Robu.in](https://robu.in/) |
| **Pinecil V2 Soldering Iron** | 1 | Portable USB-C iron for custom wiring & harness assembly. | [Robu.in](https://robu.in/) |

*Full itemized breakdown available in [BOM.csv](./BOM.csv).*

---

##  Known Issues
- Deep-sleep wake-up cycles on the ESP32-S3 must be calibrated to allow the SX1262 LoRa radio chip sufficient warm-up time before transmission.

---

##  Credits & Acknowledgments
- **RadioLib** by jgromes for low-level SX1262 LoRa radio abstraction.
- **FastAPI** & **WebSockets** for real-time Python telemetry streaming.

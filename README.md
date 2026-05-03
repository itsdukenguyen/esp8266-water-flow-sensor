# ESP8266 G1" Water Flow Sensor for Home Assistant

<p align="center">
  <img src="https://via.placeholder.com/1200x300/007ACC/FFFFFF?text=ESP8266+Water+Flow+Sensor" alt="Project Banner" width="100%" />
</p>

[![ESPHome](https://img.shields.io/badge/ESPHome-2026.1.4-007ACC.svg)](https://esphome.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-ESP8266-000000.svg)](https://www.espressif.com)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2025+-41B1E5.svg)](https://www.home-assistant.io)

**Fully local DIY inline water flow meter** using a brass Hall-effect sensor. Provides accurate real-time flow rate in gal/min and tracks total + daily/monthly usage.

*(Real project photos coming soon)*

## Features
- Real-time flow rate in **gal/min**
- Cumulative total volume + automatic daily & monthly usage
- Leak detection when away
- High flow warning
- Daily usage summary
- Real-world calibration with 5-gallon bucket tests
- 100% local, encrypted API, OTA updates

## Hardware
See [`BOM.md`](BOM.md) for complete bill of materials and cost breakdown.

## Quick Start
1. Copy `water-flow-sensor.yaml` into ESPHome
2. Configure WiFi credentials using `secrets.yaml`
3. Flash to your NodeMCU ESP8266
4. Device auto-discovers in Home Assistant

## Documentation
- [`docs/calibration-log.md`](docs/calibration-log.md) — Test data and formula
- [`docs/automations.md`](docs/automations.md) — All Home Assistant automations
- [`water-flow-sensor.yaml`](water-flow-sensor.yaml) — Fully commented config

## License
[MIT License](LICENSE) © 2026 Duc Nguyen
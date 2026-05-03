# ESP8266 G1" Water Flow Sensor for Home Assistant

[![ESPHome](https://img.shields.io/badge/ESPHome-2026.1.4-007ACC.svg)](https://esphome.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-ESP8266-000000.svg)](https://www.espressif.com)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2025+-41B1E5.svg)](https://www.home-assistant.io)

**Fully local DIY inline water flow meter** built with a brass Hall-effect sensor. Accurate real-time flow rate in gal/min and cumulative usage tracking.

![Project Overview](assets/screenshots/installed.jpg)  
*(Photos coming soon)*

## Features
- Real-time flow rate (`gal/min`)
- Total volume + automatic daily/monthly usage
- Leak detection when away (already implemented)
- Calibrated with real 5-gallon bucket tests
- 100% local control, encrypted API, OTA updates

## Hardware
See [`BOM.md`](BOM.md) for full bill of materials and cost breakdown.

## Quick Start
1. Copy `water-flow-sensor.yaml` into ESPHome
2. Configure WiFi credentials (`secrets.yaml`)
3. Flash to NodeMCU ESP8266
4. Device auto-discovers in Home Assistant

## Documentation
- [`docs/calibration-log.md`](docs/calibration-log.md) — Test data & formula
- [`docs/automations.md`](docs/automations.md) — Live Home Assistant automations
- [`water-flow-sensor.yaml`](water-flow-sensor.yaml) — Fully commented config

## License
[MIT License](LICENSE) © 2026 Duc Nguyen
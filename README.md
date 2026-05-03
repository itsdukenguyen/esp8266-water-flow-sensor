# ESP8266 G1" Water Flow Sensor for Home Assistant

<p align="center">
  <img src="assets/banner.jpg" alt="ESP8266 Water Flow Sensor" width="100%" />
</p>

[![ESPHome](https://img.shields.io/badge/ESPHome-2026.1.4-007ACC.svg)](https://esphome.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-ESP8266-000000.svg)](https://www.espressif.com)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2025+-41B1E5.svg)](https://www.home-assistant.io)

**Fully local DIY inline water flow meter** using a brass Hall-effect sensor. Accurate real-time flow in gallons per minute with total, daily, and monthly tracking.

## Features
- Real-time flow rate (**gal/min**)
- Cumulative + automatic daily/monthly usage
- Leak detection when away
- High flow warning
- Daily usage summary (9 PM)
- Real-world 5-gallon bucket calibration
- Fully local, encrypted, OTA updates

## Hardware
See [`BOM.md`](BOM.md) for full bill of materials and pricing.

## Quick Start
1. Copy `water-flow-sensor.yaml` into ESPHome
2. Update WiFi secrets
3. Flash to NodeMCU ESP8266
4. Auto-discovers in Home Assistant

## Documentation
- [`docs/calibration-log.md`](docs/calibration-log.md) — Test results & formula
- [`docs/automations.md`](docs/automations.md) — All automations
- [`water-flow-sensor.yaml`](water-flow-sensor.yaml) — Commented config

## License
[MIT License](LICENSE) © 2026 Duc Nguyen
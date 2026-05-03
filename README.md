# ESP8266 G1" Water Flow Sensor for Home Assistant

[![ESPHome](https://img.shields.io/badge/ESPHome-2026.1.4-007ACC.svg)](https://esphome.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-ESP8266-000000.svg)](https://www.espressif.com)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2025+-41B1E5.svg)](https://www.home-assistant.io)

**Fully local DIY inline water flow meter** using a brass Hall-effect sensor. Measures flow rate in **gal/min** and tracks total + daily/monthly usage with real-world calibration.

*(Add real photos here soon)*

## Features
- Real-time flow rate (`gal/min`)
- Cumulative total volume + Daily & Monthly usage (via `utility_meter`)
- Leak detection automation (when away)
- Calibrated using multiple 5-gallon bucket tests
- 100% local, encrypted, OTA updates

## Hardware
See [`BOM.md`](BOM.md)

## Quick Start
1. Copy `water-flow-sensor.yaml` to ESPHome
2. Update WiFi in `secrets.yaml`
3. Flash to NodeMCU ESP8266
4. Auto-discovers in Home Assistant

## Calibration
Tested with 5-gallon bucket.  
**Formula**: `Q (L/min) = (Hz + 4) / 8` → converted to gallons.

## Home Assistant Integration
- Entities: `sensor.water_flow_rate`, `sensor.total_water_volume`, `sensor.daily_water_usage`
- Utility meters for daily & monthly tracking
- See [`docs/automations.md`](docs/automations.md) for real automations used in this system

## Repository Structure
(Your current structure is good — no change needed)
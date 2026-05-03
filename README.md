# ESP8266 G1" Water Flow Sensor for Home Assistant

[![ESPHome](https://img.shields.io/badge/ESPHome-2026.1.4-007ACC.svg)](https://esphome.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2025.1+-41B1E5.svg)](https://www.home-assistant.io)

**DIY inline water flow meter** using a brass Hall-effect sensor. Fully local, privacy-focused, and accurate after calibration.

![Installed Sensor](assets/screenshots/installed.jpg)
![HA Dashboard](assets/screenshots/dashboard.png)

## Features
- Real-time flow rate (`gal/min`)
- Total volume + Daily usage tracking
- Ready for leak detection automations
- Pulse metering with calibrated conversion
- OTA updates & encrypted API

## Hardware
See [`BOM.md`](BOM.md)

## Installation
1. Copy `water-flow-sensor.yaml` into ESPHome
2. Edit WiFi & API secrets
3. Flash to NodeMCU
4. Add to Home Assistant (auto-discovered)

## Calibration
Tested with 5-gallon bucket. Formula:  
`Q (L/min) = (Hz + 4) / 8` → converted to gallons.

## Repository Structure
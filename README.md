\# ESP8266 + G1" Brass Hall Effect Water Flow Sensor



DIY water flow meter integrated with \*\*Home Assistant\*\* via \*\*ESPHome\*\*. Monitors flow rate (gal/min) and total volume (gallons) with full local control.



!\[Water Flow Sensor Installed](images/installed.jpg)

!\[Wiring](images/wiring.jpg)



\## Features

\- Real-time flow rate in gallons per minute

\- Cumulative and daily water usage

\- Leak detection ready (via HA automations)

\- Fully local, privacy-focused, no cloud

\- Calibrated for real-world accuracy



\## Hardware

\- \*\*MCU\*\*: NodeMCU ESP8266 (nodemcuv2)

\- \*\*Sensor\*\*: G1" Male Thread Brass Hall Effect Water Flow Sensor (2-50 L/min)

\- \*\*Adapters\*\*: Cascada 1" G to NPT + Sharkbite MNPT

\- \*\*Pin\*\*: GPIO4 (with internal pull-up)



\## Calibration

Tested with 5-gallon bucket. Final formula used:  

\*\*Q (L/min) = (Hz + 4) / 8\*\* → converted to gal/min.



\## Getting Started

1\. Clone this repo

2\. Copy `water-flow-sensor.yaml` into ESPHome

3\. Flash to your NodeMCU

4\. Add to Home Assistant (auto-discovered)



\## Files

\- `water-flow-sensor.yaml` — Complete ESPHome configuration

\- `BOM.md` — Bill of Materials

\- `docs/` — Additional notes \& automations



\## License

MIT - feel free to use and modify!


# Water Flow Sensor Calibration Log

## Test Setup
- **Sensor**: G1" Brass Hall Effect Water Flow Sensor (2-50 L/min)
- **MCU**: NodeMCU ESP8266 (GPIO4)
- **Method**: Filled a 5-gallon bucket from kitchen sink
- **Date**: Multiple tests performed in April/May 2026
- **Goal**: Determine accurate pulses-to-gallons conversion and validate formula

## Raw Test Data (Arduino Sketch)

**One representative 5-gallon test** (approx. 2:45 duration, ~1.8–2.5 gal/min):

- Total pulses recorded: **~5,487** for ~5.03 gallons
- **Empirical calibration**: **~1,090 pulses per gallon**
- Average flow during steady state: ~2.0–2.4 gal/min
- Frequency range: 48–73 Hz

### Key Observations
- Early fill (higher pressure): Higher Hz (~60-73)
- End of fill (tap closing): Dropped to ~48-51 Hz
- No major noise or missed pulses with 50ms internal filter
- Manufacturer-style formula `(Hz + 4) / 8` performed well after adjustment from initial `/7.5`

## Final ESPHome Configuration Used

**Formula in production**:
```cpp
float hz = pulses_min / 60.0;
float l_min = (hz + 4.0) / 8.0;
float gal_min = l_min / 3.78541;
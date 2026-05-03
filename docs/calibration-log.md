# Calibration Log

**Project:** ESP8266 G1" Water Flow Sensor  
**Status:** Production Ready

## Test Methodology
- Filled a standard **5-gallon bucket** from kitchen sink
- Multiple tests performed in April–May 2026
- Used Arduino sketch for initial pulse validation
- Final validation in ESPHome

## Key Results

| Test | Duration | Pulses | Measured Volume | Avg Flow Rate | Notes |
|------|----------|--------|-----------------|---------------|-------|
| 5-Gallon Bucket | ~2:45 | ~5,487 | 5.03 gal | ~1.82 gal/min | Steady flow, good match |

**Empirical Factor:** **~1,090 pulses per gallon**

## Final Formula Used (ESPHome)

```cpp
float hz = pulses_min / 60.0;
float l_min = (hz + 4.0) / 8.0;        // Calibrated from real tests
float gal_min = l_min / 3.78541;
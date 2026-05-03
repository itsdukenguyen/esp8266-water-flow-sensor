# Home Assistant Automations

**Part of the ESP8266 Water Flow Sensor Project**

## Active Automations in This System

### Water Leak Alert When Away

```yaml
- id: water_leak_alert_duc_away
  alias: Water Leak Alert When Away
  description: Notify if water is flowing while away (possible major leak)
  trigger:
    - platform: numeric_state
      entity_id: sensor.water_flow_sensor_water_flow_rate
      above: 0.1
      for:
        minutes: 5
  condition:
    - condition: state
      entity_id: device_tracker.pixel_9_pro_xl
      state: "not_home"
  action:
    - service: notify.mobile_app_pixel_9_pro_xl
      data:
        title: "🚨 Possible Water Leak!"
        message: "Water is flowing at {{ states('sensor.water_flow_sensor_water_flow_rate') | round(2) }} gal/min while you're away."
  mode: single
  
  
utility_meter:
  water_daily_usage:
    source: sensor.water_flow_sensor_total_water_volume
    name: Water Daily Usage
    cycle: daily
  water_monthly_usage:
    source: sensor.water_flow_sensor_total_water_volume
    name: Water Monthly Usage
    cycle: monthly
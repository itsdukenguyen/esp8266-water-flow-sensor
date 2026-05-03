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
	
	
- id: water_high_flow_warning
  alias: "Water - High Flow Warning"
  description: Alert if unusually high water flow is detected (possible burst pipe or open faucet)
  trigger:
    - platform: numeric_state
      entity_id: sensor.water_flow_sensor_water_flow_rate
      above: 8.0                    # Adjust based on your normal max flow
      for:
        seconds: 30
  condition:
    - condition: state
      entity_id: input_boolean.water_leak_cooldown
      state: "off"
  action:
    - service: notify.mobile_app_pixel_9_pro_xl
      data:
        title: "⚠️ High Water Flow Detected"
        message: "Water is flowing at {{ states('sensor.water_flow_sensor_water_flow_rate') | round(2) }} gal/min. Possible issue."
        data:
          tag: water_high_flow
          group: water_alerts
    - service: system_log.write
      data:
        message: "High water flow warning triggered: {{ states('sensor.water_flow_sensor_water_flow_rate') }} gal/min"
        level: warning
    - service: input_boolean.turn_on
      target:
        entity_id: input_boolean.water_leak_cooldown
  mode: single
  
  
- id: water_daily_usage_summary
  alias: "Water - Daily Usage Summary"
  description: Send daily water usage report at 9:00 PM
  trigger:
    - platform: time
      at: "21:00:00"
  action:
    - service: notify.mobile_app_pixel_9_pro_xl
      data:
        title: "💧 Daily Water Usage Report"
        message: >-
          You used {{ states('sensor.water_daily_usage') | round(1) }} gallons today.
          
          Total usage this month: {{ states('sensor.water_monthly_usage') | round(0) }} gallons.
        data:
          tag: water_daily_summary
          group: water_reports
    - service: system_log.write
      data:
        message: "Daily water usage summary sent: {{ states('sensor.water_daily_usage') }} gal"
        level: info
  mode: single
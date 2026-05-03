# Water Flow Sensor Automations (From Live HA System)

## 1. Water Leak Alert When Away (Active in Your System)

```yaml
- id: water_leak_alert_duc_away
  alias: Water Leak Alert When Away
  description: Notify if water is flowing while Duc is away (possible leak)
  triggers:
    - entity_id: sensor.water_flow_sensor_water_flow_rate
      above: 0.1
      for:
        minutes: 5
      trigger: numeric_state
  conditions:
    - condition: state
      entity_id: device_tracker.pixel_9_pro_xl
      state: not_home
  actions:
    - data:
        title: Possible Water Leak!
        message: Water is flowing ({{ states('sensor.water_flow_sensor_water_flow_rate') | round(2) }} gal/min) while you're away. Check for leaks!
      action: notify.mobile_app_pixel_9_pro_xl
  mode: single
  
  
  utility_meter:
  water_daily_usage:
    source: sensor.water_flow_sensor_total_water_volume
    name: Water Daily Usage
    cycle: daily
    delta_values: false
  water_monthly_usage:
    source: sensor.water_flow_sensor_total_water_volume
    name: Water Monthly Usage
    cycle: monthly
    delta_values: false
	
	
- alias: "High Water Flow Warning"
  trigger:
    - platform: numeric_state
      entity_id: sensor.water_flow_sensor_water_flow_rate
      above: 8.0
      for: seconds: 30
  action:
    - service: notify.mobile_app_pixel_9_pro_xl
      data:
        title: "High Water Flow"
        message: "Water flowing at {{ states('sensor.water_flow_sensor_water_flow_rate') }} gal/min"
		
		
- alias: "Daily Water Usage Report"
  trigger:
    - platform: time
      at: "21:00:00"
  action:
    - service: notify.mobile_app_pixel_9_pro_xl
      data:
        title: "💧 Daily Water Usage"
        message: "You used {{ states('sensor.water_daily_usage') | round(1) }} gallons today."
		
		
influxdb:
  include:
    entity_globs:
      - sensor.*water*
      - sensor.*flow*
# OpenTherm Thermostat.

![image](https://github.com/diyless/opentherm-thermostat/assets/61807075/37594781-d49c-4a24-8407-881a1ee3e0e9)

This repository is for a feedback on using our OpenTherm Thermostat.

Here you can request a new feature or report an issue(s) experienced while using our Thermostats.

## Original Firmware

If you have experimented with your thermostat, i.e. set up the wrong settings or loaded a custom firmware - you can restore the original one using our [web flasher](https://diyless.com/flasher).
You would not need an activation code if you use it with an original ESP32 bought from us in the thermostat bundle.


# Firmware Versions

## v2.1 (in progress)
### bugfixes

- CH schedule not working
- CH schedule payload and enable now are independent properties
- BLE connected mode - fixed battery percentage
- BLE connected mode - timeout reduced to 4 minutes
- Heating Action - take into account CHActive OpenTherm flag

### changes

- state json properties rename
  - CHWaterPressure -> CHPressure
  - ReturnWaterTemperature -> CHRetTemp
  - OutsideTemperature -> OutsideTemp
  - ExhaustTemperature -> ExhaustTemp
- availability topic changed: *~/tele/LWT* -> *~/avail* (single topic / message for all entities)
- availability properties for BLE / OT / MQTT / Internal sensors

### improvements / new features

- HA autodiscovery - device unique id added
- HA autodiscovery - diagnostics sensors added
- CH Boiler Limit / Boiler Max properties (and sensors) added
- OpenTherm messages log to the mqtt (_~/otlog_)
- Initial REST API implementation (_/api/set_ endpoint), accepts JSON payload. Currently allows setting the room temperature (_roomTemp_ property)

<details>
  <summary> list of autodiscoverable sensors </summary>

  - Flame Level
  - Flame State
  - CH Temperature
  - CH Setpoint
  - CH State
  - CH Boiler Temp Limit
  - CH Boiler Max Temp
  - CH Water Pressure
  - CH Return Temperature
  - DHW State
  - DHW Temperature
  - DHW Temperature2
  - Outdoor Temperature
  - Exhaust Temperature
  - Diagnostic
  - Fault
  - Fault Code
  - OpenTherm Connection State
  - PI factor I

  - MQTT Sensor Temperature
  - MQTT Sensor Connection State
  - MQTT Sensor State
  - MQTT Sensor Last Seen

  - Internal Sensor Temperature
  - Internal Sensor Connection State
  - Internal Sensor State

  - WiFi RSSI
  
  - BLE Battery
  - BLE Battery Voltage
  - BLE RSSI
  - BLE Loss Rate
  - BLE Last Seen
  - BLE Temperature
  - BLE Humidity
</details>

## v2.2 (planned)

### improvements / new features
- Equithermic regulation (weather dependent)
- Constant boiler temperature with hysteresis
- offscreen first touch event changes settings
  

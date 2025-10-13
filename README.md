# OpenTherm Thermostat.

![image](https://github.com/diyless/opentherm-thermostat/assets/61807075/37594781-d49c-4a24-8407-881a1ee3e0e9)

This repository is for a feedback on using our OpenTherm Thermostat.

Here you can request a new feature or report an issue(s) experienced while using our Thermostats.

## Original Firmware

If you have experimented with your thermostat, i.e. set up the wrong settings or loaded a custom firmware - you can restore the original one using our [web flasher](https://diyless.com/flasher).
You would not need an activation code if you use it with an original ESP32 bought from us in the thermostat bundle.


# Firmware Versions

## v2.1 (2024.12.09)
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

## v2.2 (2025.01.25)

### bugfixes
- JSON messages corruption (invalid properties values)
- Thermostat2/3 model name as Thermostat 1 within HA autodiscovery

### improvements / new features
- Equithermic regulation with hysteresis (weather dependent)
- Constant temp regulation with hysteresis (manually controlled boiler temperature)
- Outside temperature sources: diyless (using weatherapi), weatherapi, openweathermap
- sensors offset config
- room setpoint min/max config
- configurable room setpoint step
- HA sensors for outside temperature sources

## v2.2.1 (2025.08.11) Thermostat3 only

### bugfixes
- External (DS18B20) sensor not working as a room temperature source

## v2.2.2 (WIP)

### bugfixes
- External mqtt sensor not working

### improvements
- 'Publish a temperature value to the _topic_name_...' hint improved to show full topic name

## v2.3 (WIP)

### bugfixes
- T3: first touch event on sleeping screen changes settings

### improvements / new features
- DHW schedule
- kiosk mode
- Configurable HA discovery prefix

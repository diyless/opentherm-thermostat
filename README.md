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

## v2.2.2 (2025.10.24)

### bugfixes

- External mqtt sensor not working ([#21](https://github.com/diyless/opentherm-thermostat/issues/21))
- Relative modulation level command change ([12](https://github.com/diyless/opentherm-thermostat3/issues/12))

### improvements / new features

- 'Publish a temperature value to the _topic_name_...' hint improved to show full topic name (for mqtt / external mqtt sensors) ([#27](https://github.com/diyless/opentherm-thermostat/issues/27#issuecomment-3396450928))
- display MQTT state & control (T2 / T3) ([#4](https://github.com/diyless/opentherm-thermostat/issues/4))
- uptime HA sensor ([#17](https://github.com/diyless/home-assistant-opentherm-thermostat/issues/17))
- config backup / restore ([#24](https://github.com/diyless/opentherm-thermostat/issues/24))
- ambient light sensor HA entity (T3)
- system page wifi rssi / ot stats display

## v2.2.3 (2026.03.19)

### bugfixes

- display off button turns the screen on (if screen off timeout set to zero) ([#4](https://github.com/diyless/opentherm-thermostat/issues/4#issuecomment-3448414717))
- HA logs flood because of a missing property in JSON ([#24](https://github.com/diyless/opentherm-thermostat3/issues/24))
- CHMin + Curve combination does not work ([#29](https://github.com/diyless/opentherm-thermostat/issues/29))
- ntp server typo fix ([#23 comment](https://github.com/diyless/opentherm-thermostat/issues/23#issuecomment-3474330509))

### improvements / new features

- websocket scheme selector based on location.protocol (thermostat behind reverse proxy with SSL)

## v3.0.0 (2026.09.19)

### bugfixes

- Filter invalid OneWire / DS18B20 temperature spikes ([T1#62](https://github.com/diyless/opentherm-thermostat/issues/62), [T1#19](https://github.com/diyless/opentherm-thermostat/issues/19))
- False OpenTherm disconnections ([T3#32](https://github.com/diyless/opentherm-thermostat3/issues/32))
- Boiler kept heating during a long OpenTherm connection loss ([T3#27](https://github.com/diyless/opentherm-thermostat3/issues/27), [T1#20](https://github.com/diyless/opentherm-thermostat/issues/20))
- Invalid outside / external sensor temperature (4095.938) reported when the sensor is absent ([T1#35](https://github.com/diyless/opentherm-thermostat/issues/35))
- Web UI and MQTT stop responding after editing a schedule / on large schedules ([T3#35](https://github.com/diyless/opentherm-thermostat3/issues/35), [T1#54](https://github.com/diyless/opentherm-thermostat/issues/54))
- Firmware reverted to the previous version after restart ([T3#39](https://github.com/diyless/opentherm-thermostat3/issues/39))
- HA logs flood because of missing properties in JSON ([T1#70](https://github.com/diyless/opentherm-thermostat/issues/70))
- Connection to the diyless broker even when both telemetry and remote control are disabled ([T3#40](https://github.com/diyless/opentherm-thermostat3/issues/40))
- WiFi / network stability improvements ([T1#44](https://github.com/diyless/opentherm-thermostat/issues/44))
- Two simultaneous secure MQTT connections (own HA broker + diyless broker) now work reliably
- Settings could stop being saved until the next restart
- Schedule skipped the current time slot after a restart / power cut / time zone change
- DHW setpoint is now limited to the range reported by the boiler
- Large MQTT messages were dropped
- Invalid numeric values in web / MQTT / weather / schedule input are rejected (float conversion and JSON validation errors)
- T3: OneWire sensor state fix and Home Assistant entity ([T1#62](https://github.com/diyless/opentherm-thermostat/issues/62))
- T3: BLE sensor unavailable in Home Assistant ([T3#10](https://github.com/diyless/opentherm-thermostat3/issues/10))
- T3: WiFi networks list on the display limited to 7 entries ([T3#20](https://github.com/diyless/opentherm-thermostat3/issues/20))
- T3: Schedule usage via display UI bugfix ([T3#35](https://github.com/diyless/opentherm-thermostat3/issues/35))
- T3: Keep schedule state always available
- T3: built-in sensor occasional hang / wrong readings

### improvements / new features

- Time support: time status, NTP via DHCP ([T1#23](https://github.com/diyless/opentherm-thermostat/issues/23), [T3#33](https://github.com/diyless/opentherm-thermostat3/issues/33))
- Enable/disable the heating schedule from Home Assistant ([T1#3](https://github.com/diyless/opentherm-thermostat/issues/3))
- Remote control preview
- MQTT connection error display

## Planned

- DHW schedule
- kiosk mode
- Configurable HA discovery prefix
- T3: first touch event on sleeping screen changes settings

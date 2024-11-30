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

- CH schedule  not working
- CH schedule payload and enable now are independent properties
- BLE connected mode - fixed battery percentage
- BLE connected mode - timeout reduced to 4 minutes

### changes

- state json properties rename
  - CHWaterPressure -> CHPressure
  - ReturnWaterTemperature -> CHRetTemp
  - OutsideTemperature -> OutsideTemp
  - ExhaustTemperature -> ExhaustTemp
- availability topic changed: *~/tele/LWT* -> *~/tele/climate*
- availability topics for BLE / OT sensors: *~/tele/ble*, *~/tele/ot*

### improvements / new features

- HA autodiscovery - device unique id added
- HA autodiscovery - diagnostics sensors added
- CH Boiler Limit / Boiler Max properties (and sensors) added 

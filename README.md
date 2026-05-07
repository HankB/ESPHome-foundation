# ESPHome-foundation

Starting point for ESPHome projects.

## Motivation and purpose

Previous ESP8266/ESP32 projects have suffered from issues. This project is intended to provide a starting point for other projects and which adhere to the policies established by those projects. Unless following the established pattern proves too difficult for the benefit achieved. The existing project:

* Publishes sensor readings to an MQTT broker to which HomeAssistant subscribes.
* Publishes sensor readings at fixed intervals, typically 1/min. Some sensors such as presence or push-buttons publish when events happen.
* Publishes using predetermined topics which are `HA/[hostname]/[location]/[identifier]`
* Payloads are formatted as JSON and include a timestamp, sensor ID, sensore reading(s) and any additional "useful" information.

```text
HA/brandywine/garage/freezer_temp {"t":1778127784, "temp":7.25, "device":"DS18B20", "DS18B20_ID":"28-0000005815e0"}
```

The intent of this foundation is to include:

* MQTT to support publishing.
* NTP/SNTP to provide time stamps.
* Wifi - of course!

This initial project is not intended to directly support HomeAssistant.

## Status

* 2026-05-07 Blink LED
* 2026-05-06 Add MQTT, disable Home Assistant API

## 2026-05-06 Setup

Initial install in a Python virtual environment is:

```text
python3 --version
pushd ~/esp
python3 -m venv venv
source venv/bin/activate
pip3 install esphome
esphome version
```

```text
(venv) hbarta@olive:~/esp$ esphome version
Version: 2026.4.5
(venv) hbarta@olive:~/esp$ 
```

ESPHome has been installed in `~/ESP/venv` and can be started by typing:

```text
source ~/esp/venv/bin/activate
esphome version
```

## 2026-05-06 project creation

```text
esphome wizard ESPHome-foundation.yaml # first run
esphome run ESPHome-foundation.yaml # Subsequent runs
```

## Errata

* 2026-05-07 ESPHome seems not to provide a templating option for setting hostname. For example it would be useful to have something like "[family]-[MAC-3]" that wouild expand to something like `ESP32-B9ACE8` where the device's MAC address is `08:3A:F2:B9:AC:E8`. there is a "substitute capacity" that allows to define the name once and use it myltiple times.
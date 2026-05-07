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

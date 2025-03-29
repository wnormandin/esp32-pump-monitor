# esp32-pump-monitor

This is a project put together to manage a wildlife-serving fountain and weather station.  The entire thing is solar-
powered with a rechargable Li+ battery.

The ESP32 in this case is a microcontroller monitoring the power to send notifications if the solar array cannot keep up
with the battery drain and I need to connect a charger.  It does some other things too.

1. Manages the speed of the 12vdc water pump feeding the fountain - duty cycle is limited at night and when low power
2. Monitors temperature and humidity
3. Monitors battery charge and solar charging efficiency
4. Posts statistics to a RESTful API service on a local network for metrics gathering (and in my case, grafana dashboards)
5. Manages ESP32 state according to duty cycle, leveraging lightsleep/deepsleep routines to conserve power
6. Connects to home WiFi for remote management via MicroPython WebREPL

I'll keep extending the functionality if power demands permit.  The Battery unit in this project has its own built-in
over/under-charge protection circuit, so the ESP32's primary purpose is to monitor performance/environment and conserve
power by reducing the pump activity during certain conditions.

## Monitor Service
Lorem ipsum...

### Service Configuration
Lorem ipsum...

## Monitor Client
Lorem ipsum...

### Client Configuration
Lorem ipsum...

## Deployment to ESP-WROOM-32 Boards
Lorem ipsum...

# Project Component List

| Item                  | Count | Datasheet / Link                        | Specs                  | Notes                                                         |
|-----------------------|-------|-----------------------------------------|------------------------|---------------------------------------------------------------|
| ESP-WROOM-32          | 1     | [PDF Datasheet][1]                      |                        | WiFi-enabled ESP32 microcontroller                            |
| MicroPython Binary    | 1     | [ESP32_GENERIC-20241129-v1.24.1.bin][2] | ESP32-compatible       | MicroPython binary deployed to the client devices             |
| Solar Panel           | 2     | [Zealife Deer Feeder Solar Panel][3]    | 8"x4", 6.3v, 1.5W      | Using 2 of these to meet the 12v battery level                |
| Lithium Ion Battery   | 1     | [TalentCell Li+ Battery Pack][4]        | 12v 3A (max), 33.3 Wh  | This unit has built-in over/under-charge prevention           |
| Solderable Breadboard | 1     |                                         |                        | Will go SMD someday                                           |
| Switch Drive Module   | 1     | [EPZLON MOSFET Switch Driver][5]        | 12v-50v, 3.3-5v signal | Fancy pwm-controlled mosfet switch for the pump               |
| Voltage Regulator     | 1     | [12v-to-3v DC Voltage Regulator][6]     | 12v-to-3.3v            | Step down power supply for the ESP32 and low-power components |
| 12v submersible pump  | 1     | [12v Submersible Water Pump][7]         | 12v / 4.8W             |                                                               |
|                       |       |                                         |                        |                                                               |


[1]: <https://esp32.com/download/file.php?id=1717> "PDF Datasheet for the ESP32"
[2]: <https://micropython.org/resources/firmware/ESP32_GENERIC-20241129-v1.24.1.bin> "ESP32_GENERIC-20241129-v1.24.1.bin"
[3]: <https://www.ebay.com/itm/267167934999?mkcid=16&mkevt=1&mkrid=711-127632-2357-0&ssspo=h_CTBC6iSpa&sssrc=2047675&ssuid=&widget_ver=artemis&media=COPY> "Zealife Deer Feeder 6v Solar Panel"
[4]: <https://www.talentcell.com/lithium-ion-battery/> "TalentCell Lithium Ion Battery Pack"
[5]: <https://a.co/d/31luwGT> "EPZLON MOSFET Switch Driver Module"
[6]: https://a.co/d/efJLlEA "12v-to-3.3v DC Voltage Regulator"
[7]: https://a.co/d/dNqmrwU "12v Submersible Water Pump"
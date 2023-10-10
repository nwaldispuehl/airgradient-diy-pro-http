# Airgradient DIY PRO HTTP

Firmware for the [Airgradient](https://www.airgradient.com/) [DIY Pro](https://www.airgradient.com/indoor/) v4.2 Indoor Air Quality Monitor that offers the measurement values as JSON via HTTP.

The `airgradient-diy-pro-http.ino` is a modified copy of one of the [Airgradient Arduino](https://github.com/airgradienthq/arduino) [example](https://github.com/airgradienthq/arduino/tree/master/examples) files: 
[DIY_PRO_V4_2.ino](https://github.com/airgradienthq/arduino/blob/master/examples/DIY_PRO_V4_2/DIY_PRO_V4_2.ino).

## Example

Once started with configured WLAN, a JSON structure containing all current sensor readings can be obtained on the IP address of the Airgradient DIY Pro, e.g.:


```
$ curl --silent 10.20.30.40 | jq .

{
  "sensor": {
    "co2": 668,
    "pm01": 5,
    "pm02": 6,
    "pm10": 10,
    "pm03PCount": 1173,
    "tvoc_index": 248,
    "nox_index": 1,
    "temp_c": 24.32,
    "humidity": 54
  },
  "system": {
    "wifi": {
      "rssi": -83,
      "ssid": "MY_WIFI",
      "hw_addr": "ca:ff:ee:ba:be:00",
      "ip": "10.20.30.40"
    },
    "millis": 1234567,
    "serial": "abcdef"
  }
}

```


## How to install

Just follow the [Airgradient instructions](https://www.airgradient.com/open-airgradient/instructions/basic-setup-skills-and-equipment-needed-to-build-our-airgradient-diy-sensor/).

Basically 
- clone this repository into your [Arduino](https://www.arduino.cc/) [IDE](https://www.arduino.cc/en/software) folder (likely `~/Arduino` :rolleyes:), 
- open the project as Arduino Sketchbook in the IDE,
- add the [additional board manager URL](https://www.airgradient.com/open-airgradient/instructions/basic-setup-skills-and-equipment-needed-to-build-our-airgradient-diy-sensor/) in the properties and install the respective Board (ESP8266 `LOLIN(WEMOS) D1 R2 & mini`) and 
- all libraries mentioned in the header of the [`airgradient-diy-pro-http.ino`](./airgradient-diy-pro-http.ino) file,
- and plug in your DIY Pro air monitor.

Then you should be able to flash it with the new code. :cheers:

Nota bene: If you need the 'send to server' functionality to the Airgradient Cloud you gotta uncomment the respective [line](./airgradient-diy-pro-http.ino#L191) in the `loop` function.
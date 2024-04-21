# Yabox
Yet another box - multi purpose box for my domotics

## Hardware
- Wemos D1 Pro Mini (ESP8266 board)
- Nokia 5510 display
- BME 280 temperature, pressure & humidity sensor
- Rotary encoder with integrated push button
- Push button

## What I think I'll integrate in the box
- Node that sends temperature, humidity & pressure to my domoticz (either NRF24L01 gateway, MQTT client, or REST call)
- Display the room temperature, humidity & pressure
- Display values coming from the domotics system, such as
- - outside temperature, humidity & pressure (e.g. coming from MQTT)
  - solar paners: actual power generation, energy generation
  - gas consumption (power, energy)
 
- Act as MPD client, to control my MPD media player
- The rotary encoder will be used to navigate through various screens & as push button

## Pinout for the Wemos D1 Pro mini

- https://lastminuteengineers.com/wemos-d1-mini-pinout-reference/
- https://randomnerdtutorials.com/esp8266-pinout-reference-gpios)
- All pins have configurable internall pullup-pulldown resistors

|Label|GPIO|ESP8266 PIN note|Reason|Connect to|Support interrupts|
|-----|----|------------|------|----------|------------------|
|D0|GPIO16|!|HIGH at boot, used to wake up from deep sleep|Rotary encoder CLK|no|
|D1|GPIO5|SCL|/|BME280 SCL|yes|
|D2|GPIO4|SDA|/|BME280 SDA|yes|
|D3|GPIO0|!|connected to FLASH button, boot fails if pulled LOW|Display CE|yes|
|D4|GPIO2|!|HIGH at boot, boot fails if pulled LOW|Display RST|yes|
|D5|GPIO14|v|SCK|Display CLK|yes|
|D6|GPIO12|v|MISO|Display DC|yes|
|D7|GPIO13|v|MOSI|Display DIN (mosi)|yes|
|D8|GPIO15|!|Required for boot, boot fails if pulled high. Need to press rotary button while startup with rotary on breakout (otherwise pulled high)|Rotary encoder switch|yes|
|RX|GPIO3|!|Rx pin, used for flashing and debugging|Programming|?|
|TX|GPIO1|!|Tx pin, used for flashing and debugging|Programming|?|
|A0|ADC0|!|Analog input pin, cannot be configured as output|Rotary encoder DT|?|
|GND|/|v|/|GND all components|n/a|
|3V3|/|v|/|3V3 all components|n/a|

Separate push button will be used to control the display light

## Dependencies
- https://github.com/adafruit/Adafruit-PCD8544-Nokia-5110-LCD-library (which depends on https://github.com/adafruit/Adafruit-GFX-Library itself)

## Some useful resources
- https://www.edgemicrotech.com/esp8266-rotary-encoder-2004-lcd-dht11-with-a-menu-system/ (menu system)
- https://www.sparkfun.com/datasheets/LCD/Monochrome/Nokia5110.pdf
- https://github.com/mcauser/WeMos-D1-mini-Nokia-5110-PCD8544/blob/master/examples/hello-wemos/hello-wemos.ino

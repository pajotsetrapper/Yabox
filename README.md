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

|Label|GPIO|Safe to use?|Reason|Connect to|
|-----|----|------------|------|----------|
|D0|GPIO16|!|HIGH at boot, used to wake up from deep sleep|Rotary encoder out A|
|D1|GPIO5|v|/|Nokia 5510 Display CLK|
|D2|GPIO4|v|/|Nokia 5510 Display DIN|
|D3|GPIO0|!|connected to FLASH button, boot fails if pulled LOW|BME280 SCL|
|D4|GPIO2|!|HIGH at boot, boot fails if pulled LOW|BME280 SDA|
|D5|GPIO14|v|/|Nokia 5510 Display DC|
|D6|GPIO12|v|/|Nokia 5510 Display CE|
|D7|GPIO13|v|/|Nokia 5510 Display RST|
|D8|GPIO15|!|Required for boot, boot fails if pulled HIGH|Rotary encoder out B|
|RX|GPIO3|!|Rx pin, used for flashing and debugging|Free|
|TX|GPIO1|!|Tx pin, used for flashing and debugging|Free|
|A0|ADC0|!|Analog input pin, cannot be configured as output|Rotary encoder switch|
|GND|/|v|/|GND all components|
|3V3|/|v|/|3V3 all components|

* Best is to attach the encoder & buttons to interrupt capable pins:
The Wemos board wiki suggests that any pin except D0 can be used for interrupts.
D3 and D4 are commonly chosen because they work well for various shields and modules.
!! dinf a solution for Roatary encoder pin A

... and the push button is then used as switch between VCC & the display's backlight

## Dependencies

- https://github.com/adafruit/Adafruit-PCD8544-Nokia-5110-LCD-library (which depends on https://github.com/adafruit/Adafruit-GFX-Library itself)

## Some useful resources

- https://www.edgemicrotech.com/esp8266-rotary-encoder-2004-lcd-dht11-with-a-menu-system/ (menu system)
- 

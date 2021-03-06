RFLink-ESPLink pcb
===================

This is a PCB card for use with [RFLink](http://rflink.nl/blog2/) software, [ESP-Link](https://github.com/jeelabs/esp-link), [ESP-Easy](https://github.com/letscontrolit/ESPEasy) or what you find fits you best.
It is mainly for my purpose of getting [IKEA anslut remote control](http://www.ikea.com/se/sv/catalog/products/90300773/) in my Home Assistant setup. And for measure my pellets and power meter.

**You can fill the board so it meat yours need!!**

Use it as a RFLink with receiver and transmitter, and connect to server with USB, add CC2500 module for IKEA asnlut support.

Add a Wemos D1 Mini to get the RFLink more portable and communicate via WiFi via [tcp-mode](https://home-assistant.io/components/rflink/#tcp-mode).
If you just are interested in IKEA anslut, use a CC2500 module + Arduino Pro Mini + Wemos D1 Mini and communicate with MQTT.
 
Inspired by https://github.com/NDBCK/Ansluta-Remote-Controller for Arduino Pro Mini support, and also https://github.com/Genestealer/Home-Assistant-RFLink-Gateway-ESP8266 fore the komplete setup!

Schema
-----------
![rflink-esplink schema](https://github.com/rosangen/rflink-esplink/blob/master/PCB/img/schema-rflink-esplink.png?raw=true "Schema img")
[Schema pdf](https://github.com/rosangen/rflink-esplink/blob/master/PCB/RfLink-ESPlink.pdf?raw=true "RfLink-ESPlink.pdf")

PCB
------
Size 94 x 96mm
![rflink-esplink pcb topside](https://github.com/rosangen/rflink-esplink/blob/master/PCB/img/topp.jpg?raw=true "rflink-esplink pcb topside")

Fore the moment, no PCB is tested, more info to come!

Configurations
-----------
Some configurations explained:

### RFLink USB connected:
```
IC2 Arduino Mega, IC5 Transmitter, IC6 or IC7 Receiver, X1 Antenna connection. 
Option 1: C5,C6 and C7 for better reception with RXB6 receiver.
Option 2: R3, R9, LED1 so se TX communication is visible (receiving data).
```

### RFLink with ESP-link:
```
IC1 ESP, IC2 Arduino Mega, IC5 Transmitter, IC6 or IC7 Receiver. R1, R2, R3.
- Ansluta option: IC4 CC2500, R4-7, C8.
- Option 1 and 2, se above.
```

### Anluta MQTT:
```
IC1 ESP, IC3 Arduino Pro Mini 3.3v, IC4 CC2500 modul, C8.
- Option R9 LED1
```

### EasyESP:
With 1-wire temp and power meter sensor.
```
IC1 ESP, R20-R25 if needed. If lead needed: R10, R11, LED 2, LED3, R20, JP1, R21, JP2. 
Temperatur: DS18B20 connected to JP1
Power meter: LTR4206E ir detector connected to JP2.
```

### Onboard 3.3v converter
If you don't want to use Mega 2560 or ESP interna 3.3v converter you can add U1 (AMS1117 3.3v) and C2, C3, C4.
- PS1 Power selector is for choose input source, IC2 Mega or IC1 ESP 5 volt. (JP5 can only be in used if not Mega 2560 is in use).
- PS2 is the 3.3v source selector, use INT with interna 3.3v converter.

Komponents
-----------

<table>
<tbody>
<tr>
<td><strong>Part</strong></td>
<td><strong>Value</strong></td>
<td><strong>Device/Type</strong></td>
<td><strong>Package/Info</strong></td>
</tr>
<tr>
<td>C1</td>
<td>10&micro;F</td>
<td>CAPACITOR</td>
<td>E2-5</td>
</tr>
<tr>
<td>C2</td>
<td>100nF</td>
<td>CAPACITOR</td>
<td>C0805</td>
</tr>
<tr>
<td>C3</td>
<td>0.1&micro;F</td>
<td>CAPACITOR</td>
<td>E2-5</td>
</tr>
<tr>
<td>C4</td>
<td>10&micro;F</td>
<td>CAPACITOR</td>
<td>E2-5</td>
</tr>
<tr>
<td>C5</td>
<td>100nF</td>
<td>CAPACITOR</td>
<td>C0805</td>
</tr>
<tr>
<td>C6</td>
<td>100nF</td>
<td>CAPACITOR</td>
<td>C0805</td>
</tr>
<tr>
<td>C7</td>
<td>10&micro;F</td>
<td>CPOL-EUE2-5</td>
<td>E2-5</td>
</tr>
<tr>
<td>C8</td>
<td>100nF</td>
<td>CAPACITOR</td>
<td>C0805</td>
</tr>
<tr>
<td>C9</td>
<td>10&micro;F</td>
<td>CPOL-EUE2-5</td>
<td>E2-5</td>
</tr>
<tr>
<td>IC1</td>
<td>WEMOS D1 MINI</td>
<td>WEMOS D1 MINI</td>
<td>&nbsp;WeMos.cc</td>
</tr>
<tr>
<td>IC2</td>
<td>ARDUINO-MEGA</td>
<td>ARDUINO MEGA 2560</td>
</tr>
<tr>
<td>IC3</td>
<td>PRO MINI 3.3V</td>
<td>ARDUINO PRO MINI</td>
</tr>
<tr>
<td>IC4</td>
<td>CC2500</td>
<td>CC2500 MODULE</td>
</tr>
<tr>
<td>IC5</td>
<td>TRANSMITTER 433MHZ</td>
<td>TRANSMITTER 433MHZ</td>
</tr>
<tr>
<td>IC6</td>
<td>RXB6</td>
<td>RECEIVER</td>
</tr>
<tr>
<td>IC7</td>
<td>RTX-MID</td>
<td>RTX-MID</td>
<td>Aurel</td>
</tr>
<tr>
<td>IC8</td>
<td>NRF24L01A</td>
<td>NRF24L01A</td>
<td>NRF24L01</td>
</tr>
<tr>
<td>IC9</td>
<td>ESP-01</td>
<td>ESP8266 Wifi module 01</td>
</tr>
<tr>
<td>J1</td>
<td>JUMPER 2 SMD</td>
<td>Jumper</td>
<td>Aktivate CC2500</td>
</tr>
<tr>
<td>J2</td>
<td>JUMPER 3 SMD</td>
<td>Jumper</td>
<td>3.3 or 5.0V Aurel</td>
</tr>
<tr>
<td>JP1</td>
<td>GS015S-3.81-3P</td>
<td>PCB terminal block</td>
<td>PCB terminal block</td>
</tr>
<tr>
<td>JP2</td>
<td>GS015S-3.81-3P</td>
<td>PCB terminal block</td>
<td>PCB terminal block</td>
</tr>
<tr>
<td>JP3</td>
<td>GS015S-3.81-3P</td>
<td>PCB terminal block</td>
<td>PCB terminal block</td>
</tr>
<tr>
<td>JP4</td>
<td>GS015S-3.81-2P</td>
<td>PCB terminal block</td>
<td>PCB terminal block</td>
</tr>
<tr>
<td>JP5</td>
<td>GS015S-3.81-2P</td>
<td>PCB terminal block</td>
<td>PCB terminal block</td>
</tr>
<tr>
<td>LED1</td>
<td>LED1206</td>
<td>LED-1206</td>
<td>LEDs</td>
</tr>
<tr>
<td>LED2</td>
<td>LED1206</td>
<td>LED-1206</td>
<td>LEDs</td>
</tr>
<tr>
<td>LED3</td>
<td>LED1206</td>
<td>LED-1206</td>
<td>LEDs</td>
</tr>
<tr>
<td>LED4</td>
<td>LED1206</td>
<td>LED-1206</td>
<td>LEDs</td>
</tr>
<tr>
<td>PS1</td>
<td>JUMPER</td>
<td>2 TO 1 POWER</td>
</tr>
<tr>
<td>PS2</td>
<td>JUMPER</td>
<td>3 TO 1 POWER</td>
</tr>
<tr>
<td>R1</td>
<td>470R</td>
<td>RESISTOR R0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R2</td>
<td>470R</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R3</td>
<td>470R</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R4</td>
<td>470R</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R5</td>
<td>470R</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R6</td>
<td>470R</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R7</td>
<td>470R</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R8</td>
<td>1K</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R9</td>
<td>1K</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R10</td>
<td>1K</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R11</td>
<td>1K</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R12</td>
<td>4k7</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R13</td>
<td>4k7</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R20</td>
<td>4k7</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R21</td>
<td>4k7</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R22</td>
<td>4k7</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R23</td>
<td>4k7</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R24</td>
<td>4k7</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>R25</td>
<td>4k7</td>
<td>RESISTORR0805</td>
<td>R0805</td>
</tr>
<tr>
<td>U1</td>
<td>AMS1117</td>
<td>800mA and 1A Low Dropout (LDO) Positive Regulator</td>
<td>SOT223</td>
</tr>
<tr>
<td>U2</td>
<td>DHT22</td>
<td>DHT-22</td>
</tr>
<tr>
<td>U3</td>
<td>DS18B20</td>
<td>DS18B20</td>
</tr>
<tr>
<td>X1</td>
<td>BU-SMA-V</td>
<td>ANTEN</td>
</tr>
</tbody>
</table>

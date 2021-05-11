# DuinoCoinI2C

This project design to mine [Duino-Coin](https://github.com/revoxhere/duino-coin) using an Esp8266/Esp32 as a master and Arduino as a slave. 

Using the I2C communication to connect all the boards and make a scalable communication between the master and the slaves.

## Pinouts

Connect the pins of the Esp8266 or Esp32 on the Arduino like the table/images below.

|| ESP8266 | ESP32 | Arduino |
|:-:| :----: | :----: | :-----: |
||3.3V | 3.3V | 5V |
||GND | GND | GND |
|`SCL`|D1 (GPIO5) | GPIO22 | A5 |
|`SDA`|D2 (GPIO4) | GPIO21 | A4 |

<h3>WARNING: Do not connect the USB of the Arduino, all the boards are powered by 3.3V.</h3>

### Esp8266 with one Arduino Nano.

<img src="Resources/Fritzing/DuinoCoinI2C/DuinoCoinI2C_1xNano.png" alt="DuinoCoinI2C" width="50%">

### Esp8266 with three Arduino Nano

<img src="Resources/Fritzing/DuinoCoinI2C/DuinoCoinI2C_3xNano.png" alt="DuinoCoinI2C" width="50%">

# Library Dependency

* [DuinoCoin](https://github.com/ricaun/arduino-DuinoCoin) (Handle the `Ducos1a` hash work)
* [ArduinoUniqueID](https://github.com/ricaun/ArduinoUniqueID) (Handle the chip ID)
* [StreamJoin](https://github.com/ricaun/StreamJoin) (StreamString for AVR)

# Arduino

All Slaves have the same code and should select the I2C Address automatically.

## Automatic I2C Address 

The I2C Address on the Arduino is automatically updated when the board starts, if an Address already exists on the I2C bus the code finds another Address to use.

# Esp8266/Esp32

The master requests the job on the `DuinoCoin` server and sends the work to the slave (Arduino).

After the job is done, the slave sends back the response to the master (Esp8266/Esp32) and then sends back to the `DuinoCoin` server.

## Max Client/Slave

The code supports 10 clients and can be changed on the define:

```
#define CLIENTS 10
```

# Tests

`At the moment the code was tested with 6 clients/slaves at the same time.`

<img src="Resources/image/image01.jpg" alt="image01" width="25%">
<img src="Resources/image/image02.jpg" alt="image02" width="25%">

---

Do you like this project? Please [star this project on GitHub](https://github.com/ricaun/DuinoCoinI2C/stargazers)!
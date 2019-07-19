# GasAlert24
Gas sensor - I.O.T. Exam project - Spring 2019

| Contributors: |  |
| --- | --- |
| Francesco Cassini | cassini.785771@studenti.uniroma1.it |
| Lorenzo Leschiera | leschiera.16@studenti.uniroma1.it |
| Matteo Ginesi     | mat.ginesi@gmail.com |

### LoRaWan on Mbed

All the comunication system is based on LoRaWAN stack protocol managed by STM32 microcontroller board `DISCO-L072CZ`, programmed by `Mbed` (www.mbed.com). 
Firmware uses `Mbed OS 5` to provide drivers and pre-built code for:

 - LoRaWAN radio module: SX1276
 - Analog Input/Output
 - Digital GPIOs
 - Debug and tracing
 - RS232 over USB stack

Code is divided in two main *blocks*:
 1. System initialization: `main.cpp`
 2. mbed-os configuration (LoRaWAN login): `mbed_app.json`

## System initialization

In the `main.cpp` file, there are all the functions/declarations needed to deploy the **send data function**.
The user has to change the `ID` constant in the file, as a hexadecimal value of 16 bit (`uint16_t`):
``` c++
...
    #define ID              0xAAFF
...
```

Sensor, for the board used in the project, is addressed on pin analog 1 (`A1`). Change it in case of need. Pin `A0` can't be used.
```c++
...
    AnalogIn sensor(A1);
...
```

In the `send_data()` function the user can set any kind of encoding of transmitted data, writing the correct message into 
the `tx_buffer` and settings the correct dimension value of it, into `packet_len` variable.
```c++
    ...
    static void send_message()
    {
        uint16_t packet_len;
        int16_t retcode;
        
        /*
            Reading sensor data (unsigned int 16 bit)
            Writing ID and sensor data into transmission buffer
            Sending data to Gateway by LoRaWAN stack
        */
        uint16_t data = sensor.read_u16();
        packet_len = sprintf(
            (char *) tx_buffer, "%4X%u", ID, data);
        
        printf("\r\ndata sent: %s\r\n", tx_buffer);
    ...
    }
```

## LoRaWAN login configuration

In the `mbed_app.json` file, each user **NEED TO CONFIGURE** their own *TheTingsNetwork* credential to their proper application.

Note:
> This code works only for `APB` protocol. The `OOTA` way isn't verificated yet.
> For all information about *TheTingsNetwork* procedures, please refer to www.thethingsnetwork.com.

In order to change radio module, set the proper value in:

```json
...
    "config": {
        "lora-radio": {
            "help": "Which radio to use (options: SX1272,SX1276)",
            "value": "SX1276"
        },
...
```

For *TheThingsNetwork* credentials, change:
```json
...
    "target_overrides": {
        "*": {
            ...
            "lora.appskey": "{C-STYLE HEX App Session Key}",
            "lora.nwkskey": "{C-STYLE HEX Network Session Key}",
            "lora.device-address": "0x<HEX DATA OF device address>" 
...
```

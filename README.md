# `AUX-Core`

> Core/Sensor PCB of the Auxspace Avionics stack, built around an ESP32-S3-WROOM-1.

AUX-Core is based on [µMETER](https://github.com/AUXSPACEeV/microMETER) and extends it by a
high-G accelerometer, a magnetometer, 9 V USB Power Delivery and the stack connector that
interfaces the board with the other PCBs of the avionics stack.

## Features

* **Barometer** DPS310 for altitude computation
* **IMU** STM LSM6DSO32X for acceleration and rotation data
* **High-G accelerometer** ADXL375 (±200 g) for launch and recovery events
* **Magnetometer** Melexis MLX90395 for attitude reference
* **Buzzer** for easier commissioning and recovery
* **CAN bus** (TCAN334) for communication with the other stack PCBs
* **µSD card** for logging
* **USB-C with 9 V Power Delivery** (CH224A sink) for programming, debugging and supply
* **Stack connector** Samtec TFM-110-02-S-D-A / SFM-110-02-L-D-A for the avionics stack
* **Status LEDs** for power, SD activity and board state

## Stack connector

The board carries a mating Samtec pin/socket pair (2x10, 1.27 mm), so Core boards and
expansion PCBs stack directly on top of each other. The connector routes the switched and
unswitched VBus rails, CAN, I²C, UART and the ARM signal through the stack.

## Power supply

The board is supplied over USB-C. The CH224A PD sink negotiates 9 V from the charger; the
on-board TPS7B8601 regulator derives the 3V3 rail from it. VBus is distributed to the stack
both directly and through the switched rails.

## Programming

The ESP32-S3 is programmed via USB-C or the UART connection.
To enter download mode, press and hold BOOTSEL at startup.

## Repository layout

| Folder                                                     | Content                                          |
| ---------------------------------------------------------- | ------------------------------------------------ |
| [`1_Blockschaltbild`](./1_Blockschaltbild)                 | Block diagrams                                    |
| [`2_Designunterlagen`](./2_Designunterlagen)               | Pin maps, calculations and design documents       |
| [`3_Elektronik`](./3_Elektronik)                           | KiCad project, symbols, footprints and 3D models  |
| [`4_Simulationen`](./4_Simulationen)                       | LTspice simulations                               |
| [`5_Tests`](./5_Tests)                                     | Test results and oscillograms                     |
| [`6_Export-Fertigungsdaten`](./6_Export-Fertigungsdaten)   | Manufacturing data, BOMs, schematics and STEP files |

## License

Hardware is released under the CERN Open Hardware Licence Version 2 - Permissive,
see [`LICENSE`](./LICENSE).

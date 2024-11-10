# SPI Communication between ATmega32 (Slave) and ATmega328P (Master)

This project demonstrates SPI communication between an ATmega32 (configured as the slave) and an ATmega328P (configured as the master). The master device initiates communication with the slave, sending a sequence of characters, while the slave receives and transmits the data back.

## Overview

- **Master**: ATmega328P
- **Slave**: ATmega32
- **Communication Protocol**: SPI (Serial Peripheral Interface)
- **Libraries**: `<SPI.h>` for master-side SPI functions

The master continuously sends data to the slave, which echoes it back using the SPI protocol. The data received by the slave is then transmitted over UART.

## Components and Setup

1. **ATmega32**: Configured as the SPI slave.
   - Receives data from the master via SPI.
   - Transmits the received data over UART.
2. **ATmega328P**: Configured as the SPI master.
   - Sends data to the slave in a loop.
   - Uses `SPI.transfer` to transmit ASCII characters sequentially.

### Wiring

- **SPI Pins**:
  - `MISO` (Master In Slave Out): Connect ATmega32 MISO to ATmega328P MISO.
  - `MOSI` (Master Out Slave In): Connect ATmega32 MOSI to ATmega328P MOSI.
  - `SCK` (Serial Clock): Connect ATmega32 SCK to ATmega328P SCK.
  - `SS` (Slave Select): Connect ATmega328P pin 10 to ATmega32 SS.

## How to Use

1. **Upload the Slave Code** to the ATmega32 and connect it to a UART terminal to observe received data.
2. **Upload the Master Code** to the ATmega328P.
3. Observe the sequence of characters sent from the ATmega328P to the ATmega32 via SPI and retransmitted over UART.

## Notes

- Ensure both devices share a common ground.
- Check the SPI mode and clock settings to match your sensor’s requirements if adjusting for different setups.

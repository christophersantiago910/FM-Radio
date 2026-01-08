# Arduino FM Radio

This project implements a standalone FM radio using an Arduino nano as the microcontroller. The system features an external FM receiver, LCD display, rotary encoder tuning, and amplified audio output.

The entire system is powered by a MB102 power supply and a 9V battery. 

---

## Project Features

- FM tuning via rotary encoder
- Frequency display on Nokia 5110 LCD
- EEPROM storage of last tuned frequency
- External physical FM antenna
- Audio amplification via PAM8403 module

---

## Power Architecture

| Voltage | Devices Powered |
|------|------------------|
| 5 V | Arduino Nano, TEA5767 FM module, rotary encoder, PAM8403 amplifier |
| 3.3 V | Nokia 5110 LCD |
| GND | Common reference for all modules |

---

## System Overview

- **Arduino Nano**
  - Communicates with modules and manages program
- **TEA5767 FM Radio Module**
  - Controlled via I²C
  - Outputs analog audio
- **Nokia 5110 LCD**
  - Shows FM radio station
  - Powered at 3.3 V (every other component is powered at 5 V)
- **Rotary Encoder**
  - User input for frequency adjustment
- **PAM8403 Audio Amplifier**
  - Drives a small speaker

---

## LCD Configuration (Nokia 5110 / PCD8544)

- Power supply: 3.3 V
- Backlight power supply: 3.3 V through a 220 Ω resistor
- Interface is connected to the microcontroller
- LCD reset once the system is rebooted up

---

## Antenna Configuration

A physical FM antenna connected directly to the TEA5767 antenna pin.

---

## Wiring

### Nokia 5110 LCD

| LCD Pin | Arduino Uno Pin |
|------|------------------|
| VCC | 3.3 V |
| GND | GND |
| SCLK | D13 |
| DIN (MOSI) | D11 |
| D/C | D5 |
| SCE (CE) | D4 |
| RST | D3 |
| LED | 3.3 V via 220 Ω resistor |


### TEA5767 FM Module

| Module Pin | Arduino Uno Pin |
|-----------|------------------|
| VCC | 5 V |
| GND | GND |
| SDA | A4 |
| SCL | A5 |
| ANT | Physical antenna |


### Rotary Encoder

| Encoder Pin | Arduino Uno Pin |
|------------|------------------|
| CLK | A1 |
| DT | A0 |
| SW | A2 |
| VCC | 5 V |
| GND | GND |



### PAM8403 Audio Amplifier

| Amplifier Pin | Connection |
|--------------|-------------|
| VCC | 5 V |
| GND | GND |
| IN L / IN R | TEA5767 audio outputs |
| OUT | Speaker |

---

## Pictures

Version that incorporates perforated board and significantly more solder fumes is currently being made.

---

## Wiring Diagram

The complete wiring diagram for this project is shown below.

**Currently in the process of making this**

![Wiring Diagram](docs/wiring_diagram.png)

---

## Source Code

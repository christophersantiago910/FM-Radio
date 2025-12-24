# Arduino FM Radio with Nokia 5110 LCD (Uno R3)

This project implements a standalone FM radio using an Arduino Uno R3 as both the
microcontroller and power source. The system features an external FM receiver,
graphical LCD display, rotary encoder tuning, and amplified audio output.

The Arduino Uno is powered via USB and supplies both 5 V and 3.3 V rails to the system.

---

## Project Features

- FM tuning via rotary encoder
- Frequency display on Nokia 5110 (PCD8544) LCD
- EEPROM storage of last tuned frequency
- External physical FM antenna
- Audio amplification via PAM8403 module
- Clean separation of 5 V and 3.3 V power domains

---

## Power Architecture

| Voltage | Devices Powered |
|------|------------------|
| 5 V | Arduino logic, TEA5767 FM module, rotary encoder, PAM8403 amplifier |
| 3.3 V | Nokia 5110 LCD logic and backlight |
| GND | Common reference for all modules |

Important: The Nokia 5110 LCD must not be powered from 5 V.

---

## System Overview

- **Arduino Uno R3**
  - Runs the main firmware
  - Supplies regulated 5 V and 3.3 V power
- **TEA5767 FM Radio Module**
  - Controlled via I²C
  - Outputs analog audio
- **Nokia 5110 LCD**
  - SPI-controlled graphical display
  - Powered at 3.3 V only
- **Rotary Encoder**
  - User input for frequency adjustment
- **PAM8403 Audio Amplifier**
  - Drives a small speaker

---

## LCD Configuration (Nokia 5110 / PCD8544)

- Logic supply: 3.3 V
- Backlight supply: 3.3 V through a 220 Ω resistor
- SPI interface connected directly to the Arduino Uno
- LCD reset is forced in software at startup to ensure reliable initialization

---

## Antenna Configuration

The project uses a physical FM antenna connected directly to the TEA5767 antenna pin.

- Signal conductor connects to ANT
- If the antenna includes a ground or shield, it is connected to system ground
- No series components are used between the antenna and the radio module

---

## Pin Mapping

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

---

### TEA5767 FM Module

| Module Pin | Arduino Uno Pin |
|-----------|------------------|
| VCC | 5 V |
| GND | GND |
| SDA | A4 |
| SCL | A5 |
| ANT | Physical antenna |

---

### Rotary Encoder

| Encoder Pin | Arduino Uno Pin |
|------------|------------------|
| CLK | A1 |
| DT | A0 |
| SW | A2 |
| VCC | 5 V |
| GND | GND |

---

### PAM8403 Audio Amplifier

| Amplifier Pin | Connection |
|--------------|-------------|
| VCC | 5 V |
| GND | GND |
| IN L / IN R | TEA5767 audio outputs |
| OUT | Speaker |

---

## Wiring Diagram

The complete wiring diagram for this project is shown below.

![Wiring Diagram](docs/wiring_diagram.png)

---

## Source Code

# RA4M1-Custom Arduino Board Package

## Overview

This repository provides a custom Arduino board package for the Renesas RA4M1 MCU, designed for use with boards such as the **WeAct RA4M1 64 Pin Core Board** and the **PT Motorsport RA4M1 Dev Board**. These boards expose more IO pins than the official Arduino UNO R4 Minima and do not include extra features like WiFi (found on the R4 WiFi).

## Features

- **Expanded IO access:** Supports more pins than the Arduino UNO R4 Minima, including 10 analog inputs.
- **Accurate pin mapping:** Digital and analog pins mapped to the RA4M1 hardware.
- **Built-in support for common Arduino peripherals** (UART, I2C, SPI, CAN, etc.)
- **LED indicators:** TX/RX LEDs mapped for serial activity.
- **Direct access to SWD, CAN, and other advanced features** for developers.

## Supported Boards

- **WeAct RA4M1 64 Pin Core Board**
- **PT Motorsport RA4M1 Dev Board**
- Any compatible board exposing similar pinouts

---

## Pin Mapping

The following table shows the mapping between Arduino logical pins and the physical RA4M1 pins (port/pin):

| Arduino Pin | Port/Pin          | Notes                        |
|-------------|-------------------|------------------------------|
| D0          | P3_1              |                              |
| D1          | P3_2              | UART TX                      |
| D2          | P1_5              |                              |
| D3          | P1_4              | PWM                          |
| D4          | P1_3              |                              |
| D5          | P1_2              | PWM                          |
| D6          | P1_6              | PWM                          |
| D7          | P1_7              |                              |
| D8          | P3_4              |                              |
| D9          | P3_3              | PWM                          |
| D10         | P1_12             | PWM, SPI CS                  |
| D11         | P1_9              | PWM, SPI MOSI                |
| D12         | P1_10             | SPI MISO                     |
| D13         | P1_11             | SPI SCK, LED_BUILTIN         |
| A0          | P0_14             | Analog, DAC                  |
| A1          | P0_0              | Analog                       |
| A2          | P0_1              | Analog                       |
| A3          | P0_2              | Analog                       |
| A4 (SDA)    | P1_1              | I2C SDA                      |
| A5 (SCL)    | P1_0              | I2C SCL                      |
| 20          | P5_0              | Analog voltage measure       |
| 21          | P0_12             | TX LED                       |
| 22          | P0_13             | RX LED                       |
| 23          | P5_1              | TX on SWD connector          |
| 24          | P5_2              | RX on SWD connector          |
| 25          | P1_8              | SWDIO                        |
| 26          | P3_0              | SWCLK                        |
| 27          | P4_0              |                              |
| 28          | P4_1              |                              |
| 29          | P4_2              |                              |
| 30          | P4_11             |                              |
| 31          | P4_10             |                              |
| 32          | P4_9              |                              |
| 33          | P2_6              |                              |
| 34          | P2_5              |                              |
| 35          | P1_13             |                              |
| 36 (A6)     | P0_3              | Analog                       |
| 37 (A7)     | P0_4              | Analog                       |
| 38 (A8)     | P0_15             | Analog                       |
| 39 (A9)     | P0_11             | Analog                       |

- **Analog Inputs:** A0–A9 (A0–A5: pins 14–19, A6: pin 36 (P0_3), A7: pin 37 (P0_4), A8: pin 38 (P0_15), A9: pin 39 (P0_11))
- **PWM Outputs:** Marked above (D3, D5, D6, D9, D10, D11)
- **I2C:** A4 (SDA), A5 (SCL)
- **SPI:** D10 (CS), D11 (MOSI), D12 (MISO), D13 (SCK)
- **UART:** D0 (RX), D1 (TX)
- **LEDs:** D13 (LED_BUILTIN), 21 (TX LED), 22 (RX LED)
- **CAN:** D4 (TX), D5 (RX) (per `pins_arduino.h`)

---

## Setup

1. **Add the custom board manager URL** to your Arduino IDE. (https://ptmotorsport.github.io/RA4M1-Custom/package_PTMoSpoCo-RA4M1_index.json)
2. **Install the "PT MoSpoCo Boards"** package via Boards Manager. If you receive an error saying that the archive hash differs from the index hash you may have to manually the install the .zip file. To do this, go to C:\User\AppData\Local\Arduino15\staging\packages and replace the existing PTMoSpoCo-RA4M1.zip file with the PTMoSpoCo-RA4M1.zip file available above.
3. **Select your board:** Tools > Board > *RA4M1 PT MoSpoCo*.
4. **Connect your hardware** and upload sketches as usual.

(You may also need to load an Arduino Bootloader onto your RA4M1 board using Renesas FSP before your board will accept arduino sketches)

## Example Usage

Once installed and selected in the Arduino IDE, you can access all the extra IO pins via their logical Arduino numbers (D0, D1, ..., D39, A0–A9). For example:

```cpp
void setup() {
  pinMode(A8, INPUT); // Use new analog pin
  Serial.begin(115200);
}

void loop() {
  int analogValue = analogRead(A8);
  Serial.println(analogValue);
  delay(500);
}
```

## Notes

- **Pin mapping is defined in `variant.cpp` and `pins_arduino.h`.**
- If you have special hardware requirements, check your board schematic to confirm which physical RA4M1 pins are exposed.
- The current mapping supports 40 pins, including 10 analog inputs.

## Contributing

If you find mapping errors or want to propose improvements, please open an issue or pull request!

---

## License

MIT License

Copyright (c) 2025 ptmotorsport

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

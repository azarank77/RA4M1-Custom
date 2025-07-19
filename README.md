# RA4M1-Custom Arduino Board Package
Purpose
This repository provides a custom Arduino board package, enabling users to easily work with boards such as the WeAct RA4M1 64 Pin Core Board and the PT Motorsport RA4M1 Dev Board. These boards feature more IO pins than the Arduino R4 Minima, and omit additional features like WiFi found on the R4 WiFi.

## Features
Unlocks additional IO pins present on supported RA4M1-based boards.
Specifically targets boards with expanded pinouts, letting you use all available microcontroller IOs.
Designed for users who need more flexibility than the standard Arduino R4 Minima provides.

## Setup
Follow the standard Arduino procedure for adding custom boards.
Download the provided package_PTMoSpoCo_UNOR4Minima_index.json or use the appropriate board manager link.
Add the board package URL in your Arduino IDE preferences.
Install the "PT MoSpoCo Boards" via the Arduino Boards Manager.
Select your target board (e.g., RA4M1 PT MoSpoCo) from the Tools > Board menu.

## Usage
After installation, select the custom board within the Arduino IDE. You can now write and upload sketches that utilize all additional IO pins offered by your development board, beyond those available on the standard Arduino R4 Minima.

This is particularly useful for projects requiring more IO and more direct access to the RA4M1 microcontroller's capabilities.

# Pico W Keypad-to-LED Controller

Embedded demo for **Raspberry Pi Pico W (RP2040)** where a 4x4 membrane keypad controls 12 LEDs.

## Project Overview
This project implements a simple input → processing → output pipeline:
- **Input:** 4x4 matrix keypad (digits + A/B/C/D + */#)
- **Processing:** key scan and dispatch logic on Pico/Pico W
- **Output:** 12 LEDs grouped as numeric (1–8) and alpha (A–D)

The firmware behavior is preserved from the provided source code (no logic changes).

## Repository Structure

```text
.
├── CMakeLists.txt
├── diagram.json
├── src/
│   └── main.cpp
├── include/
└── docs/
    ├── architecture.md
    └── wiring.md
```

## Features
- Single-key LED activation for keys `1..8` and `A..D`
- Group ON/OFF control:
  - `9` turns ON LEDs 1..8
  - `0` turns OFF LEDs 1..8
  - `*` turns ON LEDs A..D
  - `#` turns OFF LEDs A..D
- 10 ms loop delay to reduce polling jitter

## Hardware Bill of Materials (from `diagram.json`)
- 1x Raspberry Pi Pico / Pico W board
- 1x 4x4 membrane keypad
- 12x LEDs (8 blue, 4 red)
- 12x 220Ω series resistors for LEDs
- 4x 1kΩ pull-up resistors for keypad rows
- Jumpers and breadboard

## GPIO Mapping Summary
Detailed table: `docs/wiring.md`.

- Keypad rows: GP26, GP22, GP21, GP20
- Keypad cols: GP19, GP18, GP17, GP16
- LED outputs: GP11, GP10, GP9, GP8, GP7, GP6, GP5, GP4, GP3, GP2, GP28, GP27

## Run in Wokwi
1. Create a new **Raspberry Pi Pico** project in Wokwi.
2. Copy `src/main.cpp` into `sketch.ino` (or equivalent Arduino source file in Wokwi).
3. Replace `diagram.json` with this repository's `diagram.json`.
4. Start simulation and press keypad keys.

## Run on Real Pico W Hardware
Because the code uses Arduino APIs (`setup()`, `loop()`, `Keypad.h`), use **Arduino-Pico** or **PlatformIO (Arduino framework)**:

1. Install Arduino IDE and add the **Raspberry Pi Pico/RP2040** core.
2. Install the **Keypad** library.
3. Select board: **Raspberry Pi Pico W**.
4. Open `src/main.cpp` contents in an `.ino` sketch (or adapt project layout for your toolchain).
5. Connect Pico W in BOOTSEL mode, upload, and monitor behavior.

## Wi-Fi Notes
This firmware does **not** use Wi-Fi APIs. No credentials are required or stored.

## Documentation
- Wiring and pinout: [`docs/wiring.md`](docs/wiring.md)
- Software architecture: [`docs/architecture.md`](docs/architecture.md)

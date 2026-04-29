# Firmware Architecture

## Overview
The firmware is monolithic and event-driven, following the Arduino runtime model:
- `setup()` initializes all LED GPIOs as outputs and sets them LOW.
- `loop()` continuously polls the keypad and executes a switch-case dispatcher.

Core logic remains unchanged from the provided implementation.

## Source File Layout
- `src/main.cpp`: complete firmware implementation.
- `docs/wiring.md`: hardware map and GPIO matrix.
- `diagram.json`: Wokwi hardware model.

## Runtime Flow
1. **Initialization Phase (`setup`)**
   - Iterates through `ledPins[12]`
   - Configures each as `OUTPUT`
   - Sets initial state to `LOW`

2. **Polling Phase (`loop`)**
   - Reads `keypad.getKey()`.
   - Ignores `NO_KEY`.
   - Uses `switch(key)` to dispatch behaviors.

3. **Action Phase**
   - Single-key cases: set one LED HIGH.
   - Group cases (`9`, `0`, `*`, `#`): bounded `for` loops update LED groups.
   - Fixed `delay(10)` before next loop iteration.

## Data Structures
- `keys[4][4]`: keypad character map.
- `ledPins[12]`: GPIO list for LED outputs.
- `rowPins[4]`, `colPins[4]`: keypad scan wiring.
- `Keypad keypad(...)`: keypad driver instance.

## Design Notes
- No dynamic memory allocation.
- Deterministic behavior with fixed-size arrays.
- No Wi-Fi stack usage despite Pico W target.

## Self-Review (generate → review → improve)
- Generated initial docs from code and schematic.
- Reviewed for consistency between `ledPins` index order and physical labels.
- Improved tables to show both logical index and key label to prevent wiring ambiguity.

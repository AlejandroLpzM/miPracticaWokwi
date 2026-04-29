# Wiring Guide (Raspberry Pi Pico W)

## Assumptions
- Pin mapping is derived from the provided source arrays (`ledPins`, `rowPins`, `colPins`) and Wokwi connection list.
- LEDs are active-high through 220Ω series resistors, with cathodes to GND.

## Components List
- 1x Raspberry Pi Pico W (RP2040)
- 1x 4x4 membrane keypad
- 12x LEDs:
  - Blue LEDs labeled 1..8
  - Red LEDs labeled A..D
- 12x 220Ω resistors (LED current limiting)
- 4x 1kΩ resistors (row pull-ups to 3V3)

## GPIO Pin Mapping

### Keypad
| Keypad Signal | Pico W GPIO | Purpose |
|---|---:|---|
| R1 | GP26 | Row input/scan line |
| R2 | GP22 | Row input/scan line |
| R3 | GP21 | Row input/scan line |
| R4 | GP20 | Row input/scan line |
| C1 | GP19 | Column drive/scan line |
| C2 | GP18 | Column drive/scan line |
| C3 | GP17 | Column drive/scan line |
| C4 | GP16 | Column drive/scan line |

### LEDs
| Logical LED | Key Label | Pico W GPIO |
|---:|---|---:|
| LED1 | `1` | GP11 |
| LED2 | `2` | GP10 |
| LED3 | `3` | GP9 |
| LED4 | `4` | GP8 |
| LED5 | `5` | GP7 |
| LED6 | `6` | GP6 |
| LED7 | `7` | GP5 |
| LED8 | `8` | GP4 |
| LED9 | `A` | GP3 |
| LED10 | `B` | GP2 |
| LED11 | `C` | GP28 |
| LED12 | `D` | GP27 |

## Power and Ground
- Keypad row pull-up resistor network tied to **3V3**.
- LED cathodes tied to **GND**.
- Ensure common ground across all components.

## Functional Mapping
- `1..8`: turns ON corresponding blue LED.
- `9`: turns ON all blue LEDs (1..8).
- `0`: turns OFF all blue LEDs (1..8).
- `A..D`: turns ON corresponding red LED.
- `*`: turns ON all red LEDs (A..D).
- `#`: turns OFF all red LEDs (A..D).

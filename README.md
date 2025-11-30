# LED Sequence Controller for MAX78000 FTHR Board

## Project Overview
This project implements an interrupt-driven LED sequence controller on the MAX78000 FTHR board. The system features two distinct LED patterns that can be toggled instantly via a push button with proper debouncing

# LED Sequence Controller for MAX78000 FTHR Board

## Project Overview
This project implements an interrupt-driven LED sequence controller on the MAX78000 FTHR board. The system features two distinct LED patterns that can be toggled instantly via a push button with proper debouncing.

## Features
- **Two LED Patterns**: Morse code "C O E" and rotating LED pattern
- **Instant Mode Switching**: Interrupt-driven button response
- **Hardware Debouncing**: 50ms debounce delay for reliable button presses
- **Low Power Operation**: CPU sleeps between interrupts using `__WFI()`
- **Timer-Driven Updates**: Precise 100ms timing via hardware timer
- **Multi-Port LED Support**: Controls LEDs across GPIO0, GPIO1, GPIO2, and GPIO3

## Hardware Requirements
- MAX78000 FTHR Evaluation Board
- 8 LEDs connected to specified GPIO pins
- Push button (SW1 on FTHR board)

## LED Pin Assignments
| LED | GPIO Port | Pin    |
|-----|-----------|--------|
| 0   | GPIO0     | PIN_17 |
| 1   | GPIO0     | PIN_16 |
| 2   | GPIO3     | PIN_1  |
| 3   | GPIO0     | PIN_19 |
| 4   | GPIO0     | PIN_11 |
| 5   | GPIO0     | PIN_8  |
| 6   | GPIO2     | PIN_3  |
| 7   | GPIO1     | PIN_1  |

## Pattern Descriptions

### Morse Code Pattern (Mode 0)
Displays "C O E" in Morse code using all 8 LEDs:
- **C** = `-.-.` (Dash Dot Dash Dot)
- **O** = `---` (Dash Dash Dash) 
- **E** = `.` (Dot)

**Timing** (100ms per step):
- Dot = 100ms ON
- Dash = 300ms ON (3 consecutive ON steps)
- Element gap = 100ms OFF
- Letter gap = 100ms OFF
- Word gap = 300ms OFF

### Rotating Pattern (Mode 1)
Creates a "moving dark spot" effect where one LED is off while all others are on:
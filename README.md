# CHIP-8 Emulator in Rust

A lightweight CHIP-8 interpreter written in Rust using [SDL2](https://github.com/Rust-SDL2/rust-sdl2) for graphics, input handling, and timing.

---

## Features

- **Standard CHIP-8 Specifications**:
  - 4 KB RAM with standard memory mapping (entry point at `0x200`).
  - 16 general-purpose 8-bit registers (`V0`–`VF`).
  - 16-level call stack and 16-bit program counter / index register.
  - Native 64×32 monochrome display rendered with a 15× scaling factor (960×480 window).
  - Built-in default font set loaded into low memory (`0x000`–`0x04F`).
- **Timing & Refresh**:
  - Decoupled CPU clock (~30 opcode ticks per video frame) synchronized with SDL2 `vsync` (~60 Hz).
  - Independent 60 Hz delay and sound timers.
  - Basic display synchronization to prevent screen tearing during draw operations.
- **Hardware-Accelerated Windowing**: Powered by SDL2 Canvas with integer scaling.

---

## Keypad Layout

The original COSMAC VIP hexadecimal keypad (`0` through `F`) is mapped to standard QWERTY keyboard layout:

```text
Original CHIP-8 Keypad        Keyboard Mapping
+---+---+---+---+              +---+---+---+---+
| 1 | 2 | 3 | C |              | 1 | 2 | 3 | 4 |
+---+---+---+---+              +---+---+---+---+
| 4 | 5 | 6 | D |     --->     | Q | W | E | R |
+---+---+---+---+              +---+---+---+---+
| 7 | 8 | 9 | E |              | A | S | D | F |
+---+---+---+---+              +---+---+---+---+
| A | 0 | B | F |              | Z | X | C | V |
+---+---+---+---+              +---+---+---+---+

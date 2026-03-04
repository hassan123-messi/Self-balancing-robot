
# Phase 2 — Intelligence (Raspberry Pi)

Goal: add high-level decision making on a Raspberry Pi while the ESP32 keeps real-time balance control.

## Scope
- Vision / perception on the Pi (camera processing).
- High-level commands sent to ESP32 (desired velocity/turn).
- ESP32 remains responsible for balance loop timing.

## Planned Deliverables
- Pi scripts for camera + tracking
- Command protocol Pi → ESP32 (Serial / UART)
- System architecture notes

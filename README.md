# LED Matrix Game System – Pomodoro Timer & Pixel Animations

A 16x16 WS2812B LED matrix Arduino project that doubles as a desk display and a Pomodoro timer. The system uses a joystick and keypad for low-latency input, and a buzzer for alerts. It was inspired by pixel art speaker products like the Divoom Ditoo Pro, with a focus on affordability and customization.

This repo contains the Arduino sketch that powers two modes:
- Cartoon mode with looping pixel animations selected from a 4x4 keypad
- Pomodoro mode with configurable study/short-rest/long-rest cycles and on-matrix status indicators

## Features
- 16x16 LED matrix animations (FastLED + FastLED_NeoMatrix)
- Pomodoro timer with staged input flow and visual indicators
- Joystick to hot-switch between modes without reset
- Buzzer alerts for session transitions
- Low-latency input handling for realtime interaction

## Hardware
- Arduino Uno R3
- 16x16 WS2812B RGB LED matrix (256 LEDs)
- 4x4 keypad
- Joystick module with button
- Active-low buzzer
- 5V power supply (high-current; 20A recommended for full brightness)

## Wiring (Arduino Pins)
LED Matrix
- Data in: D13
- Power: 5V external supply
- Ground: common ground with Arduino

Joystick
- X: A0
- Y: A1
- Button: D12 (INPUT_PULLUP)

Buzzer
- Signal: D11 (active-low)

Keypad
- Rows: D9, D8, D7, D6
- Cols: D5, D4, D3, D2

## Controls
Cartoon Mode
- Press `1`, `2`, `3` to play animations (loops until another key press)

Pomodoro Mode
- Move joystick right to switch from Cartoon to Pomodoro
- Enter durations (minutes) via keypad in this order:
  - Study duration
  - Short rest
  - Long rest
- Press the joystick button to confirm each entry
- Press `#` to reset settings at any time

Indicators
- Left column shows completed Pomodoros (0-4)
- Top-right indicator shows current state:
  - Red: study
  - Green: short rest
  - Orange: long rest (after 4th pomodoro)

## Build & Upload
1. Install required libraries in Arduino IDE:
   - FastLED
   - FastLED_NeoMatrix
   - Adafruit_GFX
   - Keypad
   - Framebuffer_GFX
2. Open the sketch
3. Select board and port, then upload

## Code Notes
- Matrix brightness is set to `20` for power safety; raise carefully if your supply can handle it.
- The LED matrix uses a zigzag layout configured in `FastLED_NeoMatrix`.
- The buzzer is wired active-low (LOW = on, HIGH = off).

## Demo Video
- [YouTube Link](https://youtu.be/51b9Jg0wtMc?si=Mg0HbM815nPTNqQi)

# SimonMemoryWearableWoop
A wearable Simon Memory game! 

Tutorial available on YouTube: https://www.youtube.com/watch?v=QNNUVUPXfdI&t=55s have fun building this! 

This is the main file. There is an alternative version that also connects to a phone / computer etc. That one has a highscores league table. 
This is a wearable build that is on my channel.

Note: There are FIVE conductive pieces, NOT 7! Initially, I was going to try for 7, but there are 5 touch pins available. 

<img width="877" height="533" alt="Screenshot 2025-11-04 154914" src="https://github.com/user-attachments/assets/35664ef2-1441-4996-9984-fcc5c41f74ff" />


## 2026 update - much more reliable touch

The game now works properly with conductive fabric:

- **Each pad calibrates itself** at power-on (during the rainbow - keep your hands off the pads!), so there's no single magic threshold number to fight with
- **The strongest touch wins** - touching one pad can nudge the others, so the pad that rose the most is the one that counts
- **Instant feedback** - a pad's LED lights the moment your touch registers
- **More time** - 6 seconds between touches, and holding a pad doesn't use up your time
- **Binary score reads correctly on the wrist** - LED 0 is 1, so `00011` = 3
- **Win at 31 rounds** (the most 5 LEDs can show in binary)

### Tuning

Open the Serial Monitor at 115200 baud:

- `t` - show/hide live touch readings. Each pad shows as a % of its touch threshold - 100% = touch
- `c` - re-calibrate the pads (hands off the fabric!)

If a light touch doesn't reach 100%, lower `TOUCH_PERCENT` near the top of `main.cpp` (e.g. 10). If pads trigger on their own, raise it. `TURN_TIMEOUT_MS` sets how long you get between touches.

### Libraries

- Adafruit NeoPixel

Board: Adafruit QT Py ESP32-S3. LEDs on A1, touch pads on A2 (also start), A3, SDA, SCL, TX.

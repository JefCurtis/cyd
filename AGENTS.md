# CYD workshop agent guidance

Use `.agents/skills/cyd-init/SKILL.md` for one-time laptop and device setup. Use `.agents/skills/cyd-development/SKILL.md` for ongoing firmware work.

Read these before changing firmware:

- `README.md`
- `docs/ARCHITECTURE.md`
- `docs/HARDWARE.md`
- `.agents/skills/cyd-development/SKILL.md`
- `.cyd-device.json` when present; it records the environment that passed the physical screen and touch test

For a new project idea or ChoreQuest handoff, also read `docs/NEXT_PROJECT.md`.

## Supported target

- ESP32-2432S028R with 4 MB flash and no PSRAM
- ILI9341-compatible 320x240 display
- XPT2046 resistive touch
- `cyd` and `cyd2usb` PlatformIO environments
- Upload at 460800 baud, monitor at 115200

## Rules

- `platformio.ini` and `include/config.h` are the hardware source of truth.
- Keep hardware, UI, game logic, local data, and future network code separate.
- Keep LVGL calls in `src/ui` or the display adapter.
- Do not block LVGL callbacks with delays, WiFi loops, or HTTP requests.
- Preserve partial rendering unless a memory calculation proves a change is safe.
- Prefer touch targets at least 30 to 44 pixels.
- Keep the application useful offline.
- `Hotelnet` is the tested workshop network and has no password or captive portal.
- Verify HTTPS certificates before sending credentials or private data. Never use `setInsecure()` as a workaround.
- Never commit credentials or API tokens.
- Run `pio run` after changes.
- Do not flash a connected device unless the user approves replacing its firmware.
- Never add co-author trailers to commits.

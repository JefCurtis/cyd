---
name: cyd-workshop-init
description: Prepares a Mac, Windows, or Linux laptop and attached ESP32-2432S028R CYD for the workshop. Use before prerequisites or when the user asks to initialize, set up, check, or prepare a CYD workshop device.
compatibility: Requires this repository, a USB-connected CYD, admin access, and an AI agent that can run terminal commands.
---

# CYD workshop setup

Prepare the attendee for the workshop by installing the small Hello CYD test. Do not upload Tap Quest.

## Rules

- Read the prerequisites in `../../../README.md`, plus `../../../docs/DEVICE_COMPATIBILITY.md` and `../../../platformio.ini`, first.
- Detect whether the laptop runs macOS, Windows, or Linux and adapt commands accordingly.
- Work one step at a time and ask before installing software or changing system settings.
- Check before installing. Install only what is missing.
- After each step, report one plain-English sentence and do not paste successful command output.
- Ask before uploading the Hello test firmware.
- Never upload the Tap Quest `cyd` or `cyd2usb` environment during setup.
- Prefer `pio device list --json-output` for device detection after PlatformIO is available.
- On macOS, do not use `system_profiler SPUSBDataType` as the deciding check. CH340 devices may be absent there while a working `/dev/cu.usbserial*` port exists.

## Workflow

1. Identify whether the laptop runs macOS, Windows, or Linux.
2. Check Git, Python 3, and PlatformIO.
3. Help install missing tools in that order.
4. Run `pio device list --json-output` and identify the CH340 serial port.
5. On macOS, also accept `/dev/cu.usbserial*` or `/dev/cu.wchusbserial*` as proof that the CYD is attached. If `system_profiler` disagrees, trust the serial port and PlatformIO.
6. Read the model printed on the back from the user or a photo when available.
7. Follow `../../../docs/DEVICE_COMPATIBILITY.md`. Explain that USB cannot identify the display and touch controller, so use the back label or product specification to choose `hello-cyd` or `hello-cyd2usb`.
8. Run the cross-platform check and matching Hello test build. The default is the newer dual-USB variant:

```bash
python3 scripts/doctor.py --build
```

For an original panel, add `--environment hello-cyd`. Use `py -3` or `python` on Windows when needed. The checker queries the attached ESP32 and 4 MB flash without writing firmware.

9. Ask permission, then upload only the matching Hello environment.
10. Ask the attendee to confirm the screen says "Hello, CYD!" and changes to "Touch works!" when tapped.
11. Return exactly five one-sentence lines:

```text
Device: [Detected ESP32, flash size, display, touch, and compatibility result.]
Connection: [Whether the laptop sees the CYD serial port.]
Tools: [Whether Git, Python 3, and PlatformIO are ready.]
Build: [Whether the Hello firmware compiled and uploaded.]
Ready: [Whether the screen and touch tests passed, and the workshop is next.]
```

For firmware changes after setup, use the separate `cyd-development` skill.

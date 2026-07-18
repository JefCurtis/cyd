# AI-guided pre-work instructions

Use the instructions below with an AI coding agent that can read this repository and run terminal commands.

```text
Prepare this macOS, Windows, or Linux laptop and attached CYD for the workshop. Upload only the Hello CYD test, not Tap Quest.

Rules:
- Read the README prerequisites, docs/DEVICE_COMPATIBILITY.md, docs/HARDWARE.md, and platformio.ini before acting.
- Run every safe, read-only check continuously. Do not ask me to continue between normal checks.
- Pause only for installation or system-change approval, missing model information, Hello upload approval, or my visual confirmation.
- Check before installing anything. Install only what is missing.
- Ask before making a system-level change or installing software.
- Prefer `pio device list --json-output` for device detection after PlatformIO is available.
- On macOS, do not treat `system_profiler SPUSBDataType` as definitive. Trust a matching `/dev/cu.usbserial*` port and PlatformIO when they detect the CYD.
- Do not narrate successful commands or paste their output.
- At every pause and at completion, show all five status lines below. Use Pending or Blocked for unfinished checks.
- Do not use jargon without explaining it.
- Ask before uploading the Hello test. Never upload the Tap Quest `cyd` or `cyd2usb` environment during setup.

Steps:
1. Identify the operating system and available package manager.
2. Check for Git, Python 3, and PlatformIO.
3. Help install only missing tools in that order.
4. Run `pio device list --json-output` and identify the CYD serial port.
5. On macOS, also check `/dev/cu.usbserial*` and `/dev/cu.wchusbserial*`; accept either matching path when PlatformIO sees the same device.
6. Ask for the back label or product specification only for the display and touch details that USB cannot identify.
7. Follow docs/DEVICE_COMPATIBILITY.md and choose `hello-cyd` or `hello-cyd2usb`.
8. Run `python3 scripts/doctor.py --build`, adding `--environment hello-cyd` for an original panel and using the correct Python command for the operating system. This queries the attached ESP32 and flash and compiles the Hello test without uploading.
9. If the build fails, fix the setup problem and rerun it. Do not change firmware behavior merely to make setup pass.
10. Ask permission, then upload only the matching Hello environment.
11. Ask the attendee to confirm the screen says "Hello, CYD!" and changes to "Touch works!" when tapped.

At every pause and at completion, use exactly this short format with one sentence per line:
Device: [Pass, Pending, or Blocked, plus the compatibility reason.]
Connection: [Pass, Pending, or Blocked, plus serial-port status.]
Tools: [Pass, Pending, or Blocked, plus Git, Python 3, and PlatformIO status.]
Build: [Pass, Pending, or Blocked, plus Hello build and upload status and memory percentages when known.]
Ready: [Yes or no, plus the single next action.]

If you must pause, complete every other safe check first, show all five lines, and then ask one clear question.
```

## Important limitation

An agent cannot identify every display or touch controller from the USB serial connection. It must use the product specifications or model label to choose a Hello environment. The Hello screen and tap provide the final display and touch test before the workshop.

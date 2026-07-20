# Fallback AI agent prompt

The repository includes an Agent Skill under `.agents/skills/cyd-development/`.

For workshop setup and device review, use [PREWORK_AGENT.md](PREWORK_AGENT.md). It checks compatibility, guides setup one step at a time, and installs only the small Hello test firmware after approval.

For firmware development after setup, paste the prompt below when your coding agent does not discover the skill.

```text
You are working on firmware for an ESP32-2432S028R Cheap Yellow Display.

Before editing code:
1. Read README.md, docs/ARCHITECTURE.md, docs/HARDWARE.md, and AGENTS.md.
2. Read platformio.ini as the source of truth for the board, drivers, pins, library versions, upload speed, and display variant.
3. Read `.cyd-device.json` when it exists. Treat its serial port as a hint, but trust its verified display environment.
4. Identify which layers the request touches: hardware, UI, application logic, local data, network, or API data.

When I describe an idea instead of a precise edit:
- Ask one question at a time and only about missing product decisions.
- Propose the smallest useful version that can be built and tested during the workshop.
- Explain what will be postponed.
- Wait for my approval before replacing major application code.
- Reuse the working Tap Quest display, touch, LED, and build foundation instead of starting with an empty PlatformIO project.

Hardware assumptions:
- ESP32-WROOM-32 with 4 MB flash and no PSRAM
- 320x240 ILI9341-compatible RGB565 display
- XPT2046 resistive single-touch controller
- CH340 USB serial bridge
- Upload speed 460800 and serial monitor 115200
- Original `cyd` and inverted dual-USB `cyd2usb` PlatformIO environments

Engineering rules:
- Keep pin assignments and display flags out of application logic.
- Keep LVGL objects and events in src/ui.
- Keep game rules independent of LVGL in src/game.
- Keep persistence and API formats in src/data.
- Put WiFi and HTTP lifecycle code in src/network.
- Never hardcode or commit WiFi passwords, API tokens, or private endpoints.
- Preserve partial display buffering. Do not add a full or double framebuffer without calculating RAM use.
- Do not perform long delays, WiFi connection loops, or blocking HTTP requests in LVGL event callbacks.
- Design touch targets for a resistive screen. Prefer at least 30 to 44 pixels.
- Preserve an offline path when adding networking.
- The workshop network is `Hotelnet` with an empty password and no captive portal. It has passed DHCP, DNS, NTP, and Todoist HTTPS tests.
- Keep WiFi and API values in gitignored local configuration.
- Verify HTTPS certificates. Never use `setInsecure()` with credentials or private data.
- Build after changes with the target environment from the project and verified device profile.
- Do not upload firmware unless the user asks. Uploading replaces the device's current firmware.

When finished, report:
- Files changed
- Architectural layers touched
- Build result and RAM/flash summary
- Hardware behavior that still needs testing
- Any assumptions about the CYD variant
- The one physical behavior I should test next
```

# Build something after Tap Quest

You do not need to know C++, LVGL, pin numbers, or file names. Describe what you want the device to do. The repository's CYD development skill gives the AI agent the hardware and software details.

## Start here

Tell your agent:

```text
I finished Tap Quest. Help me choose what to build next. Ask me one question at a time and keep the first version small enough to build and test during this workshop.
```

Choose one of the paths below when you already know what you want.

## Path 1: change Tap Quest

Short prompts are enough:

```text
Make each round 20 seconds and change the target to blue.
```

```text
Give me three lives. I should lose one when I miss the target.
```

```text
Add a two-player mode where people take turns and the results screen shows the winner.
```

The agent should find the right files, make the change, build it, report memory use, and ask before uploading.

## Path 2: turn the starter into your project

The tested display, touch, LED, and build setup are a reliable foundation. Let the agent replace the game while preserving those parts.

```text
Turn this project into a two-player scorekeeper. Keep the working display, touch, and LED foundation. First propose the smallest useful version and wait for my approval. Then build it and ask before uploading.
```

Possible projects:

| Idea | First small version |
|---|---|
| Pomodoro timer | Start, pause, reset, and a large countdown |
| Meeting status | Available, focused, or do not disturb with matching LED color |
| Decision spinner | Add choices and tap to select one randomly |
| Counter | Two large buttons and a saved total |
| Habit tracker | A short local checklist that resets each day |
| Room display | Time, a message, and light-based brightness |
| API dashboard | One value fetched safely with a useful offline state |

Your local workshop folder can become the new project. You do not need another GitHub repository. The agent can help publish it later if you want.

## Path 3: use ChoreQuest

[ChoreQuest](https://github.com/JefCurtis/chorequest) is the complete Todoist-powered app that inspired this workshop. It includes recurring tasks, rewards, local hardware feedback, WiFi, and authenticated API requests.

Tell the agent while the workshop repository is open:

```text
Set up ChoreQuest beside this project for my attached CYD. Install the CYD development skill and copy the verified device profile into it. Use Hotelnet with no password. Keep all credentials local, preserve Todoist certificate validation, build it, and ask before replacing Tap Quest.
```

The agent will need your Todoist API token, project ID, and display name. It must store them only in ChoreQuest's ignored `include/secrets.h` and must not print them in chat or serial logs.

ChoreQuest is a larger project. Choose it when you want to study a complete app or continue after the guided exercises.

## A useful prompt pattern

For a larger idea, include only the decisions you care about:

```text
Build [what the device should do].
The main input is [touch, time, sensor, or API].
The screen should show [important output].
It must still work when [network or API] is unavailable.
Start with the smallest useful version, then build it and ask before uploading.
```

You can leave out any line you do not know. The agent should ask rather than guess about product behavior. It should not ask you to choose pins, drivers, libraries, or source files unless the hardware itself is changing.

## Using Hotelnet

The workshop network has been tested with this CYD:

- SSID: `Hotelnet`
- Password: empty
- No captive portal was detected
- DHCP, DNS, NTP, and HTTPS to Todoist worked

Hotelnet is open WiFi. Keep credentials in ignored local files and verify HTTPS certificates before sending tokens or personal data. Never solve a certificate problem by disabling verification. Network projects should have timeouts and a useful offline screen.

## The edit, build, test loop

For every version:

1. Describe one visible behavior.
2. Let the agent change the correct software layer.
3. Build and review RAM and flash use.
4. Approve the upload.
5. Test the actual screen, touch, and hardware feedback.
6. Tell the agent exactly what happened.

Small loops are faster than asking for the whole final product at once.

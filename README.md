# Megumi Raid Macro: User Guide

## Before you start

- Use Windows and keep the game visible on the desktop while the macro runs.
- Put the game at the same screen size and position you plan to use during the run.
- Keep the supplied game screenshots/templates unchanged; the macro uses them to recognize the Retry button, boss banners, timer, and hotbar slots.
- Run the macro only when you are ready for it to send mouse and keyboard input.

## Start the macro

1. Open the `fast` folder.
2. Double-click `Run_Macro.bat`.
3. On first run, the launcher checks for Python and tries to install it if it is missing, then installs or updates the macro's Python packages.
4. If Windows asks for permission to install Python, approve it. If automatic installation is unavailable, install Python 3 from python.org, enable the option to add Python to PATH, then run the batch file again.
5. The settings window opens. Configure it, then choose **Save & Run**.

## Configure the settings

- **Resolution:** select your display resolution, or use **Detect my screen**. This also sets the suggested image scale.
- **Fullscreen / Halfscreen:** choose the layout you actually use. Changing this setting does not move or resize scan areas.
- **Skills:** select the keys the macro should use for Megumi and Mahoraga. Middle click is available as a skill option.
- **Game window title:** leave `Roblox` unless your game window has a different exact title.
- **Scan areas:** these screen-coordinate boxes tell the macro where to look for the Retry button, boss banner, timer, and hotbar. Defaults are for the original setup. If your layout differs, use **Grab** to capture the two opposite corners for each area; follow the dialog's corner labels.
- **Timing:** adjust the wait before clicking Retry, before starting the Megumi combo, before its skill spam, the number of Retry clicks, and the spacing between timer-reset keys.
- **Features:** enable or disable the Megumi combo, Mahoraga skill spam, automatic hotbar equip, timer reset, stats window, and colored console output.
- **Skip this window next time:** enable this after setup to reuse saved settings. To open settings again, open Command Prompt in the `fast` folder and run `py -3 Megumi_Raid_Nightmare.py --settings`.

Use **Reset to defaults** if you want to discard the current edits. Settings are saved when **Save & Run** is pressed. The launcher checks that required images exist and that scan boxes are large enough before starting.

## What happens while it runs

- The macro scans for Retry, enabled boss banners, the configured timer image, and hotbar slot states.
- When Retry is detected, it pauses its other routines, moves to the button, clicks it the configured number of times, and returns the cursor to its home spot.
- When an enabled boss banner is detected, it starts that boss's configured key routine.
- If automatic equip is enabled, it checks slots 2 and 3 and presses a slot key when neither appears equipped.
- When the timer image is confirmed, it sends **Esc**, **R**, and **Enter**, then repeats that sequence after a 4-second wait.
- The stats window shows completed Retry loops and elapsed runtime. The console reports detections and warnings.

## Stop or change settings

- Press **Ctrl+C** in the macro's console to stop it cleanly and release simulated keys.
- To change settings, stop the macro, open Command Prompt in the `fast` folder, and run `py -3 Megumi_Raid_Nightmare.py --settings`.
- Avoid closing the console while the macro is running; closing it ends the process.

## Troubleshooting

- **Python was not found:** run `Run_Macro.bat` again after Python installation. If automatic setup fails, install Python 3 from python.org with **Add Python to PATH** enabled.
- **A required image is missing:** restore the macro's original image templates to the `fast` folder, then restart.
- **It misses a button or banner:** check that the game resolution, window placement, image scale, and scan areas match the current screen. Use **Grab** to update scan-area corners.
- **Keys go to another window:** make sure the game is open and not minimized, and check the exact game-window title in settings.
- **It stops responding or behaves unexpectedly:** stop with Ctrl+C, reopen the macro, and check the console's last warning. If it happens repeatedly, note the warning and which game state was visible.

The macro uses automated input and image matching, so game updates, UI changes, and display scaling can affect detection. Follow the game's rules when using automation.

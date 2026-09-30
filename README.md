# Megumi Raid Nightmare Macro 👹

An advanced, production-grade automated computer vision macro specifically tailored for **Roblox Anime Raids** (calibrated for the Megumi/Mahoraga Nightmare encounter). 

Built using Python, **OpenCV**, and multi-threaded processing, this script monitors your screen in real time to handle boss triggers, loop restarts, character anti-stalls, and slot re-equipping flawlessly without lagging your game loop.

---

## ✨ Features
*   **Intelligent Boss Detection:** Differentiates between **Megumi** and **Mahoraga** banners using precise template matching score comparisons.
*   **Dynamic UI Setup Window:** Includes a full configuration interface (`tkinter`) on startup to adjust timing, keys, switches, and pixel bounds without digging into code.
*   **Natural Mouse Gliding:** Uses a custom mathematical **Smootherstep interpolation algorithm** to glide your cursor smoothly instead of teleporting it (helps stay under anti-cheat thresholds).
*   **Independent Auto-Equip Engine:** Runs a lightning-fast dedicated thread to watch your hotbar. If a weapon or slot drops unequipped, it forces it back active.
*   **Anti-Stall Timer Reset:** Automatically senses when a run goes past the time limit (e.g., `22:00`), instantly inputting `Esc + R + Enter` to force a map reset.
*   **Always-On-Top Dashboard:** Spawns a floating window displaying active statistics (**Completed Loops** and **Total Uptime**).

---

## 🛠️ Prerequisites & Installation

### 1. Install Python
Make sure you have **Python 3.8+** installed on your system. 

### 2. Install Dependencies
Open your command prompt or terminal and run the following command to download the required computer vision and input libraries:

```bash
pip install mss opencv-python numpy pyautogui pydirectinput
```

---

## 📸 Image Template Configuration

The macro checks your screen against small reference snapshot snippets. You **MUST** crop and place these exact `.png` assets inside the **same directory** where your script lives:

| Filename | Description |
| :--- | :--- |
| `Retry.png` | The text/button indicating a round failure or completion replay. |
| `Megumi.png` | The distinct boss banner name for "Defeat Megumi". |
| `Mahoraga.png` | The distinct boss banner name for "Defeat Mahoraga". |
| `timer.png` | The visual representation of the overtime/stuck counter (e.g., `22:00`). |
| `Equipted2.png` / `Equipted3.png` | What your hotbar slots 2 and 3 look like when active. |
| `UnEquipted2.png` / `UnEquipted3.png` | What your hotbar slots 2 and 3 look like when passive/holstered. |

> 💡 **Crucial Crop Tip:** Crop your assets using standard screenshot software matching your current game configuration. For best template alignment, capture images closely bounded around the text or borders.

---

## 🚀 How to Run and Use

### Step 1: Fire up the Script
Execute the script from your command prompt:
```bash
python megumi_macro.py
```

### Step 2: Configure Your Layout via GUI
The macro will launch an interactive settings dashboard. Follow these alignment parameters:
1. **Choose/Input Resolution:** Select your monitor's display layout (or write yours inside the custom box). This scales the target template size automatically!
2. **Assign Scan Areas via `Grab`:**
   * Look at an item on your game layout (e.g., the *Retry Button*).
   * Click **Grab** next to `Top-right corner`. You have **3 seconds** to hover your real mouse cursor directly over the top-right corner of that button. 
   * Repeat the click for the `Bottom-left corner` to enclose the target box cleanly.
3. **Map Skill Routines:** Toggle which hotbar or click buttons (`Z, X, C, V, R, MMB`) should fire during the Megumi or Mahoraga combat phases.
4. **Save & Run:** Press **Save & Run**. All definitions are written locally to a structural `settings.json` file so you don't have to fill it out next time.

### Step 3: Modifying Configuration Later
If you want to pull the settings panel back up down the road instead of passing straight into the loop automation, run:
```bash
python megumi_macro.py --settings
```

---

## ⌨️ Routine Actions Performed

### 🟣 Megumi Phase
When the macro reads a valid Megumi banner sequence:
1. Pauses briefly (custom delay), then pulls focus cleanly over to the **Roblox** environment container.
2. Assures hotbar status slots are safely drawn/held.
3. Presses and holds `W` for 1.0 second to drive positioning forward.
4. Taps your dash/movement trigger (`Q`) twice.
5. Begins execution loops spamming your selected keys.

### 🔴 Mahoraga Phase
A high-intensity override routine:
1. Immediately gains game frame windows prominence.
2. Non-stop cycles input spams across all chosen combat hotkeys simultaneously to out-DPS the nightmare mechanics.

---

## ⚠️ Important Failsafes & Exit
* **How to Exit:** Focus on the command terminal execution screen and press **`Ctrl + C`** to break out of the scripts loops safely and pull down background thread tasks clean.
* **QuickEdit Protection:** Windows command windows can occasionally hang operations if you click inside text logs. This script features low-level Windows API injections to programmatically strip QuickEdit locks on startup to stop accidental system pauses.
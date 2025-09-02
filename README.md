# Patch | Dev

## For developers-
[designers info & reference](https://github.com/Intelektika-team/Project-PATCH/blob/develop/fordesigner.md) |
[designers directory](https://github.com/Intelektika-team/Project-PATCH/tree/develop/designers)

[developers info & reference](https://github.com/Intelektika-team/Project-PATCH/blob/develop/fordeveloper.md) |
[developers directory](https://github.com/Intelektika-team/Project-PATCH/tree/develop/scr)

### About patch - dev
- Baudrate - 115200 baud
- Id form - xxxx-xxxx-abcd-xabc
    - example - 1234-5678-T3st-1qwE
- Hardware:
    - Rp 2040
    - 8 buttons, encoders
- Frimware:
    - Arduino cpp
    - Python3 api
- Events send format "{device}-{number}-{action}-{value}"
    - Example: "button-1-pressed-1"



## 🚀 Overvie
Patch is a programmable hardware panel designed for developers, engineers, and power users. It enables instant execution of custom automation scripts via physical buttons and encoders, connecting seamlessly over USB. Each button press or encoder rotation triggers user-defined Python scripts on the host computer, turning complex workflows into simple physical actions.

## 🧠 Core Philosophy
- **Simplicity:** Patch uses a straightforward UART-based protocol for reliable communication.
- **Power:** Execute any Python script—no limitations, no sandboxing.
- **Elegance:** Features a semi-transparent, minimalist design inspired by modern tech aesthetics.
- **Openness:** The protocol is open and extensible, allowing integration with any software stack.

## ⚙️ Hardware Specifications
- **Microcontroller:** Raspberry Pi RP2040
- **Interface:** USB-C (UART/CDC)
- **Controls:**
 ⚒ - 8x Tactile buttons (programmable)
  - 2x Rotary encoders (with push-button functionality)
- **Case:** 3D-printed matte finish shell
- **Firmware:** Custom-built in C/C++ (Arduino framework compatible)

## 🛠 Communication Protocol
Patch communicates via serial (UART) at `115200 baud`. The protocol is text-based and human-readable.

### ► Device Discovery
Each Patch device has a unique ID printed on its packaging. To autodiscover the device:

1. Host sends: `start {id}\n`
2. Patch responds: `started {id}\n` (if ID matches)

### ► Event Reporting
Patch sends events in the format:
`{device}-{number}-{action}-{value}\n`

- **Examples:**
  - `button-1-pressed-1`
  - `button-1-released-0`
  - `encoder-2-rotated-10` (value represents rotation steps)

## 💻 Software Setup (Host Computer)

### ► Python Daemon
The host runs a Python daemon that:
1. Discovers the Patch device via ID
2. Listens for incoming events
3. Maps events to user-defined Python scripts

### ► Required Libraries
```bash
pip install pyserial
```

### ► Configuration
Script mappings are defined in a `config.json` file:
```json
{
  "button-1-pressed": "/path/to/script1.py",
  "encoder-2-rotated": "/path/to/script2.py"
}
```

### ► Example Usage
```python
# Example script: git_push.py
import subprocess
subprocess.run(["git", "add", "."])
subprocess.run(["git", "commit", "-m", "Automated commit by Patch"])
subprocess.run(["git", "push"])
```

## ✅ Getting Started
1. Connect Patch via USB
2. Run the daemon: `patchwork --start-id YOUR_DEVICE_ID`
3. Press a button—your script executes instantly

## ✅ Support & Community
- **Documentation:** [docs](https://github.com/Intelektika-team/Project-PATCH)
- **Issues:** GitHub Issues
- **Discussions:** GitHub Discussions
- [**wiki**](https://github.com/Intelektika-team/Project-PATCH/wiki)
---

**Patch: Just press it.**

by Intelektika-team, teamlead - pt, status - active development.

/dev branch/


**Intelektika 2025 - Dimitrovgrad - started at 30.08.2025**

keywords-
Intelektika team, Intelektika-team, Intelektika, Intelektika patch, team intelektika, project patch, the patch, patch

# ds-tense

**ds-tense** is a lightweight wrapper script for [dualsensectl](https://github.com/nowrep/dualsensectl) on Linux. It adds persistent memory, preset management, and game-specific automation to the DualSense trigger tension settings.

## 🎮 The Problem
The PS5 DualSense controller has adaptive triggers that offer incredible immersion (variable tension, resistance, vibration). On Windows, tools like DSX handle this beautifully.

On Linux, we have the excellent command-line tool `dualsensectl`. It works great, but it has no memory. The moment you disconnect the controller or reboot, your settings are gone. If you want specific tension for a racing game and different tension for a shooter, you have to manually type long commands every time.

## 🛠️ The Solution
**ds-tense** bridges that gap. It allows you to:
* **Save Presets:** Create named profiles for your favorite settings (e.g., `racing`, `fps`, `hard_trigger`).
* **Auto-Load:** Automatically apply presets when a game launches via Steam.
* **Easy Management:** Simple CLI commands to create, load, and delete settings.

## 📋 Prerequisites

1.  **A PS5 DualSense Controller.**
2.  **Linux OS** (Arch, Fedora, Ubuntu, etc.).
3.  **dualsensectl:** This script depends on `dualsensectl` to communicate with the hardware.
    * [Install instructions for dualsensectl](https://github.com/nowrep/dualsensectl)

## 📥 Installation

1.  Clone this repository:
    ```bash
    git clone [https://github.com/TheThirdDoor/ds-tense.git](https://github.com/TheThirdDoor/ds-tense.git)
    cd ds-tense
    ```

2.  Run the installer:
    ```bash
    chmod +x install-ds-tense
    ./install-ds-tense
    ```
    *Note: You will be prompted for your `sudo` password to allow the script to copy files to your system path.*

## 🚀 Usage

### 1. Experiment and Set
First, figure out what tension values feel good to you using the raw setting mode.
```bash
ds-tense set <setting_values>
```

2. Create a Preset
Once you find a tension you like, save it with a memorable name.

```bash
# Syntax
ds-tense create <name> <setting_values>

# Example: Create a preset named "fps_mode"
ds-tense create fps_mode 2333670000
```
3. Load a Preset
Apply your saved settings instantly.

```bash
ds-tense load fps_mode
```
4. List and Manage
View all your current commands and presets by running the script without arguments:

```bash
ds-tense
```
## 🎮 Steam Integration (Auto-Load)
You can make Steam apply a specific preset automatically when you launch a game.

Right-click the game in your Steam Library and select Properties.

Navigate to the General tab.

In the Launch Options box, enter the following:

```bash
ds-tense load <preset_name>; %command%
```
(Replace <preset_name> with your specific preset, e.g., fps_mode).

Close the window and play!

## 🍷 Troubleshooting: Proton & WINE
If you are playing Windows games via Proton/WINE, the compatibility layer often tries to take exclusive control of the controller, resetting the triggers to "none" (no tension).

To prevent this, you need to edit the WINE registry for that prefix:

Navigate to HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\winebus in the registry editor (protontricks or regedit).

Create a DWORD key named DisableHidraw.

Set the value to 1.

## 🗑️ Uninstalling
To remove the script and associated files from your system:

```bash
ds-tense uninstall
```
## ❤️ Support
If you found this tool useful, consider checking out my Patreon.

## 📄 License (GNU AGPL)
[Read the License](LICENSE)

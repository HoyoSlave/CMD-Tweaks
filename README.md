# CMD Tweaks (`cmd_tweaks`)

A lightweight, powerful performance optimization module for Android (Magisk / KernelSU / APatch) utilizing native Android Shell (`cmd`, `setprop`, `dumpsys`) commands and custom automation scripts to enhance gaming performance, battery efficiency, and system responsiveness.

---

## 🌟 Features

- **Automated Game & Daily Mode Switching (`loop.sh`)**
  - Monitors active top apps and automatically switches system profiles when launching target games (defined in `perflist.txt`).
  - Automatically toggles **Do Not Disturb (DND)** mode during gameplay.
  - Automatically adjusts CPU/GPU profiles, thread priorities (`renice`, `ionice`), and `taskprofile` CPU sets for foreground game tasks.
  - **Asset Preloading**: Preloads game assets directly into memory for reduced stutter and faster load times.
  - Scheduled maintenance at **03:00 AM**: Runs `fstrim` and optional background **Dalvik Dexopt Compilation** (`speed` for user apps, `space` for system apps).

- **Performance & Multitasking Profiles (`option.sh` & `profiler.sh`)**
  - **System Profiles**:
    - **Performance**: Sets CPU/GPU scaling frequencies to maximum, disables adaptive power saving, overrides thermal limits, and prioritizes active tasks.
    - **Balanced**: Balances performance and thermal output for everyday smooth operation.
    - **Power Saver**: Reduces minimum CPU/GPU scaling levels, restricts background tasks, and enables aggressive battery saver settings while offering high refresh rate overrides.
  - **Multitasking Profiles**: Tune Activity Manager constants (`activity_manager_constants`) and memory factors from **Highest** (max background apps) down to **Lowest** (strict RAM management).

- **Thermal & Fast Charging Tweaks (`thermal.sh`)**
  - Root option to disable thermal throttling services (`miui.powerkeeper`, thermal engine daemons, thermal zone permissions) for unthrottled sustained gaming performance.
  - Dedicated **Fast Charging** override mode.

- **Graphics & Renderer Overrides**
  - **Unreal Engine Tuning (`unreal.sh`)**: Dynamically pushes custom `Engine.ini` and `DeviceProfiles.ini` graphics tweaks to all installed Unreal Engine titles (quality tiers 0 to 4).
  - **Game Downscaling (`scale.sh`)**: Control Android 12+ Game Mode downscaling on demand per-game or globally.
  - **Global Window Rescaling (`screen.sh`)**: Real-time display resolution and DPI scaling for extreme performance gains.
  - Switch graphics backend between **Default**, **SkiaGL**, and **SkiaVK**.
  - Force **ANGLE** (OpenGL ES to Vulkan translation layer) or **Native** driver selection per package.

- **System De-bloat & Logging Reduction (`service.sh`)**
  - Disables heavy system logging, tracing (`atrace`, logcat buffers, `migard`, window/input tracing), and debugging services.
  - Cleans temporary thumbnail cache, log files, package art, dexopt artifacts, and blob store junk at boot.
  - Optimizes background restrictions and standby buckets for all user packages while protecting critical music/media apps.

- **Integrated WebUI / Dashboard (`webroot/index.html`)**
  - Built-in WebUI accessible via KernelSU / Webview or web browser to configure profiles, game lists, sliders, toggles, and scripts interactively.

---

## 📂 File & Directory Structure

```
/data/adb/modules/cmd_tweaks/
├── service.sh             # Main boot script (runs background optimizations and starts loop.sh)
├── uninstall.sh           # Reset script to revert all changes made by the module
├── module.prop            # Module metadata
├── charge                 # Fast charge trigger file
├── other/
│   ├── loop.sh            # Background daemon monitoring active apps and maintenance tasks
│   ├── option.sh          # Handles switching system performance and multitasking profiles
│   ├── profiler.sh        # Manages CPU/GPU sysfs frequencies, governors, and thermal limits
│   ├── thermal.sh         # Controls thermal throttling services and battery temp overrides
│   ├── scale.sh           # Handles Android 12+ Game Space downscaling
│   ├── screen.sh          # Adjusts global screen size and DPI density
│   └── unreal.sh         # Injects graphics configuration into Unreal Engine games
└── webroot/
    └── index.html         # WebUI interface for interactive control
```

---

## ⚙️ Configuration & Storage Paths

The module uses `/storage/emulated/0/Android/media/.sosp/` for dynamic configuration files:

| Path | Description |
| :--- | :--- |
| `/storage/emulated/0/Android/media/.sosp/perflist.txt` | Target package list for automatic Gaming Mode trigger |
| `/storage/emulated/0/Android/media/.sosp/gamelist.txt` | Target package list for `scale.sh` Game Manager downscaling |
| `/storage/emulated/0/Android/media/.sosp/settings.ini` | Stores user toggle states (`gaming`, `daily`, `disturb`, `preload`, `compile`, `thermal`, `maximum`) |
| `/storage/emulated/0/Android/media/.sosp/sprof` | Stores current active System Profile |
| `/storage/emulated/0/Android/media/.sosp/mtask` | Stores current active Multitasking Profile |
| `/storage/emulated/0/Android/cmd_tweaks.log` | Execution and status log file |

---

## 🚀 Usage & Commands

### Manual Execution via Shell / Terminal

If you want to run options manually from a terminal (e.g., Termux or ADB shell as root):

#### 1. Change Performance / Multitasking Profiles
```bash
# Apply Performance mode with Lowest multitasking
su -c /data/adb/modules/cmd_tweaks/other/option.sh performance lowest

# Apply Balanced mode with Medium multitasking
su -c /data/adb/modules/cmd_tweaks/other/option.sh balance medium

# Apply Power Saver mode with Highest multitasking
su -c /data/adb/modules/cmd_tweaks/other/option.sh powersave highest
```

#### 2. Thermal Control & Fast Charge
```bash
# Disable Thermal Throttling
su -c /data/adb/modules/cmd_tweaks/other/thermal.sh disable

# Enable Thermal Throttling (Default)
su -c /data/adb/modules/cmd_tweaks/other/thermal.sh enable
```

#### 3. Unreal Engine Graphics Preset
```bash
# Set Unreal Engine games quality (0 = Lowest, 1 = Low, 2 = Medium, 3 = High, 4 = Ultra)
su -c /data/adb/modules/cmd_tweaks/other/unreal.sh 2
```

#### 4. Resolution & Density Scale
```bash
# Scale screen resolution & DPI to 80% (0.8)
su -c /data/adb/modules/cmd_tweaks/other/screen.sh 0.8

# Reset resolution & DPI to normal
su -c cmd window size reset && su -c cmd window density reset
```

---

## 🌐 WebUI Control Panel

If running via KernelSU or WebUI-supported manager:
1. Open the WebUI interface embedded in the module options.
2. Use the tabs:
   - **Home**: Control `./loop.sh` state, set package rules for daily vs. gaming mode, configure asset preloading, and edit the games list.
   - **Settings**: Toggle fast charging, sensor privacy, thermal limits, Google services, doze mode, and system profiles.
   - **Game**: Adjust global resolution sliders, game-downscale multipliers, and Unreal Engine quality levels.

---

## 🗑️ Uninstallation

Uninstalling through Magisk / KernelSU will execute `uninstall.sh` automatically upon reboot, which:
- Resets display size, density, and downscaling settings.
- Restores background network settings and app standby buckets.
- Restores global settings and activity manager default parameters.
- Re-enables system logging and thermal services.
- Cleans up created temporary directories and scripts.

---

## 📜 Credits & Disclaimers

- Shell profiler logic credits: **@Rem01Gaming** (`t.me/rem01schannel`)
- Developed by **SOSP Team** (`t.me/S_O_S_P/1`)

> **Disclaimer**: Use at your own risk. Disabling thermal throttling or forcing maximum CPU/GPU frequencies may cause elevated device temperatures and increased battery consumption.

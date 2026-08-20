# CMD Tweaks (`cmd_tweaks`)

A lightweight, powerful performance optimization module for Android (AxManager / Magisk / KernelSU / APatch) utilizing native Android Shell (`cmd`, `setprop`, `dumpsys`) commands and custom automation scripts to enhance gaming performance, battery efficiency, and system responsiveness.

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

## 📜 Credits & Disclaimers

Profiler credits: [@Rem01Gaming](https://t.me/rem01schannel)

Developed by [@HoyoSlave](https://t.me/S_O_S_P) with Members

> **Disclaimer**: Use at your own risk. Disabling thermal throttling or forcing maximum CPU/GPU frequencies may cause elevated device temperatures and increased battery consumption.

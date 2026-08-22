<div align="center">
  <img src="https://raw.githubusercontent.com/HoyoSlave/hoyoslave.github.io/refs/heads/main/Pictures/cmd.jpg" width="100%" style="border-radius: 8px;">
  
  <br>

  <a href="https://t.me/S_O_S_P">
    <img src="https://img.shields.io/badge/Telegram-Channel-26A5E4?style=flat-square&logo=telegram&logoColor=white">
  </a>
  &nbsp;
  <a href="https://t.me/HoyoSlave">
    <img src="https://img.shields.io/badge/Telegram-Author-26A5E4?style=flat-square&logo=telegram&logoColor=white">
  </a>

</div>

---

## 〄 CMD-Tweaks

Designed to optimize Android devices at the system and kernel levels by utilizing the `cmd` and `dumpsys` utilities, and adjusting the `devfreq` kernel subsystem.

### WebUI Capabilities
* **Starts or Stops `./loop.sh`:** Auto adapts to daily or gaming use
  * Start `./loop.sh`: start shell-ascend
  * Stop `./loop.sh`: stop shell-ascend
  * Auto Game Preload: preload game assets into memory *faster loading and rendering
  * Enable Don't Disturb: mute incoming calls and notification *immersive experience
  * Use Dalvik Compile: running every 3am *improve performance and system efficiency
* **[root] Fast Charging:** Disabling thermal services. turn it on, wait 5 seconds, plug in the charger.
* **Disable Device Sensors:** Disabling gyroscope, camera, etc. reduce cpu load.
* **Disable Google Protect:** Disabling daily scanning and protection. reduce cpu load.
* **Disable Google Services:** Disabling google account, contact, etc. reduce memory usage *sync your contact.
* **Disable Network Stats:** Disabling network statistics. increase network downloading speed.
* **Enable Data Saver:** Restricts background data usage. increase network stability for top app.
* **Enable Doze Mode:** Restricts background activity. reduce memory usage.
* **System Profiles:** Configure system performance profiles
  * Performance: favors perf *eat more energy
  * Disable Thermal (some codes work on nr) *unlimit performance while overheating
  * Balanced: balances perf with energy usage
  * Power Saver: saves energy *reducing perf
  * Maximum Refresh Rate *unlimit 60hz while in power saver
* **Multitasking Profiles:** Control how apps can run in background
  * Higher: more bg apps, higher memory usage
  * Lower: less bg apps, lower memory usage
* **Renderer (Graphics Engine):** Selects the rendering backend
  * Default: system default renderer
  * SkiaGL: better compatibility on older devices
  * SkiaVK: better perform on modern devices
* **Angle (OpenGL ES Driver):** Translates opengles to vulkan api.
* **Kill User Apps:** Force closes all user apps to free up memory.
* **Global Scale:** Overall resolution changer
  * Lower: better performance, worse graphics
  * Higher: increases screen sensitivity
* **Game Manager (A12+):** Games resolution changer
  * Lower: better performance, worse graphics
  * Higher: increases screen sensitivity
* **Unreal Engine Configs:** Adjust unreal engine graphics
  * Lower: better performance, worse graphics
  * Higher: better graphics, worse performance
  * Recompile Unreal Engine: can fixing some rendering issues

## Supported Environments

CMD-Tweaks supporting both

Rooted and Non-Rooted environments.

| Environment | Recommended |
| :--- | :--- |
| **Root** | [KsuWebUI](https://github.com/KOWX712/KsuWebUIStandalone/releases) |
| **Non-Root** | [AxManager](https://github.com/fahrez182/AxManager/releases) |

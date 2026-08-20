# Shell-Ascend Optimization Tool

Welcome to the Shell-Ascend Optimizer. This tool provides advanced system tuning, graphics configuration, and resource management to adapt your device for both daily usage and intensive gaming. 

## 🚀 Core Automation & Background Scripts

The `./loop.sh` script automatically adapts your device's behavior based on your current usage.

| Feature | Description | Benefit |
| :--- | :--- | :--- |
| **Start / Stop** | Initializes or terminates `shell-ascend`. | Auto-adapts seamlessly to daily or gaming use. |
| **Auto Game Preload** | Preloads required game assets directly into memory. | Significantly faster loading and rendering times. |
| **Do Not Disturb** | Suppresses incoming calls and notifications. | Provides an uninterrupted, immersive experience. |
| **Dalvik Compile** | Automates compilation routines every day at 3:00 AM. | Improves overall app performance and system efficiency. |

## ⚙️ System Tweaks & Resource Management

These toggles allow you to aggressively manage system services to prioritize foreground performance and network stability.

| Service | Description & Usage |
| :--- | :--- |
| **[Root] Fast Charging** | Disables thermal limits. *Usage: Turn on, wait 5 seconds, then plug in the charger. Auto-disables when unplugged.* |
| **Sensors & Protect** | Disables device sensors (gyroscope, camera) and Google Protect daily scanning to reduce CPU overhead. |
| **Network & Data** | Disables network stats to increase download speeds. Enables Data Saver to stabilize connections for the active app. |
| **Doze Mode** | Restricts background activity to reduce idle memory usage. |
| ⚠️ **Disable Google Services** | Disables Google accounts, contacts, and sync to save memory. *(Note: Ensure your contacts are synced before enabling).* |
| ⚠️ **Kill User Apps** | Force-closes all active and cached user apps to instantly free up RAM. |

## 🔋 System & Multitasking Profiles

Configure how the Android system handles CPU scaling, thermal throttling, and background app limits.

*   **Performance:** Maximizes hardware output at the cost of higher battery consumption. Includes an experimental **Disable Thermal** flag to prevent throttling when the device overheats.
*   **Balanced:** Standardizes the ratio between performance and energy efficiency.
*   **Power Saver:** Reduces overall performance to maximize battery life. Includes an override for **Maximum Refresh Rate** to force 60Hz UI smoothness even in low-power states.
*   **Multitasking Capacity:** Toggle between **Higher** (keeps more apps alive in the background) or **Lower** (aggressively kills background apps to preserve memory).

## 🎮 Graphics & Rendering Optimization

Fine-tune how your GPU renders UI elements and 3D applications.

*   **Graphics Renderer:** Override the system default. Choose **SkiaGL** for better compatibility on older devices, or **SkiaVK** for superior performance on modern hardware.
*   **Angle (OpenGL ES):** Translates legacy OpenGL ES calls into the Vulkan API for smoother frame pacing.
*   **Resolution Scaling:** Adjust the **Global Scale** or **Game Manager (Android 12+)** to *Lower* (boosts framerates) or *Higher* (increases screen sharpness and sensitivity).
*   **Unreal Engine Configs:** Force UE-based games into lower/higher graphical fidelity, or trigger a **Recompile** to fix visual rendering glitches.
